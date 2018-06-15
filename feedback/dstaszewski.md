# API Architecture Feedback

Presented `curl` sample is a example revisiting API. The changes will be a different than it can be assumed.

Also i made up a [sample code](https://github.com/stachu540/hirez-api-sample-oas3/blob/master/swagger.yaml) (partly) using [OAS3](https://app.swaggerhub.com/apis/stachu540/Smite/v2). Those samples it is a proposial to changes. Hi-Rez Studios will change it for their purpose.

- _What is going on with Rate Limits?_
  Rate limits will prevents to flooding data and blocking user if he reacing the limits. Currently you are use: `/getdataused`
  which are shows our limits. But if you are sending those request your daily limit will be decreased.
  Mostly API developers using rate limits inside the headers.
  Example response (Dayli limit):
    ```yaml
    Headers:
      X-Rate-Limit: 7500
      X-Rate-Limit-Remaining: 7499 # after first query will responde one less than X-Rate-Limit
      X-Rate-Limit-Reset: 1529091932 # unix timestamp in UTC (2018-06-15T19:45:32+00:00)
    ```
  
- _Can't we move away from URL parameters to Request Body data, blah, blah, blah:_
    Yes and No. **Yes** if we creating POST query. Request Body doesn't work for GET. API is mainly using GET request.
    **No** if we want to stick into the GET request. So we will use request into the parameters like:
  - Search Teams (SMITE):
    ```sh
    curl -H "X-Session-Token: {Session-Token}" https://api.hirezstudios.com/smite/pc/teams?query=dignitas
    ```

  - Players:
    ```sh
    curl -H "X-Session-Token: {Session-Token}" https://api.hirezstudios.com/paladins/pc/players?query=creativs2
    ```
- _Does anyone actual use XML vs JSON anyway, blah, blah, blah, blah, blah_

  XML is not much popular Response Body. Many programmers using a JSON response. We can compare [JSON vs XML](https://www.w3schools.com/js/js_json_xml.asp) on those site.
  For example in Java i use [Jackson](https://github.com/FasterXML/jackson-databind) to parsing response into the [POJO](https://en.wikipedia.org/wiki/Plain_old_Java_object).
