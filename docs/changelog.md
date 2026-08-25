# Change Log — Team G5

Records every requirement or technology change made after a sprint has started, as committed in
`docs/process.md`, Section 4, rule 5. Each entry states **when** the change happened, **why**, and
**what it cost us**. Entries are appended, never rewritten.

Format: `YYYY-MM-DD — What changed`, then Reason and Impact.

---

## 2026-08-12 — Initial client decision: web application

**Reason.** First team plan assumed a browser-based client, reusing Vân's existing web
experience.

**Impact.** Directory layout, screen list and the UI section of the plan were all written against
a web client.

---

## 2026-08-13 — Client changed from web application to mobile application

**Reason.** The project brief describes a personal-expense *app*. A browser client would not
demonstrate the platform constraints the team wanted to work with, and the instructor's brief
asks for a live demo.

**Impact.** The entire client layer was re-planned. Screen list, navigation model and the client
half of the technology stack were replaced. The backend, database schema and REST API were **not**
affected — the client–server split contained the change to one layer. This is the first evidence
cited in `docs/process.md`, Section 2, question 1.

---

## 2026-08-13 — Mobile SDK dropped by three major versions

**Reason.** The spike was built against the newest published SDK. The store version of the
runtime installed on the team's demo device supports only an older SDK line, and that runtime
refuses to open a project built on a newer one. The constraint is external: the team does not
control which runtime version the app store ships.

**Impact.** Downgraded the SDK and every framework version tied to it. Two follow-on repairs were
needed that the automated version tool did not handle: the navigation library had to be removed
and reinstalled rather than upgraded in place, because installing over the old version produced a
peer-dependency conflict; and one build-time package that used to arrive as an indirect
dependency had to be declared explicitly. Verified afterwards that the client still bundled and
that all unit tests passed.

**Lesson recorded.** This is the "price of reuse" discussed in week 3: a dependency the team does
not control can rewrite the plan. It is the second evidence cited in `docs/process.md`,
Section 2, question 1, and the mechanism behind Section 3.

---

## 2026-08-13 — Constraint found: campus Wi-Fi blocks device-to-device traffic

**Reason.** The campus network isolates connected clients from each other, so the demo device
could not reach the development machine even on the same network. Discovered only by running the
client on real hardware.

**Impact.** Demos and integration testing now run over a phone hotspot instead of campus Wi-Fi.
Recorded as a standing constraint for the final demo in week 15, not a one-off workaround.
