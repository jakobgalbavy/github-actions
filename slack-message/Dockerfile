FROM debian:9.6-slim

LABEL "com.github.actions.name"="Post Slack messages"
LABEL "com.github.actions.description"="Post Slack messages from your own bot"
LABEL "com.github.actions.icon"="hash"
LABEL "com.github.actions.color"="gray-dark"

LABEL version="1.0.5"
LABEL repository="https://github.com/jakobgalbavy/github-actions"
LABEL homepage="https://github.com/jakobgalbavy/github-actions"
LABEL maintainer="jakob@galbavy.at"

RUN apt-get update && apt-get install -y curl

ADD entrypoint.sh /entrypoint.sh
ENTRYPOINT ["/entrypoint.sh"]