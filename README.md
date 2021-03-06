# command-server
A simple Slack Slash Command Server example, includes a very simple slash command (command-simple).

This Slash Command Server supports new slash commands by creating and installing new npm modules.

In the following steps we'll cover how to:
```
1. Clone a copy of the Command Server locally.
2. Run and test the Command Server locally.
3. Install the Command Server on Heroku.
4. Testing you Slash Command on Slack
5. Adding a new Slash Command.
```

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
COMMAND_SIMPLE_TOKEN=<any value for right now> node server.js
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
{"token":"<any value for right now>", "text": "Text sent to command-simple handler"}
```

Click on Send Button and view test results in the 'Response' section.

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
{"token":"<any value for right now>", "text": "Text sent to command-simple handler"}
```

Click on Send Button and see view test results in 'Response' section.

Testing your Slash Command on Slack

Go to your team's Slack integration page
```
https://<your team>.slack.com/apps/manage/custom-integrations
```

Enter the name of your command in the 'Command' field:
```
/simple
```

Enter your Slash Command Server url into the 'URL' field:
```
https://command-server.herokuapp.com/svc/slack/simple
```
Change the 'Method' to be set to 'Post'

Check the 'Show this command in the autocomplete list' checkbox

Click the 'Save Integration' button. 

Copy the 'Token' for your Slash Command.

Re-edit your Heroku app settings.

In Chrome, go to your new app's setting page
```
https://dashboard.heroku.com/apps/command-server/settings
```

Add a new setting the simple command token
```
COMMAND_SIMPLE_TOKEN    <the token value copied from Slack>
```

Test the Slash command in Slack

Go to a channel in Slack and enter:
```
'/simple whatever'
```

You should see this response within Slack:
```
slackbot [3:47 PM] Only you can see this message
Received commmand with text: whatever
```

Adding a new Slash Command:
```
1. First create a Slash Command and upload to github
2. Publish the new Slash Command on npmjs.com
3. Add your new Slash Command to your Slash Command Server
4. Test your new Slash Command on Slack
```

You can create your new Slash Command by copying command-simple

Clone the command server:
```
git clone git@github.com:gregmercer/command-simple.git
cd command-simple
``` 

Copy the following files into a new directory:
```
lib/command-simple.js
index.js
LICENSE.md
package.json
README.md
```

Change any mentions of command-simple to the name of your new command.

You can see another example at:
```
https://github.com/gregmercer/command-chart
```

Upload your new command to your github account.

Publish your new command to npmjs.com

Type the following in the directory of your new command:
```
npm login
npm publish
```

Check that your new command has been published. 
You should see it listed on your npmjs account page.

In Chrome, go to your npmjs.com account page:
```
https://www.npmjs.com/~<your account name>
```

Install the new command on your Slash Command Server
```
npm i --save <the name of your new command>
```

This should update the following file on your Slash Command Server:
```
package.json
```

Update the 'handlers.json' file on your Slash Command Server to have a new entry for your new command.

Your 'handlers.json' file should now look something like this:
```
[
  {
    "command": "simple",
    "pkg": "command-simple",
    "tokenVar": "COMMAND_SIMPLE_TOKEN",
    "options": {"protocol": "https"}
  },
  {
    "command": "chart",
    "pkg": "command-chart",
    "tokenVar": "COMMAND_CHART_TOKEN",
    "options": {"protocol": "https"}
  }
]
```

To re-test on Heroku and in Slack, you'll need to use git to add, commit and push the changes for 'package.json' and 'handlers.json' to Heroku.

You'll also need to add your new slash command as a new integration in Slack, and add a new token setting on your Slash Command Server's Heroku app settings page.










