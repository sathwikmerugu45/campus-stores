# Campus Stores

## My work

### Shift walkthrough

Working through the shift from Friday afternoon to Saturday morning:

**Phase 1 — Friday 3:45 pm: Pickup**
Kabir Sen arrived to collect the Film Society's screening kit (RQ-214). I checked the approved request (HDMI projector, portable speaker, USB-C → HDMI adapter) against available inventory and issued three slips: L-402 (PR-04 projector), L-403 (SP-02 speaker), L-404 (AD-12 adapter) — all to Kabir, due Fri 8 pm.

**Phase 2 — Friday 7:30 pm: Partial return**
Kabir returned the projector and speaker. The adapter was still with Leela Das, who would bring it at 9 am Saturday. I recorded returns for L-402 and L-403, leaving L-404 open. I added a handover note: "Leela Das has adapter AD-12 for Film Society RQ-214. Close L-404 when she brings it in Saturday morning."

**Phase 3 — Saturday 9:00 am: Morning handover**
Leela Das walked in with the adapter. The desk book note made it immediately clear which slip to close. I recorded the return for L-404, fully closing the Film Society loan.

---

### What the product handles well

**The approval gate on the loan form.** When I tried to issue an item, the form only listed assets whose type matched the approved request's item list. It was impossible to accidentally hand out the wrong equipment type — a constraint that mirrors how real stores prevent substitution errors. This is a strong safety feature for a high-traffic desk.

*Evidence*: In the loan form, selecting RQ-214 and then choosing an asset automatically constrained choices, and the app refused with a clear status message if the item type fell outside the approved list.

---

### What I would change — and my prototype

**The problem**: The Requests tab showed "Approved" for every request regardless of loan state. At 7:30 pm, with a partial return in progress, I had to switch to the Loan Register to understand what was still out. A desk worker who opens the Requests tab mid-shift gets no signal that RQ-214 is partially returned and L-404 is still open.

**The change**: I added a live loan status badge to each row on the Requests list. The badge shows one of four states derived from the loan register in real time:
- **Not issued** — no slips exist for this request yet
- **On loan** — all items issued, none back
- **Partial return** *(amber)* — some items back, some still out
- **Returned** *(green)* — all issued items have been returned

This is implemented in `app.js` (`requestPage()`) and styled in `styles.css`.

**What I kept**: The form's approval gate is untouched. The request detail view is unchanged.

**Counter observation**: At a real desk, I would watch whether the morning-shift worker looks at the Requests tab or goes straight to the Loan Register when a borrower walks in mid-loan. If they go to Requests first and the badge immediately answers "what is still out," I know the signal is landing in the right place.


## Run the app

Open `index.html` in a modern browser. The app includes its scripts, styles, and icons and can run offline.

To serve it over local HTTP, run this from the repository folder and visit `http://localhost:8000`.

```sh
python3 -m http.server 8000 --bind 127.0.0.1
```

Each browser stores its own sample shift locally when browser storage is available. **Restart sample shift** restores the fictional starting records.

## Source

- `index.html` contains the desk layout, candidate brief, and bundled icons.
- `app.js` contains the sample records and interactions.
- `styles.css` defines the desktop and mobile layouts.

Icon license notices are in [third-party/lucide-LICENSE.txt](third-party/lucide-LICENSE.txt).


## Submit your work

1. [Fork Campus Stores](https://github.com/virinchi-healthcare/campus-stores/fork) into your GitHub account. Complete the candidate brief and push your changes to your public fork. In your README, point reviewers to your work and explain the decision you made.
2. In your fork, open **Commits**, select the final commit you want reviewed, and copy the page URL. It should look like `https://github.com/YOUR-USERNAME/campus-stores/commit/COMMIT-SHA`.
3. [Submit your work through the Google Form](https://docs.google.com/forms/d/e/1FAIpQLScvzoh1R4WS-SkiwAVBQbMvniieJYSoOEfLMyVo5CyjOvYUgQ/viewform). Your **roll number**, **email ID**, and **final commit link from your public fork** are required. Enter your roll number and email ID in the form only.
