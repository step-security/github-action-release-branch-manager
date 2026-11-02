[![StepSecurity Maintained Action](https://raw.githubusercontent.com/step-security/maintained-actions-assets/main/assets/maintained-action-banner.png)](https://docs.stepsecurity.io/actions/stepsecurity-maintained-actions)



<!-- markdownlint-disable -->


<p align="right"><a href="https://github.com/step-security/github-action-release-branch-manager/releases/latest"><img src="https://img.shields.io/github/release/step-security/github-action-release-branch-manager.svg?style=for-the-badge" alt="Latest Release"/></a><a href="https://github.com/step-security/github-action-release-branch-manager/commits"><img src="https://img.shields.io/github/last-commit/step-security/github-action-release-branch-manager.svg?style=for-the-badge" alt="Last Updated"/></a><a

</p>


GitHub Action for Managing Release Branches




## Introduction

This GitHub Action adopts a streamlined approach to managing release branches, drawing on a trunk-based branching strategy. In this model, the `DEFAULT_BRANCH` consistently represents the most recent release, while release branches are exclusively created for previous major releases, if applicable. This structure simplifies the process for contributors when submitting Pull Requests for bug fixes or backporting modifications to older releases, as it enables them to target a specific major release.

**How it works:** upon publishing a new major release `N`, a corresponding branch for the previous release `N-1` will be automatically generated.

Imagine you have tags like this in your repo:

```
0.1.0
0.2.0
1.0.0
1.1.0
1.2.0
1.2.1
2.0.0
2.1.0
2.2.0
3.0.0
3.1.0   main
```

Upon the first release published event, the "release branch manager" will generate new branches named `release/vN-1`, where N corresponds to the latest tag of each major release. In this case, several new branches will be created:

```
0.1.0
0.2.0   release/v0
1.0.0
1.1.0
1.2.0
1.2.1   release/v1
2.0.0
2.1.0
2.2.0   release/v2
3.0.0
3.1.0   main
```

Note that `3.1.0` is latest tag and release branch manager wouldn't create release branch because latest major release is maintained in `main` branch.

If you wish to make changes to `2.2.0`, you must create a pull request for the `release/v2` branch and generate a corresponding release/tag with a major version of `2`, for example, `2.3.0`.

This action requires GitHub releases to follow the [SemVer versioning](https://semver.org/) scheme.




## Usage

Example of workflow that that will create major release tags. To use it, just add this workflow to your `.github/workflows` directory. 

```yaml
  name: Manager Release Branch

  on:
    release:
      types:
        - published

  jobs:
    publish:
      runs-on: ubuntu-latest
      steps:
        - uses: step-security/github-action-release-branch-manager@v1
```












## Related Projects

Check out these related projects.

- [Major Release Tagger GitHub Action](https://github.com/step-security/github-action-major-release-tagger) - GitHub Action that automatically generates or updates `v<major-release>` tags every time a new release is published.

## References

For additional context, refer to some of these links.

- [Release Drafter GitHub Action](https://github.com/step-security/release-drafter) - Drafts your next release notes as pull requests are merged into your default branch.
- [Release Branch Manager GitHub Action](https://github.com/step-security/github-action-release-branch-manager) - Automatically creates "Long Term Support (LTS)" release branches when new releases are published
- [Major Release Tagger GitHub Action](https://github.com/step-security/github-action-major-release-tagger) - GitHub Action that automatically generates or updates `v<major-release>` tags every time a new release is published.




## License

<a href="https://opensource.org/licenses/Apache-2.0"><img src="https://img.shields.io/badge/License-Apache%202.0-blue.svg?style=for-the-badge" alt="License"></a>

<details>
<summary>Preamble to the Apache License, Version 2.0</summary>
<br/>
<br/>

Complete license is available in the [`LICENSE`](LICENSE) file.

```text
Licensed to the Apache Software Foundation (ASF) under one
or more contributor license agreements.  See the NOTICE file
distributed with this work for additional information
regarding copyright ownership.  The ASF licenses this file
to you under the Apache License, Version 2.0 (the
"License"); you may not use this file except in compliance
with the License.  You may obtain a copy of the License at

  https://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing,
software distributed under the License is distributed on an
"AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY
KIND, either express or implied.  See the License for the
specific language governing permissions and limitations
under the License.
```
</details>

## Trademarks

All other trademarks referenced herein are the property of their respective owners.


---
Copyright © 2017-2025 [Cloud Posse, LLC](https://cpco.io/copyright)
Copyright 2026 StepSecurity


<a href="https://cloudposse.com/readme/footer/link?utm_source=github&utm_medium=readme&utm_campaign=step-security/github-action-release-branch-manager&utm_content=readme_footer_link"><img alt="README footer" src="https://cloudposse.com/readme/footer/img"/></a>

<img alt="Beacon" width="0" src="https://ga-beacon.cloudposse.com/UA-76589703-4/step-security/github-action-release-branch-manager?pixel&cs=github&cm=readme&an=github-action-release-branch-manager"/>
