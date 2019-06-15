## NoVPAJpeg (Deprecated)

NoVPAJpeg.kext is deprecated.

In case its functionality is needed, use [WhateverGreen.kext](https://github.com/acidanthera/WhateverGreen) and add the following boot arguments:

```
shikigva=32 shiki-id=Mac-7BA5B2D9E42DDD94
```

NoVPAJpeg Lilu plugin: Disables the hardware JPEG decoding feature of the AppleVPA framework that breaks Preview and Quicklook on some systems.

Based (entirely) on [NoTouchID](https://github.com/al3xtjames/NoTouchID) by al3xtjames (TheRacerMaster)


### Building

#### Xcode

Set LILU_VERSION in 'User-Defined' target build settings, then build.

#### Command line

Specify LILU_VERSION when running xcodebuild:

```
git clone https://github.com/vulgo/NoVPAJpeg.git
cd NoVPAJpeg
xcodebuild -target NoVPAJpeg -configuration Release LILU_VERSION=1.2.8
```


### Configuration

NoVPAJpeg accepts the following boot arguments:

- ```-novpaoff``` disable NoVPAJpeg
- ```-novpabeta``` enable NoVPAJpeg on unsupported macOS versions (10.14 is supported by default)


### About

Preview or Quicklook will use the AppleVPA.framework's hardware JPEG decoding feature for Mac models with an IGPU, as enabled by board-id in this file:

```
/System/Library/PrivateFrameworks/AppleVPA.framework/Versions/A/Resources/Info.plist
```

If the feature is enabled, AppleVPA.framework looks for the IGPU driver using these exact [IORegistry](https://github.com/vulgo/IORegistryExplorer/releases) paths, trying both:

- ```IOService:/AppleACPIPlatformExpert/PCI0@0/AppleACPIPCI/IGPU@2```
- ```IOService:/AppleACPIPlatformExpert/PCI0@0/AppleACPIPCI/GFX0@2```

The Intel accelerator driver must be found using one of these paths, otherwise Preview or Quicklook will freeze.

For systems where the IGPU is unavailable, NoVPAJpeg introduces a patch for the AppleVPA.framework binary so that it no longer matches 'jpeg' in the above Info.plist, for any Mac model.

### Credits

[Cyberdevs](https://www.insanelymac.com/forum/topic/334881-how-to-fix-quicklook-and-preview-loading-issues-in-mojave/), [arsradu](https://www.insanelymac.com/forum/topic/334881-how-to-fix-quicklook-and-preview-loading-issues-in-mojave/)

### License

Copyright (C) 2018 Alex James (TheRacerMaster).

Licensed under the Apache License, Version 2.0 (the "License"); you may not use this file except in compliance with the License. You may obtain a copy of the License at

http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software distributed under the License is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. See the License for the specific language governing permissions and limitations under the License.
