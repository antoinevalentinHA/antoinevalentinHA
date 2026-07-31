# antoinevalentin

I run one system, and everything here orbits it.

**[Arsenal](https://github.com/antoinevalentinHA/arsenal)** is an in-production Home Assistant configuration for a family home — heating, domestic hot water, air conditioning, ventilation, irrigation, energy, security, presence, measurement, dashboards and infrastructure observability. It is built contract-first: every domain has a written contract before it has code, a single decision authority per domain, and CI that refuses what contradicts the contract. The documentation is written in French; the repository README is an English entry point.

The rest of this account is what that system needs in order to run.

---

## Tooling built around Arsenal

| Repository | What it does |
|---|---|
| [ha-state-archive](https://github.com/antoinevalentinHA/ha-state-archive) | Structured archival of Home Assistant versions — state versioning, automated auditing, configuration integrity. |
| [ha-archive-search](https://github.com/antoinevalentinHA/ha-archive-search) | Infrastructure-side search engine over those archives. |
| [ha-termux-tools](https://github.com/antoinevalentinHA/ha-termux-tools) | Inspecting and grepping the configuration from Android, via Termux. |
| [rainbird-esp32](https://github.com/antoinevalentinHA/rainbird-esp32) · [rainbird-esp32-elegoo](https://github.com/antoinevalentinHA/rainbird-esp32-elegoo) | ESP32 firmware bridging Rain Bird battery-powered BLE controllers to MQTT, with OTA updates. The second is an ELEGOO WROOM-32 board variant. |

## Integrations my installation loads

These four forks are not scratch copies: Arsenal runs on them. They are pinned, patched and kept in working order, and fixes go upstream where upstream can take them.

| Fork | Upstream | Why it is forked |
|---|---|---|
| [ha_airstage](https://github.com/antoinevalentinHA/ha_airstage) | danielkaldheim | Fujitsu air conditioning. Served from a stable branch, pinned to pyairstage 2.4.x. |
| [hassio-bluetti-bt](https://github.com/antoinevalentinHA/hassio-bluetti-bt) · [bluetti-bt-lib](https://github.com/antoinevalentinHA/bluetti-bt-lib) | Patrick762 | Bluetti power stations. Served from a stable branch. |
| [ha-linky](https://github.com/antoinevalentinHA/ha-linky) | bokub | Linky smart meter. Carries a fix branch anticipating a recorder statistics change. |
| [atmofrance](https://github.com/antoinevalentinHA/atmofrance) | sebcaps | Air quality for French cities. |

## Upstream work

[audi_connect_ha](https://github.com/antoinevalentinHA/audi_connect_ha) — I contribute to the integration itself rather than run my own version of it: my fork exists to carry `fix/*` branches (transient 403/502 handling, auth guards, FR translation) toward upstream, and my installation stays on the official release.

## Patterns published from Arsenal

Extracted from the running system and published as-is, for whoever finds them useful. They are stable rather than active — they document an approach, they are not products.

- [ha-heating-decision-engine](https://github.com/antoinevalentinHA/ha-heating-decision-engine) — centralized heating decisions: strict priority, abstention, anti-bounce.
- [ha-mobile-notification-architecture](https://github.com/antoinevalentinHA/ha-mobile-notification-architecture) — decoupling automations from mobile devices.
- [ha-self-parametrized-template-sensors](https://github.com/antoinevalentinHA/ha-self-parametrized-template-sensors) — write the template logic once, reuse it across many entities.
- [ha-automation-id-generator](https://github.com/antoinevalentinHA/ha-automation-id-generator) — next available automation ID, no custom integration required.

## Outside all of this

[rallye-trip-meter-android](https://github.com/antoinevalentinHA/rallye-trip-meter-android) — a native Android/Kotlin rally trip meter: GPS distance, stage and total distance, manual calibration. Unrelated to the rest, and the only thing here that is.

---

Bordeaux, France.
