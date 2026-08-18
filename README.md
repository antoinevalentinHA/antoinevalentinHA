# antoinevalentinHA

I run one Home Assistant system in a family home, and I govern it like software: a written contract before any code, one decision authority per domain, and CI that blocks whatever contradicts the contract. I am not a developer. I use AI as an execution force under constraints I set, and I make the calls.

Almost everything on this account exists because that system needs it. **Start with [Arsenal](https://github.com/antoinevalentinHA/arsenal).**

---

## Arsenal — the system

**[Arsenal](https://github.com/antoinevalentinHA/arsenal)** is an in-production Home Assistant configuration for a family home. It covers heating, domestic hot water, air conditioning, ventilation, irrigation, energy, security, presence, indoor and outdoor measurement, dashboards and infrastructure observability.

**46 contractual domains · ~1,800 YAML files · ~3,900 entities.**

Three rules hold it together:

- **The contract comes first.** Every domain is written down before it is built. If the code contradicts the contract, the code is wrong — not the contract.
- **Decision, execution and display are separate.** One decision authority per domain produces a readable state, bounded executors apply it, dashboards observe it. Never the reverse.
- **CI is a boundary, not an oracle.** Red is forbidden. Green only means a change is admissible to human judgement.

The same discipline governs the AI assistance: no invented entity IDs, no casual renames, whole files in their real tree, and contracts that bound what a proposal is allowed to claim. Fast execution is not allowed to turn into silent drift.

The documentation is in French; the repository README is an English entry point. Arsenal is not a configuration to copy — its entities and topology belong to one house. What travels is the method.

---

## Written for this system

| Repository | What it is |
|---|---|
| **[ha-state-archive](https://github.com/antoinevalentinHA/ha-state-archive)** | Archival pipeline for the configuration: versioned states, integrity audits, release-oriented diffs, retention. It runs on my NAS and is published as a versioned container image on GHCR, with a CI test suite and automated publishing. |
| **[ha-archive-search](https://github.com/antoinevalentinHA/ha-archive-search)** | Search, inspection and export over those archives: corpus engine, CLI, small web app, Markdown export. Same packaging — versioned GHCR image, CI tests. When a domain behaves oddly, the answer is usually in here. |
| **[boilerack](https://github.com/antoinevalentinHA/boilerack)** | A transactional MQTT bridge over an existing `vcontrold`, for Viessmann boilers on an Optolink link. Commands are identified, expirable and confirmed by reading the boiler back — never assumed to have succeeded. Same ground as Arsenal's boiler contracts, which specify acknowledged transactional commands. **Under construction: nothing is released, and none of it has been exercised against a real boiler or broker.** |
| **[ha-termux-tools](https://github.com/antoinevalentinHA/ha-termux-tools)** | Bash scripts that mirror the configuration onto an Android phone, so it can be searched and inspected from Termux. |

---

## Derived work — the forks, and what is mine in them

Arsenal runs on these. They are pinned, patched and kept in working order, and fix branches are kept ready for upstream.

| Fork | Upstream | What is upstream, and what is mine |
|---|---|---|
| **[rainbird-esp32-elegoo](https://github.com/antoinevalentinHA/rainbird-esp32-elegoo)** | **[maillme/rainbird-esp32](https://github.com/maillme/rainbird-esp32)** — Neil Smith | **The upstream holds the original design and the vast majority of the code**: SIP-over-BLE protocol, MQTT discovery, OTA. My fork retargets it at the ELEGOO ESP32 (WROOM-32) board — an `esp32dev` PlatformIO environment, light-sleep power management that compiles for both boards, and a two-station configuration. This is the firmware in service on my irrigation bridge. [rainbird-esp32](https://github.com/antoinevalentinHA/rainbird-esp32) is my copy of the upstream XIAO ESP32-C3 variant it grew out of. |
| **[ha_airstage](https://github.com/antoinevalentinHA/ha_airstage)** | [danielkaldheim/ha_airstage](https://github.com/danielkaldheim/ha_airstage) | Fujitsu air conditioning. Served from the `arsenal-stable` branch (manifest 1.7.1). Its Python library, `pyairstage`, is upstream and unforked: the manifest requires at least 2.4.1 and stops below 3.0. |
| **[hassio-bluetti-bt](https://github.com/antoinevalentinHA/hassio-bluetti-bt)** · **[bluetti-bt-lib](https://github.com/antoinevalentinHA/bluetti-bt-lib)** | [Patrick762](https://github.com/Patrick762) | Bluetti power stations. Arsenal vendors integration 0.2.2, which installs the library from an exact versioned wheel release of my fork (`v1.1.0`). Stability comes from that version pin, not from a branch. |
| **[ha-linky](https://github.com/antoinevalentinHA/ha-linky)** | [bokub/ha-linky](https://github.com/bokub/ha-linky) | Linky smart meter, as a Supervisor add-on. Carries a fix branch anticipating a Home Assistant recorder statistics change. |
| **[atmofrance](https://github.com/antoinevalentinHA/atmofrance)** | [sebcaps/atmofrance](https://github.com/sebcaps/atmofrance) | Air quality for French cities. This one has moved past a pinned fork into a **maintained distribution**: its own releases (2.1.10 is what Arsenal runs), a local codeowner, documentation and issue tracker pointing here, and branches that track upstream. |

**[audi_connect_ha](https://github.com/antoinevalentinHA/audi_connect_ha)** is the exception: I contribute to the integration instead of running my own build. The fork exists to carry `fix/*` branches toward upstream — transient 403/502 handling, auth guards, French translation — while my installation stays on the official release (2.3.1).

---

## Patterns pulled out of the system

Four small repositories, each isolating a single pattern from the running configuration:

- **[ha-heating-decision-engine](https://github.com/antoinevalentinHA/ha-heating-decision-engine)** — one script that decides `comfort` / `reduced` / explicit abstention, with strict priority ordering, instead of heating logic scattered across automations.
- **[ha-mobile-notification-architecture](https://github.com/antoinevalentinHA/ha-mobile-notification-architecture)** — a stable notification API that decouples automations from specific phones.
- **[ha-self-parametrized-template-sensors](https://github.com/antoinevalentinHA/ha-self-parametrized-template-sensors)** — template sensors that configure themselves from their own `this.entity_id`, written once and reused across rooms.
- **[ha-automation-id-generator](https://github.com/antoinevalentinHA/ha-automation-id-generator)** — the next free automation ID for a numeric prefix, in native Home Assistant.

They are self-contained, and they still answer questions people ask.

---

## Outside Home Assistant

**[rallye-trip-meter-android](https://github.com/antoinevalentinHA/rallye-trip-meter-android)** — a rally trip meter for Android (Kotlin, Jetpack Compose): GPS partial distance corrected to the metre, total distance, instant speed, manual calibration. Different domain, same method: a functional contract before the code, and the package is `fr.arsenal.rallyetripmeter`. Tagged `v0.3.0-preview` — usable and validated on device, final field validation still ahead.

**[studio](https://github.com/antoinevalentinHA/studio)** — a fork of **[marian-m12l/studio](https://github.com/marian-m12l/studio)** (Java), which creates and transfers story packs to and from the Lunii story teller device. I maintain the fork for robustness in real use: device detection that waits for the mount instead of timing out, a pack index that refuses a malformed `.pi` rather than fabricating a UUID, a free-space precheck that counts what the transfer actually adds, and an index installed by atomic move instead of written in place. CI runs the Java suite on Linux and Windows plus the JavaScript suite. Work in progress — the repository documents which write-path failure modes are still open.

---

Bordeaux, France.
