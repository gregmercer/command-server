# command-server
A simple Slack slash command server example

Clone the command server:
```
git clone git@github.com:gregmercer/command-server.git
```

Install the require packages:
```
npm i --save body-parser
npm i --save command-simple
npm i --save cookie-parser
npm i --save debug
npm i --save express
npm i --save lodash
npm i --save morgan
npm i --save nconf
```

Edit run.sh. Enter your Slack token
```
COMMAND_SIMPLE_TOKEN=<your slack token goes here> node server.js
```

Run the command server locally:
```
sh run.sh
```

Test the command server locally:

Install Chrome extension Dev HTTP Client (DHC - REST/HTTP API Client)
```
https://chrome.google.com/webstore/detail/dhc-resthttp-api-client/aejoelaoggembcahagimdiliamlcdmfm?hl=en
```

Run Dev HTTP Client in a Chrome tab
```
chrome-extension://aejoelaoggembcahagimdiliamlcdmfm/dhc.html
```

Set Request, URL and Method
```
HTTP
localhost:3000/svc/slack/simple
POST
```

Enter Post Body
```
{"token":"<your slack token goes here>", "text": "Text sent to command-simple handler"}
```

Click on Send Button and see view test results in 'Response' section.






