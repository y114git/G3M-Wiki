# Launch Diagnostics

Open **Diagnostics** from the Library when you need to check a mod setup before
launching it.

## Quick inspection

The dialog can inspect installed files without running the patcher. Use this
view to check mod contents, patch formats, extra-file destinations and obvious
conflicts.

## Analyze Launch

**Analyze Launch** performs the same ordered patching work as a normal launch
against a temporary copy of the game files. It does not start the game or
replace files in the configured game folder.

The report includes:

- every priority step and the mods assigned to it
- changed DATA resources and extra files
- the winning mod when several mods target the same file
- hashes and source paths used during the analysis
- G3MTool, xdelta and script warnings or errors
- incomplete scans and permission failures

This is the most accurate check available before launch because `.xdelta`,
`.csx` and raw DATA inputs must run before G3M can know their final changes.

## Exporting a report

Export as JSON when another tool needs to read the result. Export as HTML when
you want a report that is easier to open or attach to a bug report.

An analysis result only describes the selected profile, game section, priority
order and files present at that time. Run it again after changing any of them.
