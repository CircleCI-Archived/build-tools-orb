# Build Tools Orb ![CircleCI status](https://circleci.com/gh/CircleCI-Public/build-tools-orb.svg "CircleCI status") [![CircleCI Orb Version](https://img.shields.io/badge/endpoint.svg?url=https://badges.circleci.io/orb/circleci/build-tools)](https://circleci.com/orbs/registry/orb/circleci/build-tools) [![GitHub license](https://img.shields.io/badge/license-MIT-blue.svg)](https://raw.githubusercontent.com/circleci-public/build-tools-orb/master/LICENSE) [![CircleCI Community](https://img.shields.io/badge/community-CircleCI%20Discuss-343434.svg)](https://discuss.circleci.com/c/ecosystem/orbs)

An orb with a few handy tools for use in CircleCI Builds. Intended purposes include:

1. Help guide people using CircleCI to solve problems and optimize their configurations.
2. Help surface and collect information so CircleCI engineers can help solve problems.

## Usage:

Reference the orb in your `config.yml` file. 2.1 Build Processing must be enabled on the project. Check the bottom of your `Advanced Settings` section in your project settings.

```yaml
orbs:
  build-tools: circleci/build-tools@x.y.z
```

Following is a selection of the diagnostic-focused commands available in the orb. For full usage guidelines, [see the orb registry listing](https://circleci.com/orbs/registry/orb/circleci/build-tools).

Most diagnostic commands are intended to be applied as `pre-steps` and `post-steps` (see [Reusing Config documentation](https://circleci.com/docs/2.0/reusing-config/#using-pre-and-post-steps)). Always include `build-tools/post-steps` to collect results generated in `pre-steps`.

```yaml
workflows:
  my-workflow:
    jobs:
      - my-super-neat-job:
          pre-steps:
            - build-tools/env-info
          post-steps:
            - build-tools/store-report
```

The commands below are indended to be added as `pre-steps` for jobs you'd like to investigate.

### [`build-tools/env-info`](https://circleci.com/orbs/registry/orb/circleci/build-tools#commands-env-info)
Generate a report of various kinds of enviroment information. Helpful to find out what packages are install in the enviroment.

```yaml
build-tools/env-info
```

### [`build-tools/ios-logs`](https://circleci.com/orbs/registry/orb/circleci/build-tools#commands-ios-logs)
Save Fastlane and Xcode information from an iOS job, to be stored as artifacts and inspected later.

```yaml
build-tools/ios-logs
```

### [`build-tools/memory`](https://circleci.com/orbs/registry/orb/circleci/build-tools#commands-memory)
Start top as a background process that appends output to a file. Helpful to see memory consumption and process lifecycle over the duration of a job

```yaml
build-tools/memory
```

### [`build-tools/test-results`](https://circleci.com/orbs/registry/orb/circleci/build-tools#commands-test-results)
Create sample test JUnit XML output for Test Summary report. Helpful if you want to sanity check if test data collection is working.

```yaml
build-tools/test-results
```

## Contributing
We welcome [issues](https://github.com/CircleCI-Public/build-tools-orb/issues) (bugs or feature requests) and [pull requests](https://github.com/CircleCI-Public/build-tools-orb/pulls)!

For larger discussions, there is also an active community at https://discuss.circleci.com/c/orbs.
