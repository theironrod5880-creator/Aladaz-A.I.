# Aladaz A.I. — What the Page Is and Isn't

**File this describes:** `aladaz-ai.html`
**Status:** working. One file. No build step, no dependencies, no server.

**Naming, held throughout:** *Aladaz A.I.* is the title on the page and the APK.
It never speaks. **Bryar** is the system inside it — the voice, the teacher, the
messenger. That distinction is deliberate and it holds everywhere.

---

## What it is

A private study companion for one person: Alada. One HTML file that opens in
any browser and runs. Bryar answers from a Mastercore embedded in the page — a
study brief written by Alada's father, carrying sources, translations, a
chronology framework, and a set of tone rules.

It is not a product. It is one family's file.

---

## Two modes

**Core Mode (default).**
Bryar answers by keyword match against the embedded Mastercore. No network
calls. Nothing leaves the device. If the question reaches past what the core
holds, Bryar says so and points to the topics it can teach.

**Connected Mode (opt-in).**
The user supplies an OpenAI-compatible endpoint, an API key, and a model name
in Settings. Once set, each turn sends the Mastercore plus the last twelve
messages of the current thread to that endpoint. Nothing else is sent.

If the connection fails, the page says so plainly and falls back to Core Mode.
It does not pretend an answer came from somewhere it didn't.

---

## What stays on the device

Three things are stored in the browser's `localStorage` on that device only,
and are never transmitted in either mode:

| Storage key | What it holds | Sent to any model? |
|---|---|---|
| `aladaz.sealed` | Alada's sealed layer — her own notes | **Never** |
| `aladaz.sandra` | Private family entries | **Never** |
| `aladaz.settings` | Endpoint, API key, model | Not sent; used to make requests |

Chat threads (`aladaz.threads`) also stay local, and only the most recent
twelve messages of the current thread travel to a model — and only in
Connected Mode.

Sandra's entry is deliberately kept out of the Mastercore string. It is not in
what gets sent when Connected Mode is on. That was a design choice, not an
oversight: private in intent is also private in transmission.

---

## What the API key really is

The key is stored in plaintext in `localStorage`. That is fine on a personal
device. It is not fine if this file is shared, published, or bundled into an
APK for other people. Anyone with device access, or a malicious browser
extension, can read it.

If the file is going to be distributed: keep the key out of the app and let
each user paste their own, or encrypt at rest with a passphrase. Not doing this
is a choice; it should be a stated one, not a forgotten one.

The endpoint URL is user-supplied. A typo sends the core and chat history
somewhere unintended. Verify before saving.

---

## What the Mastercore contains

Section references for anyone reading the embedded core:

1. Who Bryar is
2. Who Alada is
3. The Floor — Watchtower Society and JW.org stand first on every subject
4. Sources and translations — Watchtower first, everything named, differences shown
5. How Bryar teaches
6. The 5,880 framework
7. What Bryar builds — layers of the work
8. Execution rules
9. Checkup — the steady friend posture
10. The layers — Alada's sealed layer and Earl's layer open to her
11. The close

The full text is in the `CORE` constant near the top of the script in
`aladaz-ai.html`.

---

## What the page does not do

- It does not access any repository, folder, or external file. It reads what
  is embedded, and nothing else.
- It does not govern the vault. Bryar reads what it is given and cites what it
  reads. Authority over the vault sits with the author.
- It does not remember across devices. Storage is per-device.
- It does not claim authority it does not have. When it can't reach a source,
  it says so.

---

## Reading rules, as the page carries them

- Watchtower Society and JW.org stand first on every subject. Other sources
  are laid beside them — never above, never against.
- Default translation: NWT 1983.
- Where sources differ, the difference is shown, not flattened.
- Unsettled questions are held open, and said so plainly.
- No crosses, icons, graven images, or religious symbols in any output. The
  structural word "cross" (the crossing point of two spines) is permitted —
  the rule governs imagery only.

---

## To use it

1. Save the file as `aladaz-ai.html`.
2. Open it in any modern browser.
3. It runs. No installation, no build.
4. For Connected Mode, open Settings and enter endpoint, key, and model.
5. For the APK, wrap the file in a web view; storage and settings behave the
   same on-device.

---

*Made by Earl Arthur Sewell for Alada, his daughter. I stand by my work.*
