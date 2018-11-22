## NoVPAJpeg

NoVPAJpeg Lilu plugin: Disables the hardware JPEG decoding feature of the AppleVPA framework that breaks Preview and Quicklook on some systems.

Based (entirely) on [NoTouchID](https://github.com/al3xtjames/NoTouchID)

### Building

#### Xcode

Set LILU_VERSION in 'User-Defined' target build settings, then build.

#### Command line

Specify LILU_VERSION when running xcodebuild:

```
xcodebuild -target NoVPAJpeg -configuration Release LILU_VERSION=1.2.8
```

### License

Copyright (C) 2018 Alex James (TheRacerMaster).

Licensed under the Apache License, Version 2.0 (the "License"); you may not use this file except in compliance with the License. You may obtain a copy of the License at

http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software distributed under the License is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. See the License for the specific language governing permissions and limitations under the License.
