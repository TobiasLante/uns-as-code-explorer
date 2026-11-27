# Changelog

## 0.2.24 (2026-11-27)
- **Compare stays responsive while it prepares.** Collecting the systems' exports for a comparison no longer stalls the app: with a quarter of a million confirmations the longest pause was about a second, now under a tenth.
- **Answers in Compare read like a report.** Both sides begin with the short answer, name the system a fact comes from (ERP, QMS …) instead of files or scripts, and say in plain words what could not be found — never an error message.
- **The Model Explorer fits narrow windows.** At about 1000 px its head and tool row wrap instead of running past the window.
- **Updates are found.** The app checks every 6 hours whether a newer version is out, and a release candidate hears of the final version.
- The 8D example asks for the nonconformance reports the evaluation scores; an ID written short still counts.

## 0.2.23-rc5 — release candidate (2026-11-26)
- **Compare no longer weighs down the computer.** On the demo a comparison took up to 2.3 GB of memory and could stall the whole computer; now about 1.4 GB, and the app stays responsive while it prepares. The live view keeps only what the broker publishes (no longer what is sent to other users), each message holds only its own bytes, the records of a period go to disk while they are read, and large exports are written line by line.

## 0.2.23-rc4 — release candidate (2026-11-26)
- **The setup has the demo too.** The Windows setup now starts like the zip: one click on Activate for the demo plant, no login until 31 December 2026, the e-mail optional.
- **The e-mail field is always there** — also when this computer was activated before.
- **A broker without a model says so plainly**: what it needs (UNS-as-Code 0.8.1 or newer) and what works instead (the demo, or your own model folder or git).

## 0.2.23-rc3 — release candidate (2026-11-26)
- **The model comes over the broker.** The Explorer reads the plant model from UNS-as-Code over the broker it is connected to (UNSaC 0.8.1) — no git, no GitHub access. A model saved by an earlier version opens the same way.
- **Figures over a period come whole.** A period query asks UNS-as-Code for its longest scan; two days of confirmations come complete, where they stopped after 20 seconds before.
- **A side that ends early says why** — also when Claude Code was ended from outside; its answer is called cut.
- The historian export of a machine that stands now runs to now.

## 0.2.23 — beta (2026-11-24)
- **Compare, said openly: "Claude for Manufacturing (Export)" against "Claude for Manufacturing + UNS-as-Code".** The same plugin, model and question on both sides; only the way the data reaches Claude differs. The left side gets the data as Claude for Manufacturing reads it today (Anthropic's plugin: the ERP through its connector, queried by the number in the question; the shop-floor systems — MES, QMS, WMS, historian — as an export of the case's period); Claude searches and joins them itself, nothing is pre-searched and nothing comes from the plant model. The right side asks the UNS-as-Code context layer: an ISA-95 work record of everything tied to the order, lot or machine, each tie with the relation that proves it, gaps said as gaps. Under each answer: what that side was given.
- **An evaluation below both answers.** The core facts of the case come from the work record by a fixed rule — the machine that actually ran (by any of its names), the number of lots and inspection lots with their decisions, good and scrap, and the case's nonconformance reports (NCR) — and each answer is checked for them (✓/✗), plus the IDs it names that exist nowhere. An ID written short ("NCR-AUTO-…T1947") counts; a sentence that denies or only supposes an NCR does not. No AI grades.
- **Large orders.** An order with thousands of lots and hundreds of inspection lots is one work record of many pages: it is fetched once and kept for the run, not again for each question Claude asks. Each file the context side gets says that every row belongs to the case, of which ISA-95 type and by which path (an NCR through the inspection lot it records).
- **The morning report covers its period on both sides.** The confirmations are read over the period the work record sums (since yesterday 00:00 in the plant's zone), not only what the Explorer had loaded — to the end of the period: reading a period is bounded by its size, no longer by the one-minute limit of a newest-first read, which cut the night shift short on the export side. A period that still does not come whole is said in the preparation.
- **Several questions in a row.** A new question empties both sides and shows its preparation step by step (the second question showed the first one's answers while it prepared). A question once shown stays the question of its skill — newer data no longer swaps it between the pick and Run both. A period read for a comparison goes into its exports only and is freed afterwards: six questions in a row no longer run the app out of memory. Questions without fixed core facts (morning report, machine names) say so instead of showing an empty score. The Windows setup carries the skill again (it was dropped from the build on Windows). The head shows the release candidate.
- A side that ends early says why. The connection between Claude Code and the Explorer's tools no longer drops after a pause.
- **The activation comes first.** At the first start of a download with an activation, its window — with the optional e-mail for notices — is no longer covered by What's new.
- **A slim view.** One row: the question and Run both. After Run the preparation shows step by step with its time, then one line. Two equally wide sides, the answer at full height, one scrollbar. Present fills the screen (Esc ends it). There is no plant-context switch any more: the context is always on (Claude Desktop switches its extension itself).
- **The context layer first.** The Explorer's tool work_record answers with the record's head (counts per ISA-95 type, five keys each) and gives the entries per type a page at a time; Claude is told to ask it first for 8D, NCR, lot trace, breakdown, morning report and machine names. A planned machine is checked against its pool through the class tree; aliases recorded on a machine (core 6.6.0) resolve.
- **Complete instead of the newest 20 000.** Where the broker carries the UNS-as-Code pointer index, the Explorer reads everything that names an order, a machine or a record — through the index, all of it. Without an index it reads by time window (from the order's own start). Follow and the Model Explorer use the same. The status line shows the index.
- **Claude gets the model's own findings first**: devices that send but that the model does not know, machines that send nothing, programs without a recipe; whether a planned machine fits its routing; the machine's state, program and tool at the time a part was made.
- **With the plant context never less than without**: matches by value are given as lists, an order's confirmations are summed per machine with their reasons, a record's fields (such as a lot's creation time) come back, and the limits are the recipe and settings versions in force at the time.
- The 8D example is an order that ran and has a rejected part.

## 0.2.21 — beta (2026-11-19)
- **Compare: the same question, with and without the plant context.** MCP / Claude has three tabs: Compare, Readiness, Set-up. Compare asks one question twice; both sides use Anthropic's Claude for Manufacturing plugin — the left one on the systems' raw exports, as in a plant today, the right one with the UNS-as-Code plant context (the unsac-context skill and the Explorer's tools). Three ways: live side by side (two Claude Code sessions on this computer), or in Claude Desktop in two windows or one after the other. Six ready questions, one per Claude for Manufacturing skill, come from the loaded data; both sides answer in one frame — short answer, facts with source and how they are linked, what cannot be answered. Each side has a Copy button. Nothing is recorded.
- **The plugin computes.** With the plant context the morning pulse's engine reads the plant's output, orders, plan and machines (each machine by its model id) and computes its figures; the sessions may run only the plugin's own three scripts.
- **Readiness** checks Claude Code, Python (on Windows `py -3`, not the Store's placeholder), the MCP server, the model and the broker — each missing piece with its fix as a button. Refused or timed-out tool calls are counted in the head of each side, with the reason.
- **Claude's answers from the Explorer's tools come within time**: a question that needs records from the broker waits at most 25 s; what is still loading is named.
- **Demo access without registration.** A download with an activation gets its own key at the first start — a 2-hour session, renewed with one click; an e-mail only if you want notices (no sales). The key in use is shown in the status line. The Explorer itself stays free and open source (Apache-2.0).
- **A full demo broker is said in plain words**, at once, also on the first connect. The NATS connector runs on nats.js v3.
- Windows: the setup shows next to its progress bar which step runs. "What's new" opens on Windows too.
- A little winter decoration until 6 January.
## 0.2.19 — beta (2026-11-18)
- **MCP server for AI agents (read only).** `uns-explorer mcp` answers an agent (Claude, any MCP client) from the plant's UNS-as-Code model and its broker, nothing else: resolve a machine name from any system, an element and its place in the plant, the records joined to a machine, follow a record along the model's relations, the limits in force (recipe and machine settings with their owner and how binding each band is), check an ISA-95 edge, the history of a record, and one call for a whole production order (plan, the machines it actually ran on, material lots, inspection lots). Every answer names the model file and the ISA-95 relation it rests on, and says what the model cannot answer and why. It never writes — not to the broker, not to the model git. `--replay` reads a recording instead of a broker.
- **element_id joins both sides.** From UNSaC 0.7.2-j the edge writes the element path (`factory.werk1.sgm.line-a.sgm-004`) into its messages and every business record carries the element it names. The Explorer joins over that value where it is there, and over the model's name table where it is not (older recordings); the record says which.
- **Versions of a record.** The broker keeps the versions of a record (from 0.7.2-j up to 100). The record detail lists them: when, what changed (e.g. the planned machine sgm-004 → sgm-005), with the daily re-sends of an unchanged record folded.
- Machine joins count the code-list values of all their records (e.g. the decisions of the inspection lots), not only the newest ones shown.
- The model chosen at the start is no longer replaced by the model of last time when its git answers late.
- The connector counts records, not messages, so a record with several versions no longer shows as "read in part".
## 0.2.18 — beta (2026-11-17)
- **The Model Explorer no longer stalls each second.** Its mappings (which attributes the broker delivers right now) walked every record on each refresh — on the demo broker about 30,000, 90–190 ms every second. The Explorer now keeps the attribute names per source while records arrive, and what comes from the model alone is worked out once per model: 4 ms (at most 16 ms).

## 0.2.17 — beta (2026-11-17)
- **The Explorer no longer freezes on Gaps.** On a big broker (the demo broker: about 30,000 records) the Gaps page held the app for about a minute, and again every 15 seconds while it was open — Windows showed "not responding". Gaps now checks each record only for the links its model declares, and what is read from the model is read once per model, not once per record. On the demo broker Gaps answers in about a third of a second (was up to 59 seconds); the app is never held longer than about 0.4 seconds.
- The status line no longer sorts every topic each second to count them.

## 0.2.16 — beta (2026-11-16)
- Model Explorer · Entities: a node is named by its code — the part of the element path the broker subjects carry from core 6.2.0 — with its id beside it when the two differ.

## 0.2.15 — beta (2026-11-14)
- **One TESTS link per inspection lot, as in the knowledge graph.** From core 6.2.0 a source edge can name alternatives in priority order (`firstOf`): per record the first alternative with a value draws the one edge. The QMS inspection lot tests its quant, else its material lot, else its article. The Explorer showed three TESTS links per inspection lot (one per reference); Follow now shows the one link the graph draws, also from the other side: a material lot lists only the inspection lots that test the lot itself. Models without `firstOf` show as before.
- Model Explorer: the edges of a source list each alternative with its place ("alternative 2 of firstOf"). Gaps checks the column of every alternative like that of a plain edge; an alternative that points to a machine (`element_id`) joins records to the machine like a plain edge.

## 0.2.14 — beta (2026-11-11)
- **Follow loads what it misses from the broker.** On a big broker the Explorer holds only part of the records (the demo broker has 160,000 customer orders). When a link points to a record that is not loaded, Follow now asks the broker for exactly that record, by its id, in the current and the previous subject form, and goes on from there (an order, then its customer). On the demo broker, in a sample of 100 QMS inspection lots, Follow now finds the order for 100 instead of 71. One Follow takes about a quarter of a second. Works on NATS, the tablet included. MQTT and Kafka are unchanged.
- **Security (audit of 0.2.14, rc2).** A model git can no longer make the Explorer write to a broker: every subject filter is checked before it is sent (line breaks, control characters, blanks and empty parts are refused). Opening a model link can no longer delete folders: the clone folder is named by a hash of the link and stays inside the Explorer's cache, and a failed clone removes only what it created. A git token is sent only to the https address it was entered for.
- Secrets stay inside the app: the page never sees a stored password, access key or token (it shows "stored"), and a stored secret is used only for the broker address or model origin it was saved for. A login written into an address is refused; a warning shows when credentials go over a connection without TLS.
- Desktop: **Electron 45.3.1**. The page loads from the app's own `app://` address, only that one page, with a strict content security policy, no DevTools and no permissions in the packaged app; Electron's fuses are set (no Node mode, no inspector, asar integrity). Linux: the desktop entry asks once for sudo, so the app runs inside the operating system's sandbox.
- Tablet: the access key is encrypted with a key in the **Android Keystore**, and app data is no longer part of Android backups or device transfers; only `wss://`. Before this version the tablet kept the key only encoded, not encrypted: a key stored by 0.2.12–0.2.14 is removed once — enter it again — and keys used on a tablet before should be renewed.
- Kafka: the Explorer never creates topics. Follow asks the broker for at most 100 records per step. A busy or hostile broker can no longer fill the memory (a scan deadline and limits).

## 0.2.13 — beta (2026-11-11)
- **Follow links the data in both directions.** From a production order you now reach its customer order, article, BDE confirmations, material lots, segment requirements and responses, QMS inspections — and on from there. Every link says what it rests on: **edge** (the source declares it), **relationship** (a relationship of the profile), **model target** (the property names its target) or **by value** (the model names no target; the value is the key of those records — shown, marked orange). A chain line says how many records of which kind were reached; long lists show 5 cards per kind, the rest behind "+n more".
- Follow reads the reference targets of the coming model release (contract `refTargets`, `refStatus.targets / targetBy / relationship / direction / external`), abstract targets (Machine, Tooling) stand for their concrete kinds.
- **Gaps** reads topics in the previous subject form of the model (from the model git history) as such — a note per source with the last time seen, no longer "topics the model does not know". After the scan the Explorer asks the broker for every IT source it did not see (a small kind can fall between the scan's samples) — "sends nothing" is said only for what the broker was asked for; a source neither seen nor asked is "not seen".
- Tablet: a tap no longer lights up the lines of a card that comes to lie under the finger.

## 0.2.12 — beta (2026-11-11)
- **Android tablet app** (first: Samsung Galaxy Tab S8, landscape): the desktop Explorer 1:1 — Connect, Topics, Model Explorer with the map, Follow, Gaps. Brokers over a websocket (NATS `wss://`, MQTT `wss://`), the model from its git URL (kept on the tablet). Not on the tablet: Kafka, `tls://`/`nats://` direct, creds and CA files.
- Model Explorer · Profiles, also on the desktop: the "documented exception" note is one line (tap to open), filters, legend (behind a button) and zoom in one row, **⤢ large** shows the map over the whole window with the profile panel over it (× closes); the map reaches down to the foot. A tap or click on the empty map drops the picked profile. Two fingers zoom the map; a finger never edge-scrolls.

## 0.2.11 — beta (2026-11-11)
- Model Explorer · Profiles: the relation lines stay **behind** the cards also when a card is hovered or picked (0.2.10 brought them to the front then). The lines of the picked card are dark, the rest light; a faded card keeps its solid face, only its text fades.

## 0.2.10 — beta (2026-11-11)
- Model Explorer · Profiles: the relation lines lie **behind** the cards and are lighter while nothing is hovered or picked — the map is readable again. Hover or click a card: its lines turn dark and come to the front; a clicked profile keeps them after the mouse leaves the map (also after zooming).

## 0.2.9 — beta (2026-10-30)
- Joined records of a machine join on its **element_id** (the codes of the plant tree, e.g. `factory.werk1.cnc.line-a.cnc-002`), not on the name a source sent: every machine reference is resolved through the plant tree and `machine-identity.json` (ERP name, aliases). So the BDE confirmations with `cnc-002` and the operations with `cnc-02` are under the same machine.
- Every row says how it joined — `edge · ACTUAL_EQUIPMENT` (the source has an edge to the machine) or `refOnly · resolved` (a value the model keeps without an edge) — with what the source said next to it. A name the model does not know is "unresolved" in Gaps and joins nothing.
- The machine's header shows its element_id and every known name (bus, ERP, aliases, OPC UA machineName) with the evidence date of the identity map. The subject column names the record by its model entity (e.g. `BdeConfirmation`), the raw subject on hover.
- Entities: on core 6.0.0 the machines below a work center show again in the plant tree.
- The Model Explorer works with every model you open — a folder or any git address, any branch or tag; before, it worked only with GitHub branch next.

## 0.2.8 — beta (2026-10-29)
- Reads the next model generation (osf-schemas core 6.0.0 = standard 7.0.0, UNS convention 2.0.0) without the "older Explorer" banner: the ISA-88 batch profiles, machines as WorkCells of a ProductionLine, Tooling. The model of 27.10. is still read, with a note that it is older.
- A fixed value in a source (e.g. operations type = Production) counts as mapped and shows as "= Production"; before, the attribute looked unmapped.
- A code list of a source (e.g. order status offen → Waiting … storniert → Cancelled) shows under its attribute.

## 0.2.7 — beta (2026-10-29)
- Connecting is quick again: "Logging in", then "connected" within seconds — the Explorer no longer waits until it has read everything the broker holds. The Topics tab opens and shows the scan with its progress (stream 2 of 3, values read); the topics fill in while it scans.
- MQTT: the access key you were sent works for MQTT too — paste it into "Access key" (before, only "Password" worked and "Access key" gave "Not authorized"). The demo broker over MQTT: `wss://mqtt-demo.uns-as-code.com/mqtt`.
- The broker's own streams (names starting with `$`, e.g. the demo's MQTT sessions) are no longer read — waiting for them left the Explorer hanging for minutes.

## 0.2.6 — beta (2026-10-29)
- A broker with a very big stream (the demo: 690 000 business records) shows its history again right after connecting — before, the Explorer asked for the whole list of topics, the broker closed the connection and no history came at all. Every kind of record still gets its fair share of its newest values.
- On a busy stream the last value of every topic arrives (the demo's telemetry gave 39 of 93 before).

## 0.2.5 — beta (2026-10-29)
- On the demo broker every value the factory has sent in the last 30 days is there right after connecting — also sources that send only every 15 minutes or only on a change. A value the demo copied from the factory hub shows the time the hub stored it, not the time of the copy.

## 0.2.4 — beta (2026-10-28)
- Save on "UNS-as-Code demo" keeps your access key (only encrypted) — before, it said the name was built in and kept nothing. Save with an empty key field forgets it.

## 0.2.3 — beta (2026-10-28)
- The Explorer always opens on the demo broker `wss://nats-demo.uns-as-code.com` — also after an update over an older version; an old connection no longer fills the form.
- "UNS-as-Code demo" is always the first saved connection: one pick fills the form and empties the old creds and CA fields.
- Your access key for the demo is kept (only encrypted); from then on the Explorer connects to the demo by itself at start.
- An access key together with a creds file is no longer guessed: the Explorer says to empty one of the two.

## 0.2.2 — beta (2026-10-28)
- NATS access key: paste the one line you were sent into "Access key" — no creds file to copy to every computer. It is kept only encrypted by your system's keychain.
- The Explorer connects by itself at start to the connection that worked last time.

## 0.2.1 — beta (2026-10-28)
- NATS over a websocket: `ws://` and `wss://` URLs connect through the websocket (before, they ended in a plain connection to port 4222).
- The first start fills the connect form with the public demo broker `wss://nats-demo.uns-as-code.com` (NATS, no login, read only): one click on Connect shows a live factory.

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
