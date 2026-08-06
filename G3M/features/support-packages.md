# Support Packages

Open **Windows > Support Packager** to create a ZIP archive for a bug report.
G3M writes the archive to the path you choose. It does not upload the archive.

## Default package

G3M includes each available category by default. The log range stays available
outside the custom settings panel. Choose all logs, the last 24 hours, the last
7 days, or the last 30 days.

The package can contain:

- G3M version, selected game, chapter, profile, and current operation state
- operating system, architecture, Python runtime, memory, processes, and network counters
- CPU, disk, network, and G3M UI performance samples
- sanitized settings, installed-mod metadata, and the G3M data-folder tree
- logs and selected JSON, Markdown, or text files from the G3M data folder
- `g3mpatch.json` manifests extracted from installed `.g3mpatch` files
- recursive game-folder, Frickbears3 `addons`, and Pizza Tower `towers` trees
- each installed mod's config, recursive tree, or complete files

## Custom package settings

Enable **Custom package settings** to choose individual entries. Categories and
checkboxes remain visible while the setting is off, but G3M disables them until
you enable custom selection. Expand a category to inspect its entries.

Each mod has separate controls for `mod_config.json`, its file tree, and its
files. Including all mod files can make the archive large and may include content
that a mod author does not want redistributed. Check the archive before sharing
it.

## Privacy and file handling

G3M replaces the current account, home-folder, and computer names in collected
text. It redacts values whose keys look like tokens, passwords, cookies, API
keys, authorization data, or sessions. Process records exclude command lines.

The collector skips symbolic links while walking folders. It writes to a
temporary ZIP beside the selected destination and replaces the destination only
after collection succeeds. Cancellation or failure removes the temporary file.

Redaction cannot classify every private value. Open the ZIP and review its
contents before sending it to another person.
