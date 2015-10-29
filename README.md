Retrieve informations about one domain:
- Ping
- Page Rank
- Backlinks, Truts Flow, Citation Flow and other metrics provided by the Majestic API
- Availability provided by whoisxmlapi.com
- Whois data provided by whoisxmlapi.com + 3 extra info : isValidDomain, isPendingDelete, missingData (if no whois found)

TODO :
- Check the number of pages indexed by Google (primary & secondary index)
- other ideas are welcome !

In order to get all info, you need to provide your majestic API key and your whoisxmlapi user & password. Without those setting, it returns only ping & PR.

Install this module in your node project
----------------------------------------
$ npm install check-domain --save

Crash course
------------


```javascript
var checkDomain = require("check-domain");


checkDomain(
  {
    domain : "domainToCheck.com",
    majecticKey : "[add here your majestic key]",
    whois : {user : "[your whoisxmlapi name]", password : "[your whoisxmlapi password]"}
  },
  function(error, result) {
        console.log(result.isAlive);
        console.log(result.available);
        console.log(result.pr);
        console.log(result.majestic); // see the json structure provided by http://developer-support.majestic.com/api/commands/get-index-item-info.shtml
        console.log(result.whois);    // see the json structure provided by http://www.whoisxmlapi.com

        // We add 3 extra field in the whois structure
        console.log(result.whois.isPendingDelete);
        console.log(result.whois.isValidDomain);
        console.log(result.whois.missingData);

  });

```
