# SpeakCAD Slicer

Slice an STL or 3MF for your 3D printer from a conversation with Claude. Claude looks your printer up in the SpeakCAD online slicer's catalogue (380+ printers from 60+ brands: Bambu Lab, Prusa, Creality, Elegoo, Anycubic, Sovol, Qidi, Flashforge, Voron and more, with their OrcaSlicer profiles), agrees the print settings with you, and gives you a link that opens the online slicer with the printer, nozzle, layer height, material, infill, supports, walls, adhesion, speed and orientation already selected. You drop the file on that page and download the G-code, or a sliced .gcode.3mf for Bambu Lab printers, with the print time, the filament weight and the layer count.

## Use it

Ask for what you need with your printer's name: "slice this bracket for my Bambu Lab A1 in PETG, 0.2 mm layers, 30% infill", "which layer heights does my Ender-3 V3 SE profile allow?", or "prepare a slice for a Prusa MK4S, PLA, no supports". Claude calls the connector's `find_printer` tool for the profile facts and `prepare_slice` for the link, and tells you what is selected. Open the link, drop your STL or 3MF (up to 50 MB), check it in 3D, press **Slice and download**.

Slicing uses SpeakCAD credits: it is included in the Pro and Unlimited plans and spends 5 credits per slice otherwise; re-slicing the same file with other settings within 10 minutes costs nothing. An account is needed on the page, and signing up asks for no card. The full guide is at https://speakcad.com/guides/slice-from-chatgpt-or-claude.

## What the plugin contains

- `.mcp.json`: the SpeakCAD Slicer connector, a remote MCP server at `https://speakcad.com/api/mcp/slicer` (no authentication).
- `skills/slice-for-your-printer/SKILL.md`: when and how Claude uses the two tools.

## Data

The connector receives only what Claude sends its tools: a printer name and print settings. It reads SpeakCAD's public printer catalogue and returns links; it never receives your file, your conversation or your Claude account. SpeakCAD counts tool calls per day and per assistant product and stores none of the content. Your model file is uploaded by you, on the SpeakCAD page, from your browser straight to the slicer service, where it is sliced in a temporary folder and not kept. Privacy policy: https://speakcad.com/privacy. Support: hello@speakcad.com.

## Licence

MIT (see LICENSE). SpeakCAD, the online slicer and its catalogue are separate services with their own terms: https://speakcad.com/terms.
