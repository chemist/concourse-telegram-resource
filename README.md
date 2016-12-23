## Telegram resource
Send message via telegram.

##Config
* `bot`: *Required* Bot id, for example bot132413421234:string
* `chat_id`: *Required* Chat id

###Example
```
resource_types:
- name: bot
  type: docker-image
  source:
    repository: chemist/concourse-telegram-resource
    tag: latest

jobs:
- name: test
  plan:
  - task: bash script in task
    on_success:
      put: telegram
      params:
        message: build success
    config:
      platform: linux
      image_resource:
        type: docker-image
        source: {repository: chemist/alpine-fpm, tag: "latest"}
      run:
        path: sh
        args:
          - -exc
          - |
              TERM=screen-256color
              echo hello

```
