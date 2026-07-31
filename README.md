# antoinevalentin

I run one system, and everything here orbits it.

**[Arsenal](https://github.com/antoinevalentinHA/arsenal)** is an in-production Home Assistant configuration for a family home — heating, domestic hot water, air conditioning, ventilation, irrigation, energy, security, presence, measurement, dashboards and infrastructure observability. It is built contract-first: every domain has a written contract before it has code, a single decision authority per domain, and CI that refuses what contradicts the contract. The documentation is written in French; the repository README is an English entry point.

The rest of this account is what that system needs in order to run.

---

## The archive, used daily

A system that changes every day needs a record of what it was yesterday. Two pieces run on my NAS and are part of the daily routine, not accessories:

- **[ha-state-archive](https://github.com/antoinevalentinHA/ha-state-archive)** — structured archival of the configuration: state versioning, automated auditing, integrity checks.
- **[ha-archive-search](https://github.com/antoinevalentinHA/ha-archive-search)** — the search engine over those archives, on the infrastructure side. When a domain behaves oddly, this is where the answer usually is.

## Tooling around Arsenal

| Repository | What it does |
|---|---|
| [rainbird-esp32-elegoo](https://github.com/antoinevalentinHA/rainbird-esp32-elegoo) | The firmware in service on my irrigation bridge: an ELEGOO ESP32 WROOM-32 board linking Rain Bird battery-powered BLE controllers to MQTT, with OTA updates. Derived from [rainbird-esp32](https://github.com/antoinevalentinHA/rainbird-esp32), which is the upstream fork it grew out of. |
| [ha-termux-tools](https://github.com/antoinevalentinHA/ha-termux-tools) | Inspecting and grepping the configuration from Android, via Termux. |

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

## Earlier pieces

A handful of small repositories date from before Arsenal was public: single patterns pulled out of the running system — a heating decision engine, a notification architecture, self-parametrized template sensors, an automation ID generator. They are left online because they still answer questions people ask, but they are early work and stand on their own only modestly.

## Outside all of this

[rallye-trip-meter-android](https://github.com/antoinevalentinHA/rallye-trip-meter-android) — a native Android/Kotlin rally trip meter: GPS distance, stage and total distance, manual calibration. Unrelated to the rest, and the only thing here that is.

---

Bordeaux, France.
