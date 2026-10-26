# Getting Started

Everything you need before the first exercise.

## The tool

**CompUI Tooling (Tech Preview)** —
<https://compositional-ui-tooling.cfapps.eu10-005.hana.ondemand.com/>

## The dataset

The standard SAP **SFlight** travel scenario — travels, bookings, agencies,
customers, prices (USD), booking fees, status (Open / Accepted / Canceled),
and start/end dates. Every preview and generated view in this session is bound
to this live data.

## Before you start

| What | Detail |
| --- | --- |
| **Access** | SAP SSO login. On the login screen choose **`tdct3ched1.accounts.ondemand.com`** as the identity provider, then sign in with the provided training user (e.g. `jw163-002@education.cloud.sap`). |
| **Browser** | Any modern desktop browser, maximised. The tool is a dense three-pane layout — a small window hides panels. |
| **Status check** | Top-right should read **`CAP · online`** (green). This means the data service backing the SFlight scenario is reachable. If it's red, flag it before starting. |
| **Workspace tabs** | Top-centre has two tabs: **Edit** (author primitives and composites) and **Test** (generate views from a prompt). You move between them during the session. |

## Tips

- **If a generation renders empty or unexpected**, use **Regenerate** — the generation step is non-deterministic and a re-run typically resolves it. Confirm `CAP · online` is green first.
- **Composite authoring (2.2 and 3.4) calls the LLM** and depends on the authoring service being configured on the tenant. If **Generate & open** is disabled, use **Skip** or fall back to a pre-existing composite.
- **For the rule-editing exercise (3.5), use a Private (only you) composite**, never an SAP-standard one, and **Reset** the rule afterwards. The effect on a generation is a tendency, not a guarantee — the lesson is in the **Reasoning flow**, not in forcing a particular selection.
- **Return to the Reasoning flow often.** It is the most instructive surface in the tool; pair each result with its trace.

Ready? Begin with **[Exercise 1 – Explore the Workbench](../ex1/1_ExploreTheWorkbench.md)**.
