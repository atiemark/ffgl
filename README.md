This is the Resolume fork of the FFGL repository. It is up to date and has Visual Studio and Xcode projects to compile 32 bit and 64 bit plugins.

The master branch is used for continued development. It will contain the latest features, fixes and bugs. Plugins compiled with the master branch will work in Resolume 7.0.3 and up.
If you do not want to be affected by the latest bugs you can use a different branch. eg the FFGL 2.1 branch, which is the most recent released version of the sdk: https://github.com/resolume/ffgl/tree/ffgl2.1. To compile plugins for resolume 7.0.0/7.0.1/7.0.2 you will need to use the ffgl2.0 sdk because these hosts do not support the new features introduced in FFGL 2.1.

To compile plugins for hosts that support FFGL 1.6 (Resolume 6, VDMX, COGE, Isadora, Magic Music Visuals), switch to the FFGL1.6 branch: https://github.com/resolume/ffgl/tree/ffgl1.6

You can find some help to get started with FFGL plugin development on the [wiki](https://github.com/resolume/ffgl/wiki).

Also more examples are available on this [repo](https://github.com/flyingrub/ffgl/tree/more/).

## Changes since FFGL 2.1
- Added context state validation in debug builds. This provides plugin developers hints on which context state they need to restore.
- Removed default DllMain implementation so that plugins may implement it without changing the ffgl library.
- File parameters now accept an initial value just like text parameters. (This requires Resolume 7.2 for it to be picked up)
- Added support for grouping parameters together. Set a parameter's group with SetParamGroup, any cosecutive params with the same group will be listed under the same collapsable region
- Added support for top-left texture orientation. Hosts that are rendering with the top-left texture orientation currently need to flip both inputs and the output every frame. A plugin can now inform the host that it supports the top-left orientation by setting supportTopLeftTextureOrientation to true. If the host wants to use it then it'll inform the plugin, which can query if it should use top-left or bottom-left using the GetTextureOrientation function.
