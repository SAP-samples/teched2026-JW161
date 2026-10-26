# Exercise 3 – Explore on Your Own

From here, you drive. These are open-ended prompts and short challenges to
build your understanding of how a request and the rules interact. Most run from
the **Generate a view** prompt (SAP logo → type → Generate) against the SFlight
data.

> **Prerequisite:** [Exercise 2 – Author and Generate](../ex2/2_AuthorAndGenerate.md).
> **Tool:** <https://compositional-ui-tooling.cfapps.eu10-005.hana.ondemand.com/>

---

## 3.1 Phrasing and composite selection — change the request, observe the result

Run these in sequence and read the **Reasoning flow** each time to see which composite was selected and why:

| Prompt | Expected result |
| --- | --- |
| `Show me total revenue across all travels` | A single headline number → a `Metric` / KPI, not a table. |
| `Compare total price by agency` | A categorical breakdown → a **bar chart** composite. |
| `Show the trend of bookings over time` | A temporal series → a **line chart** composite. |
| `List every booking with its status` | A scannable list or table. |
| `Give me a full overview of travel bookings` | A richer, multi-section composite (e.g. a page or combined card). |

**Challenge:** phrase a request two different ways that produce the **same** composite; then two *similar* requests that produce **different** composites. Identify the wording that changed the outcome.

---

## 3.2 Interpreting the reasoning

Select any generated view and, using only the left-hand panels, answer:

1. How many **records** were fetched, and how many **fields**?
2. How many composites were **considered** versus **selected**?
3. What was the **one-sentence reason** for the selection — and is it sound?
4. In the **Used composite** tree, which **primitives** did the selected composite render?

This exercise builds the ability to explain a generated UI to a colleague using only the information the panel provides.

---

## 3.3 Tracing behaviour back to a rule

Go to **Edit → Composites** and open the composite selected for one of your prompts (e.g. **Table Card** or **Bar Chart Card**). Read its **When / Never / Must** rules.

**Challenge:** identify the exact rule sentence that explains why the prompt resolved to *that* composite rather than a neighbouring one (e.g. the KPI card's *"Prefer KPI over table when there are very few metrics (≤5)"*). This connects observed behaviour to the authored design knowledge.

---

## 3.4 Author a composite from a description

Repeat the authoring flow from Exercise 2 with your own idea. The aim is to experience that extending the catalogue is a plain-language task.

1. In **Edit → Composites**, click **`+ Add Composite`**.
2. **Location** — enter a group such as `cards` (or type a new one). Click **Next**.
3. **Name** — give it a clear display name (e.g. `Agency Scorecard`, `Booking Highlights`). Click **Next**.
4. **Describe** — write a one- or two-sentence brief naming the data to show, the layout, and any emphasis. Examples:
   - *"A card ranking travel agencies by total booking value, highest first, each row showing the agency name and its total."*
   - *"A compact card highlighting the single most expensive travel booking, with its agency, price, and status."*
5. Click **Generate & open** and review what the system produced:
   - the **Purpose** and the **Private (only you)** badge (user-authored layer);
   - the **When / Never / Must** rules it drafted — in particular, how the **Never** rule positions the new composite against existing ones (e.g. "use cards/table instead");
   - the live **Preview** against SFlight data;
   - the **Spec** view, to see which primitives it composed.
6. Open the **Properties** sub-tab to see the inputs the new composite exposes.

![The New Composite wizard: Location → Name → Describe.](./images/09-new-composite-wizard.png)

**Challenge:** write two briefs for the *same* data that differ only in emphasis (e.g. "rank by value" vs. "show status at a glance") and compare the rules the system drafts for each. What did it infer about *when* each should be used?

> If **Generate & open** is unavailable, the authoring LLM is not configured on the tenant (the Describe step notes it requires a service key). Use **Skip** to create an empty stub, or treat this exercise as a walkthrough of an already-generated composite such as **Object Card** from Exercise 2.

---

## 3.5 Change a rule and observe the effect on generation

This exercise shows that **design knowledge is live**: editing a rule changes how the system reasons about a composite in future generations. Use a **Private (only you)** composite — e.g. **Object Card** from Exercise 2 — so the SAP-standard composites are left untouched.

1. Run a generation that selects the composite, and note the result and the **Reasoning flow**. For Object Card: `show me a comprehensive view on travel 00000001`.
2. Go to **Edit → Composites**, open that composite, and edit a rule in the **Rules Definition** tab — for example, strengthen the **Never** rule (*"Never use this composite if the object has no related child collection; prefer cards/detail"*) or sharpen the **When** rule toward a narrower case.
3. Click **Save**.

![An earlier example of editing a private composite; Save / Reset appear once the rule is changed.](./images/13-edit-rule-save.png)

4. Return to **Generate a view**, run the same prompt again, and read the **Reasoning flow**. Compare against step 1: did the candidate ordering change, did the one-sentence reason change, or did the selected composite change?

**What to expect — and the real lesson:** the outcome is **not guaranteed to flip**. A strongly worded, explicit request ("as a list") can still outweigh a discouraging rule, while a more ambiguous request is swayed more easily. The point is not to force a particular result but to observe, in the **Reasoning flow**, that the edited design knowledge is genuinely being consulted — and to feel how rule wording and request wording compete. Reset the rule (**Reset**, or restore the original text and **Save**) when done.

---

## 3.6 Free-form scenarios (SFlight)

The dataset's shape is **travels, bookings, agencies, customers, prices (USD), booking fees, status (Open / Accepted / Canceled), start/end dates**. Compose your own requests against it. Suggested starting points:

- *"Which agencies have the most cancelled bookings?"*
- *"Show me the five most expensive travels."*
- *"A dashboard a travel manager would want on a Monday morning."*
- *"Summarise bookings by status."*

Re-generate with small wording changes and observe how the reasoning shifts.

---

When you're done, see **[Further Resources and Thank You](../overall_content/ConclusionAndResources.md)**.
