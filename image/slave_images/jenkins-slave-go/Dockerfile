#
# Copyright 2015 Google Inc. All Rights Reserved.
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#     http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.
#

FROM gcr.io/developer_tools_bundle/jenkins-base

RUN apt-get update && apt-get install -y --no-install-recommends golang-go && apt-get clean

RUN yes | gcloud components update pkg-go

ENV GOPATH /gopath
ENV PATH $GOPATH/bin:$PATH

# Pull down all the common app engine dependencies
RUN go get google.golang.org/appengine

# This is needed to translate Go test output into xUnit as the canonical test result format
RUN go get bitbucket.org/tebeka/go2xunit

# Set up a GOROOT from the Cloud SDK and put goapp on the path
ENV GOROOT $CLOUD_SDK/platform/google_appengine/goroot/
ENV PATH $GOROOT/bin:$PATH