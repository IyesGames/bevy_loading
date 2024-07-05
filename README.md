# Progress Tracking Helper Crate

[![Crates.io](https://img.shields.io/crates/v/iyes_progress)](https://crates.io/crates/iyes_progress)
[![docs](https://docs.rs/iyes_progress/badge.svg)](https://docs.rs/iyes_progress/)
[![MIT/Apache 2.0](https://img.shields.io/badge/license-MIT%2FApache-blue.svg)](./LICENSE)

**This crate was formerly known as `bevy_loading`!**

Bevy Compatibility:

| Bevy Version | Plugin Version       |
|--------------|----------------------|
| `main`       | N/A                  |
| `0.14`       | `0.12`,`main`        |
| `0.13`       | `0.11`               |
| `0.12`       | `0.10`               |
| `0.11`       | `0.9`                |
| `0.10`       | `0.8`                |
| `0.9`        | `0.7`                |
| `0.8`        | `0.4`,`0.5`, `0.6`   |
| `0.7`        | `0.3`                |
| `0.6`        | `bevy_loading = 0.2` |
| `0.5`        | `bevy_loading = 0.1` |

---

This crate helps you in cases where you need to track when a bunch of
work has been completed, and perform a state transition.

The most typical use case are loading screens, where you might need to
load assets, prepare the game world, etc… and then transition to the
in-game state when everything is done.

However, this crate is general, and could also be used for any number of
other things, even things like cooldowns and animations.

To use this plugin, add one or more instances `ProgressPlugin` to your
`App`, configuring for the relevant states.

Implement your tasks as regular Bevy systems that return a `Progress`
and add them to your respective state(s) using `.track_progress()`.

The return value indicates how much progress a system has completed so
far. It specifies the currently completed "units of work" as well as
the expected total.

When all registered systems return a progress value where `done >= total`,
your desired state transition will be performed automatically.

If you need to access the overall progress information (say, to display a
progress bar), you can get it from the `ProgressCounter` resource.

---

There is also an optional feature (`assets`) implementing basic asset
loading tracking. Just add your handles to the `AssetsLoading` resource.

If you need something more advanced, I recommend the `bevy_asset_loader`
crate, which now has support for integrating with this crate. :)

## Example

See the [example](./examples/full.rs) for an overview of how to use this crate.
