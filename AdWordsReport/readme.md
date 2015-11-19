# AdWordsScriptsReport.js

This a  wrapper for the [AdWordsApp.report()](https://developers.google.com/adwords/scripts/docs/reference/adwordsapp/adwordsapp_report) no more annoying strings when you expect floats or arrays and more neat way to write your AWQL-string.

## Examples

```javascript
function main() {
    var ga = new AdWordsReport();
    var reportData = ga.awql()
        .select(['Clicks','Impressions','Year','Cost','SearchImpressionShare','Labels','CampaignName'])
        .from('CAMPAIGN_PERFORMANCE_REPORT')
        .where('Clicks > 0')
        .and('Impressions > 10')
        .and('Cost > 1')
        .during('20120101,20151231')
        .run();
    Logger.log(reportData);
}
```

```
{  
   "data":[  
      {  
         "Impressions":16559.0,
         "Year":"2012",
         "CampaignName":"Example Campaign",
         "Labels":null,
         "SearchImpressionShare":0.0,
         "Clicks":316.0,
         "Cost":582.33
      },
      {  
         "Impressions":906.0,
         "Year":"2012",
         "CampaignName":"Another Campaign Example",
         "Labels":null,
         "SearchImpressionShare":0.9902,
         "Clicks":25.0,
         "Cost":110.14
      },
      {  
         "Impressions":61.0,
         "Year":"2015",
         "CampaignName":". | AdWords Scripts | Research",
         "Labels":[  
            ".",
            "adwords scripts",
            "research",
            "blogg",
            "kaugesaar",
            "test",
            "test-t"
         ],
         "SearchImpressionShare":0.391,
         "Clicks":1.0,
         "Cost":4.81
      }
   ]
}
```

You can also utilize the exportToSheet function very simply.

```javascript
function main() {
    var ga = new AdWordsReport();
        ga.use({exportToSheet:true});
    var reportData = ga.awql()
        .select(['Clicks','Impressions','Year','Cost','SearchImpressionShare','Labels','CampaignName'])
        .from('CAMPAIGN_PERFORMANCE_REPORT')
        .where('Clicks > 0')
        .and('Impressions > 10')
        .and('Cost > 1')
        .during('20120101,20151231')
        .run();
    Logger.log(reportData);
}
```

A spreadsheet will be created on your google drive and in the object you have all the necessary information such as id, name and url.

```
{  
   "data":[  
      {  
         "Impressions":16559.0,
         "Year":"2012",
         "CampaignName":"Example Campaign",
         "Labels":null,
         "SearchImpressionShare":0.0,
         "Clicks":316.0,
         "Cost":582.33
      },
      {  
         "Impressions":906.0,
         "Year":"2012",
         "CampaignName":"Another Campaign Example",
         "Labels":null,
         "SearchImpressionShare":0.9902,
         "Clicks":25.0,
         "Cost":110.14
      },
      {  
         "Impressions":61.0,
         "Year":"2015",
         "CampaignName":". | AdWords Scripts | Research",
         "Labels":[  
            ".",
            "adwords scripts",
            "research",
            "blogg",
            "kaugesaar",
            "test",
            "test-t"
         ],
         "SearchImpressionShare":0.391,
         "Clicks":1.0,
         "Cost":4.81
      }
   ]
   "sheetName":"AdWordsReport - November 17, 2015",
   "sheetId":"1rfuQRUQn03aLkTKPoI9swoCq6r9RNDYFgH7CegMtSMU",
   "sheetUrl":"https://docs.google.com/spreadsheets/d/1rfuQRUQn03aLkTKPoI9swoCq6r9RNDYFgH7CegMtSMU/edit"
}
```

---

With inspiration from:
https://github.com/therebelrobot/google-adwords

Copyright (c) 2015, Trent Oswald (therebelrobot)
Permission to use, copy, modify, and/or distribute this software 
for any purpose with or without fee is hereby granted, provided 
that the above copyright notice and this permission notice appear 
in all copies.

THE SOFTWARE IS PROVIDED "AS IS" AND THE AUTHOR DISCLAIMS ALL WARRANTIES 
WITH REGARD TO THIS SOFTWARE INCLUDING ALL IMPLIED WARRANTIES OF 
MERCHANTABILITY AND FITNESS. IN NO EVENT SHALL THE AUTHOR BE LIABLE 
FOR ANY SPECIAL, DIRECT, INDIRECT, OR CONSEQUENTIAL DAMAGES 
OR ANY DAMAGES WHATSOEVER RESULTING FROM LOSS OF USE, DATA OR PROFITS, 
WHETHER IN AN ACTION OF CONTRACT, NEGLIGENCE OR OTHER TORTIOUS ACTION, 
ARISING OUT OF OR IN CONNECTION WITH THE USE OR PERFORMANCE OF THIS SOFTWARE.