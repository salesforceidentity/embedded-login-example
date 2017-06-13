embedded-login-example
====================

This simple app builds a basic PHP app running on Heroku and uses Salesforce Identity and the Login Widget project. Users have to log in to get access to data sheet.

Pre-requisites
--------------
You'll need an org that has a Community setup and active. Ideally you should have following the [Salesforce External Identity Implementation Guide](https://developer.salesforce.com/docs/atlas.en-us.externalidentityImplGuide.meta/externalidentityImplGuide/external_identity_intro.htm) to set up this org or you have completed the [Identity for Customers](https://trailhead.salesforce.com/module/identity_external) Trailhead module.

Steps to deploy
---------------
1. Deploy this app to Heroku [![Deploy](https://www.herokucdn.com/deploy/button.png)](https://heroku.com/deploy?template=https://github.com/salesforceidentity/embedded-login-example)
2. Create a CORS entry for your community's domain. [More details here](https://developer.salesforce.com/docs/atlas.en-us.externalidentityImplGuide.meta/externalidentityImplGuide/external_identity_login_step_1.htm)
3. Create a Connected App
	* Enable OAuth
	* Select openid scope
	* Set Callback to https://HEROKUAPP_URL/_callback.php e.g. https://strong-castle-20163.herokuapp.com/_callback.php
	* Save
	* Copy the Consumer Key
	* You will also want to Manage the Connected App and change the Permitted Users policy from User to Admin Approved. Then you will want to a Profile or Permission Set for the user you want to test.
4. Set the Heroku config vars via Setting > Reveal Config Vars:
	* "SALESFORCE_COMMUNITY_URL" to the Community's domain, no trailing slash and no "https://", For example: mycommunity.force.com/community2
	* "SALESFORCE_CLIENT_ID" to your Connected App's Consumer key
	* "SALESFORCE_HEROKUAPP_URL" to the URL of deployed Heroku App, no trailing slash and no "https://", for example bouncy-castle-1234.herokuapp.com
5. Optionally you can change the following Heroku config vars as well
	* "SALESFORCE_MODE" to either "modal" or "inline" to control how the login box is rendered
	* "SALESFORCE_FORGOT_PASSWORD_ENABLED" to either "true" or "false" depending if you want to display the forgot password link
	* "SALESFORCE_SELF_REGISTER_ENABLED" to either "true" or "false" depending if you want to display the user registration link
6. Open the app and enjoy!
