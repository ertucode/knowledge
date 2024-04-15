```cli
dotnet add package JUnitTestLogger
```

-   Run ci on merge request
-   Settings -> Merge requests -> Pipelines must succeed

```yml
image: mcr.microsoft.com/dotnet/sdk:8.0

services:
    - docker:dind # testcontainers

variables:
    DOCKER_HOST: tcp://docker:2375 # testcontainers

stages:
    - test

before_script:
    - "dotnet restore"

test:
    stage: test
    script:
        - dotnet test --logger "junit;LogFilePath=TestResult.xml"
    artifacts:
        when: always
        reports:
            junit: "**/TestResult.xml"
    rules:
        - if: '$CI_MERGE_REQUEST_TARGET_BRANCH_NAME == "main"'
```
