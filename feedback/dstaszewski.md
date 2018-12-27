# API Architecture Feedback

Presented `curl` sample is a example revisiting API. The changes will be a different than it can be assumed.

Also i made up a [sample API code](https://app.swaggerhub.com/apis/stachu540/Smite/v2) (partly) using [OAS3](https://swagger.io/docs/specification/about/). Those samples it is a proposial to changes. Hi-Rez Studios will change it for their purpose.

- _What is going on with Rate Limits?_

  Rate limits will prevents to flooding data and blocking user if he reacing the limits. Currently you are use: `/getdataused`
  which are shows our limits. But if you are sending those request your daily limit will be decreased to one less query limits remain.
  Mostly API developers using rate limits inside the headers.
  Example response (Dayli limit):
    ```yaml
    Headers:
      X-Rate-Limit: 7500
      X-Rate-Limit-Remaining: 7499 # after first query will responde one less than X-Rate-Limit
      X-Rate-Limit-Reset: 1529091932 # unix timestamp in UTC (2018-06-15T19:45:32+00:00)
    ```
  
- _Can't we move away from URL parameters to Request Body data, blah, blah, blah:_

    _Yes and No_.
    
    **No** if we want creating other queries than GET method. Request Body doesn't work for GET method. Your API is mainly using GET request.
    
    **Yes** if we want to stick into the GET request method. So we will use request into the parameters like this (only examples):
  - Search Teams (SMITE):
    ```sh
    curl -H "X-API-Key: $(echo -n "{dev_id}:{session_id}:{auth_key}" | md5sum | cut -d"-" -f1 -)" https://api.smitegame.com/pc/teams?name=dignitas
    ```

  - Players:
    ```sh
    curl -H "X-API-Key: $(echo -n "{dev_id}:{session_id}:{auth_key}" | md5sum | cut -d"-" -f1 -)" https://api.paladins.com/pc/players?username=creativs2
    ```
- _Does anyone actual use XML vs JSON anyway, blah, blah, blah, blah, blah_

  XML is not much popular Response Body. Many programmers using a JSON response. We can compare [JSON vs XML](https://www.w3schools.com/js/js_json_xml.asp) on those site. In short, JSON is better readable object than XML.
  For example in Java i use [Jackson](https://github.com/FasterXML/jackson-databind) to parsing response into the [POJO](https://en.wikipedia.org/wiki/Plain_old_Java_object).

---

UPDATE 12/27/18: Let's taste a new way solutions which is [GraphQL](https://graphql.org/). Everyone will create own query data for 3rd party apps. No one needs decied which fields needs to your app. I think is better way solution, adding mentioned Rate Limits and Created API Key via `createSession()` ;)
