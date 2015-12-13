# command-server
A simple Slack slash command server example

Clone the command server:
```
git clone git@github.com:gregmercer/command-server.git
cd command-server
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

Adding command-server to Heroku

Log into Heroku
```
heroku login
```

Create a new app (called command-server) on Heroku
```
heroku create --app command-server
```

Create a new git repo and commit
```
git init
git add .
git cm 'initial commit'
```

Connect to the remote git repo on Heroku related to our new app
```
heroku git:remote -a command-server
```

Push the files to Heroku
```
git push heroku master
```

Add the simple command token to Heroku as a setting

In Chrome, go to your new app's setting page
```
https://dashboard.heroku.com/apps/command-server/settings
```

Add a new setting the simple command token
```
COMMAND_SIMPLE_TOKEN    <any value for right now>
```

Testing your Heroku command-server

Run Dev HTTP Client in a Chrome tab
```
chrome-extension://aejoelaoggembcahagimdiliamlcdmfm/dhc.html
```

Set Request, URL and Method
```
HTTPS
command-server.herokuapp.com/svc/slack/simple
POST
```

Enter Post Body
```
{"token":"<the value you set for COMMAND_SIMPLE_TOKEN>", "text": "Text sent to command-simple handler"}
```

Click on Send Button and see view test results in 'Response' section.







