# cadence_notes
Notes for cadence

## Cadence Layout flow

1. create -> layout XL/GXL to create layout files
2. split the layout into blocks
    - Current Mirror and Voltage Bias
    - Circuit with Differential Pair
    - note: use `net highlight` to trace signal path
3. check the **matching** config
    - body connection
        - cascode pairs
    - current mirror
    - symmetrical pairs
    - multiplier (multiple of 4 > even number > large odd number)
4. layout -> connectivity -> generate -> all from source -> untick I/O pins and PR boundary
5. set capacitors aside, draw transistor layout first


    For matching
    - check the common "shared" connections of the components we wish to share
    - put components as close as each other 
    - abutt the common parts (move close -> snap together)

6. add bulk and guard ring 
    - for pmos, cover `NW` on top of `NW` (for better guard ring selection)
    - guard ring, type as `NWellGuardring` net as `avdd`, enclosed by `0.3`
    - ? cover `PP` to the inner part of the N guard ring (for better anti-latchup)

    - for nmos, cover `NP` on top of `NP` -> `<Shift-G>`, set type as `PSubGuardring` set `Enclose by` as 0.17

7. create pin on finished nets
    - label: `height` = 0.2, `Font` = Roman, `layer name / purpose` Same As Pin

## tricks

- select -> property -> `routePolydir` to connect the gates together

- For vias, add at least 2 vias (more friendly to DRC)

- matching of 4-devices

        |A|B|B|A|
        |-|-|-|-|
        |B|A|A|B|

- For long devices (stack L), setup properties -> `leftCnt` / `rightCnt`

- for DUMMY
    - N dummy -> every nets to VSS
    - P dummy -> every nets to VDD

## common shortcuts
- `esc` or `<Ctrl-D>`: deselect all
- `v` only visible
- `s` only select
- `<Shift-G>` generate guard ring

- `F5` highlight DRC in Calibre; `F4` cancel highlight DRC 
- `N` change movement constraint (latitute, longtitute, orthogonal, free)

## DRC parameters
`M1` to `M1`: 0.09
