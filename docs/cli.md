---
title: "Camera QA reference buffer generator"
description: "CLI reference (public / user-facing options)"
permalink: /cli/
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

<div class="table-scroll">
<table class="cli-table">
  <colgroup>
    <col style="width:220px;">
    <col style="width:90px;">
    <col style="width:380px;">
    <col style="width:140px;">
    <col>
  </colgroup>
  <thead>
    <tr>
      <th>Option</th>
      <th class="col-required">Required</th>
      <th>Type</th>
      <th>Default</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
    <tr><td class="col-option"><code>--help</code></td><td class="col-required">no</td><td class="col-type"><code></code></td><td class="col-default"><code></code></td><td class="col-desc">Print this help message and exit</td></tr>
    <tr><td class="col-option"><code>--Width</code></td><td class="col-required">yes</td><td class="col-type"><code>UINT:POSITIVE</code></td><td class="col-default"><code></code></td><td class="col-desc">Image width in pixels</td></tr>
    <tr><td class="col-option"><code>--Height</code></td><td class="col-required">yes</td><td class="col-type"><code>UINT:POSITIVE</code></td><td class="col-default"><code></code></td><td class="col-desc">Image height in pixels</td></tr>
    <tr><td class="col-option"><code>--PixelFormat</code></td><td class="col-required">yes</td><td class="col-type"><code>TEXT:{Mono8,Mono10,Mono12,Mono14,Mono16,BayerGR8,BayerGR10,BayerGR12,BayerGR14,BayerRG8,BayerRG10,BayerRG12,BayerRG14,BayerGB8,BayerGB10,BayerGB12,BayerGB14,BayerBG8,BayerBG10,BayerBG12,BayerBG14,BayerGR16,BayerRG16,BayerGB16,BayerBG16}</code></td><td class="col-default"><code></code></td><td class="col-desc">PixelFormat: Mono8/Mono10/Mono12/Mono14/Mono16, Bayer{GR,RG,GB,BG}{8,10,12,14,16}</td></tr>
    <tr><td class="col-option"><code>--TestPattern</code></td><td class="col-required">yes</td><td class="col-type"><code>TEXT</code></td><td class="col-default"><code></code></td><td class="col-desc">TestPattern: Off|GrayHorizontalRamp|GrayVerticalRamp|GrayDiagonalRamp|GrayDiagonalIntervalRamp|UserTestPattern or numeric code (e.g. 0x202)</td></tr>
    <tr><td class="col-option"><code>--TestPatternInterval</code></td><td class="col-required">no</td><td class="col-type"><code>UINT</code></td><td class="col-default"><code>0</code></td><td class="col-desc">Interval for GrayDiagonalIntervalRamp (required only for that pattern)</td></tr>
    <tr><td class="col-option"><code>--TestPatternValueMin</code></td><td class="col-required">no</td><td class="col-type"><code>UINT:UINT in [0 - 4294967295]</code></td><td class="col-default"><code>0</code></td><td class="col-desc">Test pattern value minimum (applied as: value = min + base * step)</td></tr>
    <tr><td class="col-option"><code>--TestPatternValueMax</code></td><td class="col-required">no</td><td class="col-type"><code>INT:INT in [-1 - 4294967295]</code></td><td class="col-default"><code>4095</code></td><td class="col-desc">Test pattern value maximum. Use -1 to auto-calculate from --PixelFormat bit depth</td></tr>
    <tr><td class="col-option"><code>--TestPatternValueStep</code></td><td class="col-required">no</td><td class="col-type"><code>UINT:UINT in [1 - 4294967295]</code></td><td class="col-default"><code>1</code></td><td class="col-desc">Test pattern value step (applied as: value = min + base * step)</td></tr>
    <tr><td class="col-option"><code>--BinningHorizontal</code></td><td class="col-required">no</td><td class="col-type"><code>UINT:UINT in [1 - 2]</code></td><td class="col-default"><code>1</code></td><td class="col-desc">GenICam: BinningHorizontal (1 or 2)</td></tr>
    <tr><td class="col-option"><code>--BinningVertical</code></td><td class="col-required">no</td><td class="col-type"><code>UINT:UINT in [1 - 2]</code></td><td class="col-default"><code>1</code></td><td class="col-desc">GenICam: BinningVertical (1 or 2)</td></tr>
    <tr><td class="col-option"><code>--BinningMode</code></td><td class="col-required">no</td><td class="col-type"><code>TEXT:{average,sum}</code></td><td class="col-default"><code>average</code></td><td class="col-desc">GenICam: BinningMode (average or sum)</td></tr>
    <tr><td class="col-option"><code>--BlackLevelSelector</code></td><td class="col-required">no</td><td class="col-type"><code>TEXT:{All,Red,Green,Blue}</code></td><td class="col-default"><code></code></td><td class="col-desc">Select channel for the next --BlackLevel (All|Red|Green|Blue)</td></tr>
    <tr><td class="col-option"><code>--BlackLevel</code></td><td class="col-required">no</td><td class="col-type"><code>UINT:INT in [0 - 65535]</code></td><td class="col-default"><code></code></td><td class="col-desc">Set black level for the channel selected by the immediately preceding --BlackLevelSelector</td></tr>
    <tr><td class="col-option"><code>--output</code></td><td class="col-required">yes</td><td class="col-type"><code>TEXT</code></td><td class="col-default"><code></code></td><td class="col-desc">Output RAW file (unpacked by default)</td></tr>
    <tr><td class="col-option"><code>--version</code></td><td class="col-required">no</td><td class="col-type"><code></code></td><td class="col-default"><code></code></td><td class="col-desc">Display program version information and exit</td></tr>
    <tr><td class="col-option"><code>--print-cli-json</code></td><td class="col-required">no</td><td class="col-type"><code></code></td><td class="col-default"><code></code></td><td class="col-desc">Print CLI schema as JSON and exit</td></tr>
  </tbody>
</table>
</div>

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
