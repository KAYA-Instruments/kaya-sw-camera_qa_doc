---
title: "kaya-sw-camera_qa_reference_buffer.exe reference"
---

This page documents only user-facing options (SFNC-like):

- Options that start with an uppercase letter after `--`
- Plus: `--output`, `--help`, `--version`, `--print-cli-json`

For the complete option list (including internal/dev placeholders), run:
`kaya-sw-camera_qa_reference_buffer.exe --help`

## Synopsis

```text
kaya-sw-camera_qa_reference_buffer.exe [OPTIONS]
```

## Options

| Option | Required | Type | Default | Description |
|---|:---:|---|---|---|
| `--Height` | yes | `UINT:POSITIVE` | `` | Image height in pixels |
| `--PixelFormat` | yes | `TEXT:{Mono8,Mono10,Mono12,Mono14,Mono16}` | `` | PixelFormat: Mono8/Mono10/Mono12/Mono14/Mono16 |
| `--TestPattern` | yes | `TEXT` | `` | TestPattern: Off\|GrayHorizontalRamp\|GrayVerticalRamp\|GrayDiagonalRamp\|GrayDiagonalIntervalRamp\|UserTestPattern or numeric code (e.g. 0x202) |
| `--Width` | yes | `UINT:POSITIVE` | `` | Image width in pixels |
| `--output` | yes | `TEXT` | `` | Output RAW file (unpacked by default) |
| `--BinningHorizontal` | no | `UINT:UINT in [1 - 2]` | `1` | GenICam: BinningHorizontal (1 or 2) |
| `--BinningMode` | no | `TEXT:{average,sum}` | `average` | GenICam: BinningMode (average or sum) |
| `--BinningVertical` | no | `UINT:UINT in [1 - 2]` | `1` | GenICam: BinningVertical (1 or 2) |
| `--TestPatternInterval` | no | `UINT` | `0` | Interval for GrayDiagonalIntervalRamp (required only for that pattern) |
| `--TestPatternValueMax` | no | `INT:INT in [-1 - 4294967295]` | `4095` | Test pattern value maximum. Use -1 to auto-calculate from --PixelFormat bit depth |
| `--TestPatternValueMin` | no | `UINT:UINT in [0 - 4294967295]` | `0` | Test pattern value minimum (applied as: value = min + base * step) |
| `--TestPatternValueStep` | no | `UINT:UINT in [1 - 4294967295]` | `1` | Test pattern value step (applied as: value = min + base * step) |
| `--help` | no | `` | `` | Print this help message and exit |
| `--print-cli-json` | no | `` | `` | Print CLI schema as JSON and exit |
| `--version` | no | `` | `` | Display program version information and exit |

## Output auto-naming (`@args@`)

`--output` supports a special value: `@args@`.

When `--output @args@` is used, the utility auto-generates an output filename based on the effective CLI arguments.
This feature is relied upon by the workflow even if it is not currently shown in `--help`.

Example:

```bat
kaya-sw-camera_qa_reference_buffer.exe ^
  --Width 640 --Height 640 ^
  --PixelFormat Mono10 ^
  --TestPattern GrayDiagonalRamp ^
  --output @args@
```

## CLI schema export (`--print-cli-json`)

`--print-cli-json` prints a JSON schema describing all options.

Note: output includes a `CMDLINE:` prefix line before the JSON object. Consumers should extract JSON by locating the first `{` and the last `}`.
