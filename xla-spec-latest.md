# XLA Specification v0.0.1


## Definitions

The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD",
"SHOULD NOT", "RECOMMENDED", "NOT RECOMMENDED", "MAY", and "OPTIONAL" in this
document are to be interpreted as described in BCP 14 [@!RFC2119] [@!RFC8174]
when, and only when, they appear in all capitals, as shown here.

- `Archive`: refers to all the files, that are packed into `XLA` format
- `Compiler`: refers to a program, which reads (parses) `XLA` format files
- `Level code`: refers to raw level code, as per
  [PewPew API documentation](https://pewpewlive.github.io/ppl-docs/)
- `Manifest`: refers to `manifest.xml` file in the root of the `Archive`
- `XLA`: refers to a file format, which this spec describes.


## Structure

`XLA` is a complex file format.
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

### Note on XML format

It is RECOMMENDED to specify XML version in `.xml` files, like so:

```xml
<?xml version="1.0"?>
```

This might be used by the `Compiler` to correctly parse the files.

Also note that the spec makes heavy use of XML namespaces, they must be a valid
[IRI](https://en.wikipedia.org/wiki/Internationalized_Resource_Identifier).


## Metadata file (`.xilia`)

In the root of the level, `.xilia` file MUST be present.
That file contains the version of this spec, which is used for that
particular `Archive`. The format is as following:

```
v0.0.1-ud
```

Include 6 or more characters. Start the version in `.xilia` file with
the character `v`, then the version itself (semantic versioning v2 is used).

This will give you file contents like `v0.0.1`. If you want to add any flags,
include a hyphen after the version number, and list the flags together, one
letter for each.

The given above example, `v0.0.1-ud`, indicates using the version `0.0.1` for
the project, and also includes both `u` and `d` flags.

### Version flags

Following are the flags, that you can use to modify spec version:
 - `u`: Unicode characters may be used in parts of the `Archive`
 - `d`: A "loose" variation of a spec. In this version, many values
   can be left undefined (it is up to `Compiler` to set defaults).

It is RECOMMENDED to list the flags in the same order, as they appear in
this list.

If the flag can be applied to the `Archive`, you MUST include it.


## Level manifest (`manifest.xml`)

Following is the example of how `manifest.xml` file might look like:

```xml
<?xml version="1.0"?>

<manifest xmlns="xilia://manifest">

  <xilia/>

  <level>

    <name>Eskiv</name>
    <descriptions>
      <description>Red definitely good.</description>
    </descriptions>
    <information/>

    <rank-thresholds>
      <rank-thresholds-1p>
        <bronze>2500</bronze>
        <silver>3500</silver>
        <gold>4500</gold>
      </rank-thresholds-1p>
      <rank-thresholds-2p/>
    </rank-thresholds>

  </level>

</manifest>
```

Refer to `Structure` section, `Note on XML format` subsection for additional
info on XML standard used.

You MUST include `manifest` tag of `xilia://manifest` namespace in the
`Manifest`. There SHOULD NOT be any other tags in the `Manifest`, except
for `manifest` and `xml`.

Note that all the described in the spec elements MUST inherit the namespace
of `xilia://manifest` from the `manifest` tag.

`manifest` tag MUST include `xilia` and `level` tags, and SHOULD NOT
include any other tags. In current spec version the `xilia` tag is unused,
so you MAY leave it empty.

### Basic level info (`level` tag)

The `level` tag contains some basic information about the level, and closely
resembles `manifest.json` file, as per
[official PewPew API docs](https://pewpewlive.github.io/ppl-docs/docs/File%20Information/manifest-files)

Please refer to the given above documentation for the meaning of each field.
Following is the mapping between XML in `level` tag, and fields in
`manifest.json` of the `Level code`:
 - `name`: level name (string), maps to `name` in `manifest.json`.
 - `descriptions`: MUST contain one or more `description` tags. SHOULD NOT
   contain any other tags. Each `description` tag is a string.
   Maps to `descriptions` array in `manifest.json`
 - `information`: level information (string), maps to `information` in
   `manifest.json`.
 - `entry-point`: path to the main entry point file. This is ultimately
   decided by `Compiler`, and including this field is OPTIONAL. If the
   `entry-point` field is present, it MAY be used by `Compiler`.
 - `rank-thresholds`: MUST contain one and only one `rank-thresholds-1p`
   tag, as well as one and only one `rank-thresholds-2p` tag. In current
   spec both tags MAY be empty. `rank-thresholds-2p` SHOULD be ignored by
   `Compiler`, while empty `rank-thresholds-1p` tag maps to value `false`
   of `has_score_leaderboard` tag in `manifest.json`. If `rank-thresholds-1p`
   is not empty, it MUST contain `bronze`, `silver` and `gold` tags (all
   are integers), which map to `rank_thresholds_1p` in `manifest.json`

Unless stated otherwise, all the mentioned tags MUST NOT be empty in standard
spec version. If the spec version used includes `d` flag (see `Metadata file`
section, `Version flags` subsection), fields with no required children
MAY be empty.

Note that `PewPew API` imposes lenght limits on some of the fields. Those
are not imposed by this spec, instead it is left up to the `Compiler`.
