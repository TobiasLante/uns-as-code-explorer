<p align="center"><img src="icon.png" width="96" alt=""></p>

# UNS-as-Code Explorer

> **Beta 0.2.0 — not a final version.** Things will change, some views are rough, and there will be bugs. Feedback is welcome (Issues).

A read-only desktop explorer for a Unified Namespace — **NATS, MQTT or Kafka** — as simple as MQTT Explorer.

- **Without a model** it shows the topic tree, live values, telemetry vs transactional (with the reason), data quality and naming findings.
- **With a UNS-as-Code model git** it adds the semantics: the plant from the model's instances, profiles, units, ISA-95 objects, the rules
  on an attribute and where their band comes from, *follow a work order*, *follow a decision* and the gaps between model and broker.

The Explorer **only reads**: it never publishes to a broker, never commits Kafka offsets and never writes to the model git.
No telemetry. The only call besides your broker and model git: at start it asks GitHub whether a newer version exists (you can switch that off).

## Download

The newest version, always:

- **Windows 10/11 (x64), setup:** [https://github.com/TobiasLante/uns-as-code-explorer/releases/latest/download/UNS-as-Code-Explorer-win-x64-setup.exe](https://github.com/TobiasLante/uns-as-code-explorer/releases/latest/download/UNS-as-Code-Explorer-win-x64-setup.exe)
  installs for your user only — no admin rights; start menu and desktop entry, uninstall in the Windows settings. Not signed: SmartScreen asks once — "More info" → "Run anyway"
- **Windows 10/11 (x64), portable zip:** [https://github.com/TobiasLante/uns-as-code-explorer/releases/latest/download/UNS-as-Code-Explorer-win-x64.zip](https://github.com/TobiasLante/uns-as-code-explorer/releases/latest/download/UNS-as-Code-Explorer-win-x64.zip)
  unzip anywhere (no admin rights needed), run `UNS-as-Code Explorer.exe`. The program is not signed: Windows SmartScreen asks once — "More info" → "Run anyway"
- **Linux (x64):** [https://github.com/TobiasLante/uns-as-code-explorer/releases/latest/download/UNS-as-Code-Explorer-linux-x86_64.AppImage](https://github.com/TobiasLante/uns-as-code-explorer/releases/latest/download/UNS-as-Code-Explorer-linux-x86_64.AppImage)
  `chmod +x` and run (needs FUSE 2)
- **Linux (x64), no FUSE and no root needed:** [https://github.com/TobiasLante/uns-as-code-explorer/releases/latest/download/UNS-as-Code-Explorer-linux-x64.tar.gz](https://github.com/TobiasLante/uns-as-code-explorer/releases/latest/download/UNS-as-Code-Explorer-linux-x64.tar.gz)
  unpack, run `./uns-as-code-explorer`; `./install-desktop-entry.sh` adds it to your app menu

Older versions and `SHA256SUMS`: [Releases](../../releases).

## The model it shows: osf-schemas, branch `next`

Out of the box (0.2.0) the Explorer shows the public UNS-as-Code model repository **osf-schemas**, branch **`next`**, plant `werk1` —
no broker, no login needed: **[https://github.com/TobiasLante/osf-schemas/tree/next](https://github.com/TobiasLante/osf-schemas/tree/next)**

On the first start it opens that model, so you can look around right away: the plant, its machines, profiles, units, rules and ISA-95 objects.
Connect a broker when you want live values; pick another model git (a local clone or its URL) when you have your own.

## Connect

- **NATS:** `nats://host:4222` or `tls://host:4222`; user + password, a `.creds` file (JWT) and/or a CA file.
- **MQTT:** `mqtt://host:1883`, `mqtts://host:8883`.
- **Kafka:** `kafka://host:9092[,host2:9092]`, `kafka+ssl://…`; values in Avro: also give the schema registry (`http://registry:8081`).
- With a CA file TLS is required — never a silent fall back to plain text. Passwords and tokens are kept in the system keychain, never in plain text.

## Model (optional)

A UNS-as-Code model git: a local clone or its URL (the Explorer clones it into its own cache, read only). Pick a release tag
`unsac/<x.y.z>` or a branch, and the site.

## Known limitations (beta)

- Payloads: JSON and Avro (Kafka with a schema registry); Sparkplug B is not supported.
- The Windows program is a zip (no installer yet) and not code-signed.
- Large brokers: the topic tree keeps a bounded history per subject; very large retained sets take a while to load.

## Licence

Apache-2.0 — see [LICENSE](LICENSE) and [NOTICE](NOTICE).
