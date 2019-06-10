## HowTo: SlackMessage

* Create a Slackbot and save the UserToken
* Set the UserToken in your Actions as Secret `SLACK_BOT_USER_TOKEN`
* Invite that new Slackbot to your channel `/invite @your_bots_name`
* Get your Slack Channel code by visiting `http://XXXXXXXX.slack.com/`, click on your Channel and grab the code from the URL (`https://XXXXXXXX.slack.com/messages/<<This is what you need>>/`)
* Add the Action below to your workflow
```
action "notify slack" {
  needs = "<<previous steps>>"
  uses = "jakobgalbavy/github-actions/slack-message@master"
  secrets = [
    "SLACK_BOT_USER_TOKEN",
  ]
  env = {
    slack_channel = "<<channel_code>>",
    slack_pretext = "A new artifact was published to S3",
    slack_title = "GITHUB_REPOSITORY",
    slack_text = "User name: _GITHUB_ACTOR_<br>Branch name: _GITHUB_REF_<br>*ARTIFACT_NAME*"
  }
}
```

### Variables
You can just put any of these Keys inside any of your env Variables and the will be replaced afterwards.

Key | Value
------------ | -------------
<br> | Newline
GITHUB_REPOSITORY | Name of the Repository
GITHUB_ACTOR | Username of the Person who published
GITHUB_REF | The Branch name this was built on
ARTIFACT_NAME | This is specific for Java builds and will return the latest Artifact from the `build/` directory. 
