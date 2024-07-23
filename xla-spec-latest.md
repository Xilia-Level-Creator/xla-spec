*xla-spec-v0.0.1*

# Definitions

The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD",
"SHOULD NOT", "RECOMMENDED", "NOT RECOMMENDED", "MAY", and "OPTIONAL" in this
document are to be interpreted as described in BCP 14 [@!RFC2119] [@!RFC8174]
when, and only when, they appear in all capitals, as shown here.

- `XLA`: refers to a file format, which this spec describes.
- `archive`: refers to all the files, that are packed into XLA format

# Structure

XLA is a complex file format.
Any assets are stored alongside data, for which XML format is used.
A tarball is created from those, to pack everything into one file.

The general structure of files inside the tarball is as follows:

```
.
└── <level>.xla/
    ├── plugins/
    │   ├── <plugin1>.lua
    │   ├── <plugin2>.lua
    │   └── <plugin3>.lua
    ├── mesh.xml
    ├── entity.xml
    ├── level.xml
    ├── manifest.xml
    └── .xilia
```

Please refer to the rest of sections in this document for additional info
on each one of the elements of this file structure.

# Metadata file (`.xilia`)

In the root of the level, `.xilia` file MUST be present.
That file contains the version of this spec, which is used for that
particular archive. The format is as following:

```
v0.0.1-u
```

Include 6 or more characters. Start the version in `.xilia` file with
the character `v`, then the version itself (semantic versioning v2 is used).

This will give you file contents like `v0.0.1`. If you want to add any flags,
include a hyphen after the version number, and list the flags together, one
letter for each.

The given above example, `v0.0.1-u`, indicates using the version `0.0.1` for
the project, and also includes `u` flag.

## Version flags

Following are the flags, that you can use to modify spec version:
 - `u`: Unicode characters may be used in parts of the archive

It is RECOMMENDED to list the flags in the same order, as they appear in
this list.

If the flag can be applied to the archive, you MUST include it.
