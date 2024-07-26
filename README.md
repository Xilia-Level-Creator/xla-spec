# Format spec for .xla files

`.xla` files are a middle step for implementing [PewPewLive level](https://github.com/pewpewlive/ppl-utils) builder.
GUI can be used to generate those files, which are later compiled into an actual level.

Refer to `xla-spec-latest.md` for more info on how the latest version of .xla files store the level data.

## ToDo list

- [x] Add `examples` with some levels, implemented via .xla
- [x] Develop and document `xla-builtin.md` doc, describing built-in presets/transforms/patches.
- [ ] Develop and document `lua-spec.md` doc (maybe different name?), describing custom presets/transforms/patches
- [ ] Consider some changes to `xla-spec-latest.md`
  - [ ] Support more color formats
  - [ ] Flipping meshes
  - [ ] Event system (+listeners)
  - [ ] Consider more values, affected by `d` version flag
  - [ ] Tarball support back
