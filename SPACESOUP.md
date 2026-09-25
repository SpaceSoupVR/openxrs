# SpaceSoupVR fork of openxrs

This branch (`spacesoup/v0.18.0`) is upstream **openxr 0.18.0 / openxr-sys
0.10.0** (`d05c74a`), the exact release our standalone-VR runtime builds
against, plus the patches below. Everything else is unchanged upstream code under
its original licences (MIT / Apache-2.0).

## Why a fork

Meta's runtime offers performance extensions newer than these bindings. The one
we need first is **`XR_META_recommended_layer_resolution`**, which is missing
from openxr-sys 0.10.0. It lets the runtime drive dynamic resolution, and on
Quest 3 dynamic resolution is the prerequisite for the highest GPU clock level.

Already present and used as-is: `XR_FB_foveation(_vulkan|_configuration)`,
`XR_META_vulkan_swapchain_create_info`, `XR_FB_space_warp`,
`XR_FB_display_refresh_rate`, `XR_EXT_performance_settings`,
`XR_META_performance_metrics`, `XR_FB_composition_layer_settings`.

## Planned patches

- [ ] Add `XR_META_recommended_layer_resolution` to `sys` (generated from the
      current Khronos registry) and a safe wrapper in `openxr`.
- [ ] Refresh the generated bindings from the latest `xr.xml`, so any newer
      Meta/Khronos extension is one wrapper away.

## Using it

```toml
[patch.crates-io]
openxr     = { git = "https://github.com/SpaceSoupVR/openxrs", branch = "spacesoup/v0.18.0" }
openxr-sys = { git = "https://github.com/SpaceSoupVR/openxrs", branch = "spacesoup/v0.18.0" }
```

## Policy

- One branch per upstream release (`spacesoup/vX.Y.Z`), patches rebased onto it.
- Patches stay small and upstreamable.
