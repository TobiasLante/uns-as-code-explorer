<p align="center"><img src="icon.png" width="96" alt=""></p>

# UNS-as-Code Explorer

A read-only desktop explorer for a Unified Namespace on **NATS, MQTT or Kafka**, plus the meaning behind each topic from a UNS-as-Code model.

> Beta 0.2.0 — feedback welcome in [Issues](../../issues).

## Download

| System | File |
|---|---|
| Windows 10/11 | [Setup](https://github.com/TobiasLante/uns-as-code-explorer/releases/latest/download/UNS-as-Code-Explorer-win-x64-setup.exe) (no admin rights) · [Zip](https://github.com/TobiasLante/uns-as-code-explorer/releases/latest/download/UNS-as-Code-Explorer-win-x64.zip) |
| Linux x64 | [AppImage](https://github.com/TobiasLante/uns-as-code-explorer/releases/latest/download/UNS-as-Code-Explorer-linux-x86_64.AppImage) · [tar.gz](https://github.com/TobiasLante/uns-as-code-explorer/releases/latest/download/UNS-as-Code-Explorer-linux-x64.tar.gz) (no FUSE, no root) |

The links always give the newest version. Windows: the program is not signed, SmartScreen asks once ("More info" → "Run anyway").
Older versions and checksums: [Releases](../../releases).

## Try it without a broker

On first start the Explorer opens the public model **[osf-schemas, branch next](https://github.com/TobiasLante/osf-schemas/tree/next)** —
browse the plant, machines, profiles, units and rules right away.

## Connect your broker

- **NATS** `nats://` or `tls://` — user/password, `.creds` file, CA file
- **MQTT** `mqtt://` or `mqtts://`
- **Kafka** `kafka://` — Avro via a schema registry

Then you see the topic tree with live values, and — with a model — what each topic means, which rules apply and where model and broker differ.

## Read only

The Explorer never publishes, never commits Kafka offsets and never writes to the model. Passwords stay in the system keychain.
It only asks GitHub at start whether a newer version exists (can be switched off).

## Licence

Apache-2.0 — see [LICENSE](LICENSE) and [NOTICE](NOTICE).
