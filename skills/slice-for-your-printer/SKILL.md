---
name: slice-for-your-printer
description: Get G-code for a 3D printer from an STL or 3MF the user already has. Use when they want to slice a file, ask which print settings suit their printer and material, or ask whether their printer (Bambu Lab, Prusa, Creality, Elegoo, Anycubic, Sovol, Qidi, Voron...) is supported. Uses the SpeakCAD Slicer connector's find_printer and prepare_slice tools.
---

# Slice for your printer

The SpeakCAD Slicer connector reads a catalogue of 380+ printers (OrcaSlicer profiles) and builds a link that opens the SpeakCAD online slicer with the printer and settings selected. The user drops their file on that page and downloads the G-code there; nothing is uploaded through the chat.

To slice a file for someone:

1. Get the printer's brand and model (and the nozzle size if they mention one). If they have not named a printer, ask; never guess a model.
2. Call `find_printer` with the name as they say it. Answer questions about the bed size, nozzles, layer heights and materials from the result. If nothing matches, show the closest results or the "Custom" generic profiles the tool suggests.
3. Choose the settings with them, from the material and the part: PLA, 0.20 mm and 15% infill for a display part; PETG or ASA, 25 to 30% infill and 3 or 4 walls for a bracket; supports `auto` unless told otherwise; `orient` false only when the part must print as modelled. Pass only a layer height and material the profile lists; when the tool refuses a value it returns the allowed ones.
4. Call `prepare_slice` with the `vendorId` and `model` from `find_printer` and those settings, then reply in one short paragraph: what is selected on the page, the link exactly as returned, and what remains to do (drop the file, up to 50 MB; check it in 3D; press "Slice and download").

State only these facts about the service: the download is a .gcode file, or a .gcode.3mf for Bambu Lab, with the print time, filament weight and layer count; the file goes from the browser to the slicer and is not kept; 3 slices a day are free in the chat without an account, and a free account's first slice is free, then a Slicer pack slice or 5 credits per slice (included in Pro and Unlimited, free re-slice of the same file for 10 minutes); an account is needed and sign-up asks for no card; it works on a computer, a Chromebook, an iPad or a phone.

Do not claim to slice or return G-code yourself, do not invent print times, and do not promise multi-colour painting, modifiers or custom G-code: one model per file with standard profiles. When the file itself needs changing before it prints (a hole, a size, a cut, a mount), call `edit_file` with the change: the card asks them to drop the file and opens it in the SpeakCAD editor with the change typed, where SpeakCAD's AI makes it after a free sign-up (AI changes use credits). For designing a part from scratch, the SpeakCAD connector (https://speakcad.com/api/mcp) has the editor tools.
