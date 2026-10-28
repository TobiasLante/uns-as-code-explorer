# Changelog

## 0.2.0 — beta (2026-10-28)
- A window shows what changed after an update; tick "Don't show this again" and it stays closed until the next version.
- A cleaner light design in blue and orange; the start page shows just the three steps and where you stand.
- Kafka values in Avro: give the schema registry in the connect form.
- Several broker connections can be saved by name and picked again.
- A note when a newer version is available (can be switched off).
- A banner when the model is newer than this Explorer can read, instead of reading it wrong.
- Linux also as a .tar.gz that runs without FUSE and without root.
- A model folder is read at its own branch, with local commits.
- Windows: a setup that installs for your user only — no admin rights, the usual steps (welcome, folder, install, finish); the zip stays.
- NATS: a big hub no longer cuts the Explorer off (the history is read on its own connection); a lost connection comes back by itself, and the status bar says so in the meantime.

## 0.1.4 — beta (2026-10-27)
- The first start opens the public UNS-as-Code model on GitHub (osf-schemas, branch next, werk1): browse it without a broker.
- The Windows program carries the Explorer's logo (it showed the Electron logo before).
- One download link per system that always gives the newest version.

## 0.1.3 — beta (2026-10-27)
- New logo in the app (the topic tree with its circles), same as the program icon.
- First public release (Windows zip, Linux AppImage).

## 0.1.2 — beta
- A saved creds/CA file that is gone is taken from a defaults file next to the app.

## 0.1.1 — beta
- Two-column areas can be resized by mouse (double click: default), remembered per viewer; the head shows the version.

## 0.1.0 — beta
- Topics, Model Explorer, Follow (work order, decision) and Gaps over NATS, MQTT and Kafka; model semantics from a UNS-as-Code git.
