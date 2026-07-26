# KiCad Library — Matys Labbee

Personal, version-controlled component library for KiCad 10.

## Layout

```text
.
├── symbols/           KiCad symbol libraries, grouped by function
├── footprints/        `.pretty` footprint libraries, grouped by package/use
├── 3dmodels/          STEP/WRL models mirroring footprint library names
├── simulation/        SPICE and other simulation models
├── documentation/     Datasheets, source links, and component images
├── sym-lib-table      Project symbol-library table
└── fp-lib-table       Project footprint-library table
```

### Symbol libraries

- `Analog` — amplifiers, converters, references, and analog ICs
- `Connectors` — connectors, sockets, headers, and cable assemblies
- `Digital` — logic, memory, processors, and digital ICs
- `Electromechanical` — relays, switches, motors, and actuators
- `Modules` — complete modules and development boards
- `Power` — regulators, converters, protection, batteries, and power ICs
- `Sensors` — environmental, motion, optical, and other sensors
- `Misc` — truly uncategorized custom parts

### Footprint and 3D-model libraries

Footprints are grouped by physical package or use. Keep a matching model in
`3dmodels/<Library>.3dshapes/` whenever one is available.

## Use in a KiCad project

The included library tables use `${KIPRJMOD}`, so the simplest setup is:

1. Clone this repository next to or inside the KiCad project.
2. Copy or merge the entries from `sym-lib-table` and `fp-lib-table` into the
   project's library tables.
3. If the repository is not the project directory, replace `${KIPRJMOD}` with
   the repository's absolute path or a custom KiCad path variable.

For a global installation, open **Preferences → Manage Symbol Libraries** and
**Preferences → Manage Footprint Libraries**, then add the desired files and
`.pretty` directories.

## Adding a component

1. Put the symbol in the functional library that best describes the part.
2. Put the footprint in the matching physical-package library.
3. Name custom items with the manufacturer part number when possible.
4. Set the symbol's `Datasheet`, `Description`, and footprint fields.
5. Save 3D models as `.step` (preferred) and optionally `.wrl`.
6. Add source/license notes for third-party assets in
   `documentation/SOURCES.md`.
7. Open the edited libraries in KiCad 10 to confirm they parse before
   committing. Symbol files can also be checked with `kicad-cli sym upgrade`
   using a temporary output path.

## Naming conventions

- Symbols: `Manufacturer_MPN` when ambiguity is likely; otherwise the MPN.
- Footprints: follow KiCad's official naming style where practical.
- 3D models: match the footprint name exactly.
- Avoid spaces in library and asset filenames.
- Use millimetres and the standard KiCad coordinate conventions.

## Version control

Commit source library files and distributable models. Do not commit KiCad
autosaves, backups, caches, or operating-system metadata; `.gitignore` covers
the common cases.
