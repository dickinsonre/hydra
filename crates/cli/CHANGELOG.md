# Changelog

## [5.0.0](https://github.com/dickinsonre/hydra/compare/cli-v4.1.1...cli-v5.0.0) (2026-11-08)


### ⚠ BREAKING CHANGES

* **common,wds,uds:** `produce_report_block` takes the run's diagnostics, and `SessionWarning::element` is now `element_id`. The CLI and GUI edits here are the mechanical call-site updates that keeps them compiling; splitting them out would need a red intermediate, so the release-track signal reads as breaking for all three tracks when only the library's API changed.
* **wds:** hold one instant, not the whole run
* Simulation::open and the open_with_* family, write_report/write_out, the interface-file writers, supply_* by text, and begin_*_results moved to hydra::swmm::session as free functions; OpenError::Parse now lives on the dialect's OpenError, wrapping the engine's build refusals.
* **uds:** mesh models that previously refused with "specified and not yet served" now open and run; OpenError::Overland carries attach defects instead of the serving refusal.
* **uds:** ValidationKind::InterfaceFileNotWritten is removed. It reported a declared interface file that would not be written, and every format §14.8 declares is now served, so nothing can emit it.

### What's New

* **cli:** expose the tank level tolerance as --tank-tolerance ([b6c7d49](https://github.com/dickinsonre/hydra/commit/b6c7d4975ef607b4dcccdee238072082d45d5346))
* **common,wds,uds:** report what a run warned about ([408d1c9](https://github.com/dickinsonre/hydra/commit/408d1c9cb65013bf435fa67a6567eb026c802804))
* enable drainage threading in the official binaries ([d85629d](https://github.com/dickinsonre/hydra/commit/d85629dd98e1ec66eb945b29d783074dbfd40397))
* **uds,cli:** finish the checkpoint and give it a way in ([59a41ff](https://github.com/dickinsonre/hydra/commit/59a41ffc39a2768076fbeb12b49da24db7a3b16e))
* **uds,cli:** read an archival rain record wherever a station record is read ([e8075e2](https://github.com/dickinsonre/hydra/commit/e8075e2fcaa9c805491dea5e84de943a1394da98))
* **uds:** read and write rainfall interface files ([6d999db](https://github.com/dickinsonre/hydra/commit/6d999dbcea49c7d69769892e976e2998b141359f))
* **uds:** read RDII interface files ([c51d6cb](https://github.com/dickinsonre/hydra/commit/c51d6cb5871c8c437ca1f3d0f0d7cdc6d0c886f6))
* **uds:** read the archival climate-record layouts ([00b0c0e](https://github.com/dickinsonre/hydra/commit/00b0c0e885f78b49eda7f5339d6a0f7518825427))
* **uds:** replay a runoff interface file in place of the surface ([61878d3](https://github.com/dickinsonre/hydra/commit/61878d3caccacafb91d6afa46dbb9e279391cc48))
* **uds:** two-dimensional overland flow ([#122](https://github.com/dickinsonre/hydra/issues/122)) ([1e27fa3](https://github.com/dickinsonre/hydra/commit/1e27fa3a06c271d02665df472959b86e4947f620))
* **uds:** write RDII interface files ([2ab39c5](https://github.com/dickinsonre/hydra/commit/2ab39c5d2efc0dddd2af2732cafd1f559757c786))
* **uds:** write runoff interface files ([2d07079](https://github.com/dickinsonre/hydra/commit/2d07079ca1b7c05c67e602893287c3bb5f83f66c))
* **uds:** write the per-unit report file a usage line declares ([e6380a7](https://github.com/dickinsonre/hydra/commit/e6380a7f2c720f0aec107403998c8c69d50dba4e))


### Bug Fixes

* **cli:** drop em dashes from --help, and name the crate it wraps ([a99cdda](https://github.com/dickinsonre/hydra/commit/a99cdda3151cdb8ce320582c8bbd8ecad7ada307))
* two defects introduced by today's own fixes ([e34cf1e](https://github.com/dickinsonre/hydra/commit/e34cf1ea702b8f809f6e7c96f9a09628c01386b8))


### Performance

* **cli:** give the auxiliary-file survey the four sections it reads ([c4d86df](https://github.com/dickinsonre/hydra/commit/c4d86df2da5d60d65dee7b441ad8818705a5919c))
* **cli:** stop copying the model and holding two parsed networks ([b876921](https://github.com/dickinsonre/hydra/commit/b876921285d4dd8ae748bef4f3365d473403f40c))
* **uds:** keep bulk sections as text and drop the model after open ([0fa7039](https://github.com/dickinsonre/hydra/commit/0fa7039ec53da1601cdc0e118426fcb8a1910993))
* **uds:** keep the reporting instants only for a run that may checkpoint ([eb9e6c7](https://github.com/dickinsonre/hydra/commit/eb9e6c728597c03eeab6157f9c4077ab383eeec4))
* **uds:** let a run without a results sink forgo checkpoint retention ([1a79042](https://github.com/dickinsonre/hydra/commit/1a79042216bda2b2bc7a7446620c29af0dfd4627))
* **wds:** hold one instant, not the whole run ([8ad3077](https://github.com/dickinsonre/hydra/commit/8ad3077a4a51a32c0611db4c5717385aea72753b))


### Internal

* format-blind engines behind per-dialect interop crates ([#126](https://github.com/dickinsonre/hydra/issues/126)) ([f678d41](https://github.com/dickinsonre/hydra/commit/f678d41092d5bed041f327dd356623b41cc09f48))
