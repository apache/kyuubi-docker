<!--
 - Licensed to the Apache Software Foundation (ASF) under one or more
 - contributor license agreements.  See the NOTICE file distributed with
 - this work for additional information regarding copyright ownership.
 - The ASF licenses this file to You under the Apache License, Version 2.0
 - (the "License"); you may not use this file except in compliance with
 - the License.  You may obtain a copy of the License at
 -
 -   http://www.apache.org/licenses/LICENSE-2.0
 -
 - Unless required by applicable law or agreed to in writing, software
 - distributed under the License is distributed on an "AS IS" BASIS,
 - WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
 - See the License for the specific language governing permissions and
 - limitations under the License.
 -->

Kyuubi Docker Release Guide
===

## Prerequisites

Make sure Kyuubi has released a new version.

## Steps

### Feature release

1. Submit a pull request to the **master** branch to update the `release_version` file to the new **minor** version.
2. After the pull request is merged, push a new tag to the commit to trigger a workflow that builds and pushes a new image to dockerhub.
3. Make sure the workflow completes successfully and new image is available on dockerhub.
4. Create a new branch from the commit using the version in the branch name.

### Patch release

1. Submit a pull request to the **minor** release branch to update the `release_version` file to the new **patch** version.
2. After the pull request is merged, push a new tag to the commit to trigger a workflow that builds and pushes a new image to dockerhub.
3. Make sure the workflow completes successfully and new image is available on dockerhub.
