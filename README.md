# build-props
This repo is meant for keeping a track of `build.prop` files and `getprop` outputs of different OnePlus devices.  
Some of these files were originally part of the [Android app repo](https://github.com/oxygen-updater/oxygen-updater) (and probably still are). We've separated them into their own repository, as it's easier to add/remove files if they're decoupled from the app's code.

# File naming schemes
File names are usually taken from the `ro.rom.version` field, stripping out "HydrogenOS", "OxygenOS", or variants of the OS name.  
The extension can either be `.prop` (for a `build.prop` file), or `.getprop` (for a `getprop` output), depending on what the file is.

# Directory structure
```java
├── ...
├──device-name
│  ├──regional-variant
│    ├──VERSION.BUILD_TAG.prop
│    ├──VERSION.BUILD_TAG.getprop
│    ├── ...
│  ├── ...
└── ...
```
**device-name**s are shortened forms: e.g. `op1`, `op6t`, `op7pro`  
**regional-variant**s are either:
* `eea`: EU
* `india`: India
* `intl`: International/Global
* Carrier variants (e.g. `t-mobile`, `sprint-5g`)  
  Generally, start with the carrier name, followed by any other differentiator (e.g. wireless technology (`5g`))

# FAQ
### How do we obtain these files?
`build.prop`s are usually extracted directly from the ZIP, or copied manually from a rooted device.
A `getprop` output can be obtained either by:
* Installing ADB, connecting the device, and running the `adb shell getprop > filename.getprop`
* Installing a terminal app from the Play Store, and running the `getprop > filename.getprop` command within that app  
  Note: depending on the app, you might have to manually copy-paste the entire output into a file, as some apps don't support writing files to internal storage

Either way, make sure you rename the file to match the appropriate [naming scheme](#file-naming-schemes).

### I'm not an Oxygen Updater project team member. Can I add files too?
Absolutely! Just fork this project, make changes, and open a PR.
