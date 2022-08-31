## Homework 1
*[#homework]() [#cicd1]()*
1. Open gitlab
2. Create a new private project in personal space.
3. Create a pipeline with 3 stages “build – test – deploy” with dummy `echo` scripts.
4. Send screenshot of pipeline in chat with homework's hashtags.

### Links 1
- [Martin Fowler’s CI](https://martinfowler.com/articles/continuousIntegration.html)
- [Martin Fowler’s CD](https://martinfowler.com/bliki/ContinuousDelivery.html)
- [CD SAFE](https://v46.scaledagileframework.com/continuous-delivery-pipeline)
- [Gitlab docs](https://docs.gitlab.com)
- [Registering Gitlab Runner](https://docs.gitlab.com/runner/register/index.html)

## Homework 2-1
*[#homework]() [#cicd2-1]()*
1. Import [course project](https://github.com/tdevopsschool/course-project/tree/main) into personal gitlab space.
2. Configure **.gitlab-ci.yml** to build applications in pipelines without dockerization.
3. Keep builded jar files as artifacts with expiration in 1 hour.
4. Send screenshots of artifacts in chat with homework's hashtags.

### Links 2-1
- [Import project fron GitHub to Gitlab](https://docs.gitlab.com/ee/user/project/import/github.html)
- [.gitlab-ci.yml file](https://docs.gitlab.com/ee/ci/yaml/gitlab_ci_yaml.html)
- [Predefined variables](https://docs.gitlab.com/ee/ci/variables/predefined_variables.html)
- [Gitlab job artifacts](https://docs.gitlab.com/ee/ci/pipelines/job_artifacts.html)

## Homework 2-2
*[#homework]() [#cicd2-2]()*
1. Rewrite **.gitlab-ci.yml** to use `include` directive:
- Create another one repo for CI yml files
- Move CI from main repos into new CI repo
- Use `include` to merge CI into main repos
2. Screenshot with files of new CI repo should be in chat with homework's hashtags.

### Links 2-2
- [Gitlab anchors](https://docs.gitlab.com/ee/ci/yaml/yaml_optimization.html#anchors)
- [Gitlab extends](https://docs.gitlab.com/ee/ci/yaml/yaml_optimization.html#use-extends-to-reuse-configuration-sections)
- [Gitlab CI include](https://docs.gitlab.com/ee/ci/yaml/includes.html)
- [Use extends and include together](https://docs.gitlab.com/ee/ci/yaml/yaml_optimization.html#use-extends-and-include-together)

## Homework 3
*[#homework]() [#cicd3]()*
1. Remove arifacts section and change build to using `./gradlew jib` plugin task. Jib builds docker container without Docker daemon, so you are free to use any gitlab runner for that task
```bash
./gradlew 
--build-cache 
--parallel 
--max-workers=3 
-g /cache/.gradle 
jib 
-Djib.console=plain 
-PappName=Devops-School-App 
-Pversion=1.0
-Pregistry=<DOCKER_REGISTRY>
-PregistryPushImage=<DOCKER_IMAGE>
-PregistryPushUser=<REGISTRY_USER>
-PregistryPushPassword=<REGISTRY_PASSWORD>
--no-daemon -s
```
3. Configure **build.gradle** of backend and frontend to push created images into gitlab registry with pipeline number tag
4. Addinitionally you need to add docker config into **.gitlab-ci.yml** for pushing by jib plugin
```bash
- >  # Render docker config using Gitlab Variables
      printf '{"auths":{"%s":{"auth":"%s"}}}'
      $GITLAB_REGISTRY $(echo "$GITLAB_REGISTRY_USER:$GITLAB_REGISTRY_PASSWORD" | tr -d '\n' | base64 -i -w 0) > ~/.docker/config.json
- export DOCKER_CONFIG=~/.docker/config.json
```
5. Send screenshots of images from gitlab docker registries with homework's hashtags.

### Links 3
- [Kaniko docs](https://github.com/GoogleContainerTools/kaniko)
- [Using Kaniko to build Docker images](https://docs.gitlab.com/ee/ci/docker/using_kaniko.html)
- (https://book.hacktricks.xyz/linux-hardening/privilege-escalation/docker-breakout/docker-breakout-privilege-escalation)

## Homework 4-1
*[#homework]() [#cicd4-1]()*

*You will use this workpiece later in Kubernetes module*
1. Add dummy deploy jobs for “dev” and “prod” environments.
3. Add any URLs for both environments.
4. Screenshot with environments should be in chat with homework's hashtags.

### Links 4-1

## Homework 4-2
*[#homework]() [#cicd4-2]()*
1. Add gradle cache and image cache for build jobs. (?)
2. When added – send line from job with homework's hashtags

### Links 4-2
