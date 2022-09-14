## Homework 1
*[#homework]() [#cicd1]()*
1. Open gitlab.
2. Import [course project](https://github.com/tdevopsschool/course-project/tree/main) into personal gitlab space.
3. Create a pipeline with 3 stages “build – test – deploy” with dummy `echo` scripts.
4. Send screenshot of pipeline in chat with homework's hashtags.

### Links 1
- [Gitlab docs](https://docs.gitlab.com)
- [Registering Gitlab Runner](https://docs.gitlab.com/runner/register/index.html)
- [Import project to Gitlab by URL](https://docs.gitlab.com/ee/user/project/import/repo_by_url.html)

Additional
- [Martin Fowler’s CI](https://martinfowler.com/articles/continuousIntegration.html)
- [Martin Fowler’s CD](https://martinfowler.com/bliki/ContinuousDelivery.html)
- [CD SAFE](https://v46.scaledagileframework.com/continuous-delivery-pipeline)

## Homework 2-1
*[#homework]() [#cicd2-1]()*
1. Remove all dummy stages from previous homework except build stage.
2. Configure **.gitlab-ci.yml** to build applications in build stage without dockerization.
3. Keep builded jar files as job artifacts with expiration in 1 hour.
4. Send screenshots of artifacts in chat with homework's hashtags.

### Links 2-1
- [.gitlab-ci.yml file](https://docs.gitlab.com/ee/ci/yaml/gitlab_ci_yaml.html)
- [Predefined variables](https://docs.gitlab.com/ee/ci/variables/predefined_variables.html)
- [Gitlab job artifacts](https://docs.gitlab.com/ee/ci/pipelines/job_artifacts.html)

## Homework 2-2
*[#homework]() [#cicd2-2]()*
1. Keep gradle cache for build jobs.
2. When added – send line that cache is created and stored from jobs logs with homework's hashtags.

### Links 2-2
- [Gitlab caching](https://docs.gitlab.com/ee/ci/caching/)

## Homework 3-1
*[#homework]() [#cicd3-1]()*
1. Remove arifact and cache sections.
2. Use **dind service** to build and push images.
3. Addinitionally you need to add docker config into **.gitlab-ci.yml** for pushing images. Use **before_script** for that
```bash
- >  # Render docker config using Gitlab Variables
      printf '{"auths":{"%s":{"auth":"%s"}}}'
      $GITLAB_REGISTRY $(echo "$GITLAB_REGISTRY_USER:$GITLAB_REGISTRY_PASSWORD" | tr -d '\n' | base64 -i -w 0) > ~/.docker/config.json
- export DOCKER_CONFIG=~/.docker/config.json
```
4. Send screenshots of using dind in **gitlab-ci.yml** with homework's hashtags.

### Links 3-1
- [Use Docker-in-Docker](Docker-in-Docker with TLS enabled in the Docker executor)
- [Use Docker to build Docker images](https://docs.gitlab.com/ee/ci/docker/using_docker_build.html)

Additional
- [Docker breakout privilege escalation](https://book.hacktricks.xyz/linux-hardening/privilege-escalation/docker-breakout/docker-breakout-privilege-escalation)
- [Understanding Docker container escapes](https://blog.trailofbits.com/2019/07/19/understanding-docker-container-escapes)

## Homework 3-2
*[#homework]() [#cicd3-2]()*
1. Remove dind solution and use Kaniko instead.
2. Send screenshots of using Kaniko in **gitlab-ci.yml** with homework's hashtags.

### Links 3-2
- [Kaniko docs](https://github.com/GoogleContainerTools/kaniko)
- [Using Kaniko to build Docker images](https://docs.gitlab.com/ee/ci/docker/using_kaniko.html)

## Homework 4-1
*[#homework]() [#cicd4-1]()*
1. Rewrite **.gitlab-ci.yml** to use `include` directive:
- Create another one repo for CI yml files
- Move CI from main repos into new CI repo
- Use `include` to merge CI into main repos
2. Screenshot with files of new CI repo should be in chat with homework's hashtags.

### Links 4-1
- [Gitlab anchors](https://docs.gitlab.com/ee/ci/yaml/yaml_optimization.html#anchors)
- [Gitlab extends](https://docs.gitlab.com/ee/ci/yaml/yaml_optimization.html#use-extends-to-reuse-configuration-sections)
- [Gitlab CI include](https://docs.gitlab.com/ee/ci/yaml/includes.html)
- [Use extends and include together](https://docs.gitlab.com/ee/ci/yaml/yaml_optimization.html#use-extends-and-include-together)

## Homework 4-2
*[#homework]() [#cicd4-2]()*
*You will use this workpiece later in Kubernetes module*
1. Add dummy deploy jobs for “dev” and “prod” environments.
2. Add any URLs for both environments.
3. Screenshot with environments should be in chat with homework's hashtags.

### Links 4-2
- [Environments and deployments](https://docs.gitlab.com/ee/ci/environments/)

## Additional links
- [API resources](https://docs.gitlab.com/ee/api/api_resources.html)
