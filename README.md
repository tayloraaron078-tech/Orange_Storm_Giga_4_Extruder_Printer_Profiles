# Orange Storm Giga 4 Extruder Mod Profiles for Orca Slicer

Community-made Orca Slicer profiles for the **Elegoo OrangeStorm Giga fitted with the 4 Extruder mod**.

These files exist to fill a gap: **Elegoo sells the 4 Extruder mod, but owners still end up needing to build their own slicer setup**. In practical terms, that means users are left without an official ready-to-import printer profile pack for Orca Slicer, and setup support for this specific workflow is minimal. This repo is meant to give OrangeStorm Giga 4E users a practical starting point instead of forcing them to start from scratch.

## Use at your own risk

**Importing or printing with anything in this repository is entirely at your own risk.** These are **not** official Elegoo profiles, and neither the author of this repo nor Elegoo is responsible for failed prints, crashes, bad offsets, heater issues, damaged parts, lost time, or wasted material. Always verify the setup on your own machine before trusting it with a long print.

## What is in this repo?

This repo is meant to help two kinds of users:

1. **Beginners / quick-start users** who want the easiest path and do **not** want to review every profile file first.
2. **Manual / advanced users** who prefer importing individual printer, process, and filament profiles separately and reviewing each part of the setup.

### Quick and easy option: complete bundles

If you downloaded one of the **complete exported bundles** for your nozzle size, that is the easiest beginner path.

A complete bundle is intended to give you a mostly ready-to-go setup in one import so you do not have to manually sort through:

- printer profile files
- process profile files
- filament profile files

That makes the bundle option the best starting point for:

- beginners
- anyone setting up the printer fast
- anyone who wants to get into Orca Slicer quickly without reviewing every profile first

**Even with the complete bundles, you still use them at your own risk.** Before printing anything important, you should still confirm nozzle size, temperatures, first-layer behavior, bed heating, and tool behavior on your own machine.

### Manual option: individual profile files

If you prefer to build things up yourself, this repo also includes the individual profile files broken out into the normal Orca Slicer categories below.

## Individual profile contents

This repo is organized into three profile groups for Orca Slicer:

### 1. Printer Profiles
Located in `Printer Profiles/`.

Included nozzle variants:

- `Elegoo_OrangeStorm_Giga_4E_0_4nozzle_v7.json`
- `Elegoo_OrangeStorm_Giga_4E_0_6nozzle_v7.json`
- `Elegoo_OrangeStorm_Giga_4E_0_8nozzle_v7.json`
- `Elegoo_OrangeStorm_Giga_4E_1_0nozzle_v7.json`

These printer profiles provide the machine-level settings for the OrangeStorm Giga 4E setup, including:

- Klipper-flavored machine configuration.
- Start G-code, end G-code, filament change, and layer-change behavior.
- Preset nozzle-size-specific defaults for 0.4, 0.6, 0.8, and 1.0 mm nozzles.
- A printable area of `199 x 805 mm` as configured in these profiles.
- Default linkage to the matching process profile set for each nozzle size.
- Default linkage to the included Elegoo PLA filament profile.

### 2. Process Profiles
Located in `Process Profiles/`.

Each nozzle size has three baseline process profiles:

- **Fine**
- **Standard**
- **Draft**

That gives you **12 process profiles total**:

- 0.4 nozzle: 0.10 / 0.20 / 0.28 mm
- 0.6 nozzle: 0.15 / 0.30 / 0.42 mm
- 0.8 nozzle: 0.20 / 0.40 / 0.56 mm
- 1.0 nozzle: 0.25 / 0.50 / 0.70 mm

These process profiles are intentionally simple starter presets. Across the included files, they generally use:

- 15% sparse infill
- 3 wall loops
- 5 top layers
- 4 bottom layers
- tree support selected as the support style, but support itself disabled by default
- prime tower disabled by default
- outer wall speed of 100 mm/s
- inner wall speed of 150 mm/s
- sparse infill speed of 180 mm/s
- travel speed of 300 mm/s

### 3. Generic Filament Profiles
Located in `Generic Filament Profiles/`.

Included materials:

- `Elegoo_PLA_EOS_Giga.json`
- `Elegoo_PETG_EOS_Giga.json`
- `Elegoo_ABS_EOS_Giga.json`

These provide basic starting temperatures and fan behavior for common Elegoo materials:

- **PLA**: 225C first layer / 220C other layers, 65C first layer bed, fan 80-100%
- **PETG**: 240C first layer / 235C other layers, 80C first layer bed, fan 30-60%
- **ABS**: 250C first layer / 245C other layers, 105C first layer bed, fan 0-30%

## What these profiles accomplish

If you have the OrangeStorm Giga 4 Extruder hardware and do **not** want to start from a blank Orca Slicer setup, these files give you:

- A ready-made machine definition for the modified printer.
- Matching nozzle-specific print presets so layer heights already make sense for the nozzle you choose.
- Basic filament presets so you can start slicing with PLA, PETG, or ABS without entering temperatures from scratch.
- Startup and shutdown G-code already inserted so the printer can be tested immediately after import.
- A practical baseline that can save a lot of trial-and-error for anyone who bought the mod and then discovered there was no complete profile package waiting for them.

In short, this repo is best thought of as a **working starting point**, not a finished, universal, perfectly tuned profile set.

## Beginner quick start

If you want the fastest possible path and do not want to inspect every profile first:

1. Pick the **complete bundle** that matches your nozzle size.
2. Import that bundle into Orca Slicer.
3. Select the imported printer and preset set.
4. Confirm your nozzle size, filament temperatures, and first-layer settings.
5. Run a very small test print first.
6. Stay with the printer while it starts.

This is the easiest route, but it is **not** the safest route unless you still do the basic sanity checks above.

## Important things to know before you print

Please read this section before trusting any slicer preset on a large-format modified printer.

### These are baseline community profiles

You should expect to tune:

- flow / extrusion multiplier
- pressure advance / linear advance behavior
- retraction
- first-layer Z offset
- temperatures for your exact filament brand and color
- speeds and accelerations based on your machine condition
- cooling and support settings for your part geometry

### Multi-extruder owners should still verify tool behavior carefully

The machine files are labeled for the **4 Extruder** OrangeStorm Giga setup, but you should still manually confirm your own:

- nozzle assignment
- active tool behavior
- bed zone behavior
- offsets / alignment
- purge and prime expectations
- tool-change workflow

Do your first tests with a simple single-material print and stay with the machine.

### Bed heating behavior is customized

The included start and layer-change G-code keeps all four bed zones addressed during early printing. If your machine firmware, wiring, or bed-zone configuration differs, review that G-code before using it.

### Support and prime tower are disabled by default

The process profiles keep things simple. If your model needs supports, wipe structures, or other multi-material helpers, enable and tune them yourself.

### Filament presets are generic starting points

The included PLA, PETG, and ABS presets are not meant to replace proper material tuning. Dry filament, enclosure behavior, ambient temperature, and spool brand can all change the correct settings.

## Recommended first-run checklist

Before attempting a long or expensive print:

1. If you want the simplest path, start with the complete bundle for your nozzle size.
2. If you prefer manual control, import only the nozzle size you actually have installed.
3. Import the matching process profiles and the filament profiles you actually plan to use.
4. Open the printer profile and review the machine start G-code.
5. Confirm nozzle diameter, first layer height, and temperatures.
6. Run a small first-layer test.
7. Run a simple calibration cube or rectangle.
8. Only then move on to larger parts.

## How to import these into Orca Slicer

### Option A: Import a complete bundle

This is the recommended path for beginners and anyone who wants the quickest setup.

1. Download or clone this repository.
2. Open **Orca Slicer**.
3. Go to **File -> Import -> Import Configs** (or the equivalent import-config menu in your Orca Slicer version).
4. Select the **complete bundle** for your nozzle size.
5. Import it.
6. Select the imported printer and presets.
7. Double-check the basic machine and material settings before slicing.

### Option B: Import the individual files manually

Use this if you want more control or want to review the setup file by file.

Recommended import order:

1. **Printer profile** for your nozzle size
2. **Process profiles** that match that nozzle size
3. **Filament profiles** for the materials you use

After import:

- select the imported OrangeStorm Giga 4E printer profile
- select a matching Fine / Standard / Draft process profile
- select PLA, PETG, or ABS as needed
- review the machine and filament settings before slicing

### Option C: Import multiple files in one session

You can also select multiple JSON files during the import step and bring them in together. If Orca Slicer does not immediately show all imported presets, restart Orca Slicer and check the preset dropdowns again.

## Which files should you import if you are doing it manually?

### If you run a 0.4 mm nozzle
Import:

- `Printer Profiles/Elegoo_OrangeStorm_Giga_4E_0_4nozzle_v7.json`
- all `Process Profiles/` files containing `0_4`
- any desired file from `Generic Filament Profiles/`

### If you run a 0.6 mm nozzle
Import:

- `Printer Profiles/Elegoo_OrangeStorm_Giga_4E_0_6nozzle_v7.json`
- all `Process Profiles/` files containing `0_6`
- any desired file from `Generic Filament Profiles/`

### If you run a 0.8 mm nozzle
Import:

- `Printer Profiles/Elegoo_OrangeStorm_Giga_4E_0_8nozzle_v7.json`
- all `Process Profiles/` files containing `0_8`
- any desired file from `Generic Filament Profiles/`

### If you run a 1.0 mm nozzle
Import:

- `Printer Profiles/Elegoo_OrangeStorm_Giga_4E_1_0nozzle_v7.json`
- all `Process Profiles/` files containing `1_0`
- any desired file from `Generic Filament Profiles/`

## Troubleshooting notes

If the profiles do not appear correctly after import:

- make sure you imported the actual bundle or JSON files, not just the folders
- make sure the nozzle-specific printer and process profiles match each other
- restart Orca Slicer after import
- re-import one file at a time if Orca Slicer rejects a batch import
- open the imported preset and confirm Orca did not remap or rename anything unexpectedly

If a print starts incorrectly, stop immediately and verify:

- nozzle diameter
- selected filament preset
- temperatures
- bed behavior
- first-layer height
- machine start G-code
- tool selection / tool behavior

## Final note

Because the OrangeStorm Giga 4 Extruder mod is sold without a complete, polished official printer-profile-and-support path for Orca Slicer users, this repository is intended to save you from doing every bit of setup from zero. Whether you use the quick-start bundles or the individual files, validate everything on your own machine first and remember that all use is at your own risk.
