# Orange Storm Giga 4 Extruder Mod Profiles for Orca Slicer

Community-made Orca Slicer profiles for the **Elegoo OrangeStorm Giga fitted with the 4 Extruder mod**.

These files exist to fill a gap: **Elegoo sells the 4 Extruder mod, but owners still end up needing to build their own slicer setup**. In practical terms, that means users are left without an official ready-to-import printer profile pack for Orca Slicer, and setup support for this specific workflow is minimal. This repo is meant to give OrangeStorm Giga 4E users a practical starting point instead of forcing them to start from scratch.

These profiles are **not an official Elegoo release**. They are working baseline profiles intended to help you get the machine printing, then tune from there for your own hardware, materials, cooling, and quality targets.

## What this repository includes

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

1. Import only the nozzle size you actually have installed first.
2. Import the process profiles for that same nozzle size.
3. Import the filament profiles you actually plan to use.
4. Open the printer profile and review the machine start G-code.
5. Confirm nozzle diameter, first layer height, and temperatures.
6. Run a small first-layer test.
7. Run a simple calibration cube or rectangle.
8. Only then move on to larger parts.

## How to import these into Orca Slicer

### Option A: Import from the Orca Slicer menu

1. Download or clone this repository.
2. Open **Orca Slicer**.
3. Go to **File -> Import -> Import Configs** (or the equivalent import-config menu in your Orca Slicer version).
4. Browse to this repo.
5. Import the files you want to use.

Recommended import order:

1. **Printer profile** for your nozzle size
2. **Process profiles** that match that nozzle size
3. **Filament profiles** for the materials you use

After import:

- select the imported OrangeStorm Giga 4E printer profile
- select a matching Fine / Standard / Draft process profile
- select PLA, PETG, or ABS as needed
- review the machine and filament settings before slicing

### Option B: Import everything in one session

You can also select multiple JSON files during the import step and bring them in together. If Orca Slicer does not immediately show all imported presets, restart Orca Slicer and check the preset dropdowns again.

## Which files should you import?

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

- make sure you imported the JSON files, not the folders alone
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

## Final note

Because the OrangeStorm Giga 4 Extruder mod is sold without a complete, polished official printer-profile-and-support path for Orca Slicer users, this repository is intended to save you from doing every bit of setup from zero. Use it as a foundation, validate everything on your own machine, and tune from there.
