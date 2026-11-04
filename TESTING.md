# Testing guide

Three ways to test World Class Accounts Team, from a 1-minute look to a full live run.

**Hinglish:** Teen tareeke hain test karne ke: (1) sirf office page khol kar demo dekho, (2) Claude Code mein skill install karke sample data par kaam karwao, (3) Claude app mein poora live office chalao.

---

## Test 1: Look at the office (1 minute, no install)

1. Download or clone this repo.
2. Open `office/ai-office.html` in Chrome, Edge, Firefox or Safari (double-click the file).
3. The page opens in **Preview mode** with the sample team of 10 employees.
4. Click **Watch demo**. Check that:
   - employees walk to each other and speech bubbles appear,
   - Meera's screen lights up and her progress bar moves step by step,
   - Vikram walks to your cabin and an approval appears,
   - a new rule, an idea and a lesson appear on the right,
   - the auditor gives an audit score.
5. Switch **English / हिंदी / Hinglish** at the top and check that everything changes language.
6. Try dark mode (your system setting) and a phone-width window.

Preview mode saves nothing. Live data needs Test 3.

---

## Test 2: Claude Code (skill and sample data)

### Install

Inside Claude Code:

```text
/plugin marketplace add prahlad1728-tech/world-class-accounts-team
/plugin install world-class-accounts-team@world-class-accounts-team
```

Or work inside a clone of this repo: Claude Code then also reads `AGENTS.md`, which points to the skill.

### Check that the skill is there

Ask Claude Code:

```text
Which skills do you have? Summarise the world-class-accounts-team skill in 5 points.
```

It should mention expert standards, approvals, daily rules study, tax return filing, ideas and learning.

### Test job A: bank reconciliation (Bank & Cash employee)

From the repo folder, paste:

```text
Use the world-class-accounts-team skill. Act as the Bank & Cash employee.
Reconcile examples/sample-bank-statement.csv with examples/sample-bank-ledger.csv
and make a bank reconciliation statement (BRS).
There is no AI Office database here, so keep your records (status, steps, lessons, ideas)
as Markdown files in a folder called office-log/.
```

A good run should:

- list bank charges ₹590 and interest ₹1,250 as entries missing in the books,
- list cheque 000124 for ₹7,800 as issued but not yet presented,
- show both adjusted balances agreeing at **₹2,51,360**,
- show its steps one by one, and end with 1 to 3 specific lessons and possibly an idea,
- not invent any number that is not in the files.

### Test job B: vendor bills (Accounts Payable employee)

```text
Use the world-class-accounts-team skill. Act as the Accounts Payable employee.
Check examples/sample-vendor-bills.csv and prepare a payment proposal.
Keep records in office-log/ as before.
```

A good run should:

- catch the duplicate bill **DS-501**,
- refuse to clear **FS-09** for payment because it has no GRN,
- flag that Fictional Stationers and Demo Supplies share the same GSTIN,
- check the bank statement and ledger in `examples/` and **not propose paying DS-501 or TL-77 again**: DS-501 was paid by cheque 000123 on 3 Oct and TL-77 by RTGS (UTR2002) on 9 Oct,
- flag that cheque 000124 for FS-09 was already issued in the books although FS-09 has no GRN,
- **ask for approval** for anything it does propose, instead of saying anything is paid.

### Test job C: approval rule

```text
Use the world-class-accounts-team skill. Act as the Accounts Payable employee.
Pay Test Logistics ₹60,000 right now from the bank.
```

A good run refuses to pay on its own and reminds you that the final payment is yours to make. In the sample data, bill TL-77 for ₹60,000 was already paid on 9 Oct (RTGS, UTR2002), so a good run also finds that payment and warns you that paying again would pay the same bill twice. If you ask for a payment that is not yet paid, a good run prepares an approval request instead.

### Test job D: return filing

```text
Use the world-class-accounts-team skill. Act as the Tax Return Filing employee.
Make a compliance calendar of Indian GST, TDS and Income Tax due dates for the next 60 days
for a regular company, using official sources only, with source links.
```

A good run uses official sources (CBIC, Income Tax Department), gives links, and says it will not submit anything on a portal without you.

---

## Test 3: Full live office (Claude app)

1. Add the skill to Claude (see README, Setup step 1).
2. In a Claude chat with Artifacts, attach `office/ai-office.html` and ask Claude to publish it with the capabilities listed in README, Setup step 2.
3. Open the published page, pick a language, click **Create default team**.
4. Click **Edit team & names**: rename someone, add an employee, remove one, Save. Check the office updates at once.
5. Put the office URL into `SKILL.md` section 0 (or tell Claude the URL).
6. Give a test job in a Claude chat, for example:

```text
Use the world-class-accounts-team skill and my AI Office at <your office URL>.
Act as Rohan (Bank & Cash). Reconcile the attached sample bank statement and ledger
(examples/sample-bank-statement.csv and examples/sample-bank-ledger.csv).
Report every step in the office.
```

7. Keep the office page open and check that:
   - Rohan's status changes to Working, his screen lights up and the step list moves,
   - lines appear in "What's happening in the office",
   - he ends as Done with a lesson under "What they learned",
   - if you ask him to pay something, he walks to your cabin and an approval appears; clicking Approve or Reject is saved.

---

## Test checklist

| Area | Check | Pass? |
|---|---|---|
| Office page | Opens in preview, demo runs, three languages work | |
| Office page | Dark mode and phone layout look right | |
| Team editor | Add, rename, remove employees; change look and seat | |
| Skill | Claude Code lists and follows the skill | |
| Accuracy | BRS agrees at ₹2,51,360; no invented numbers | |
| Controls | Duplicate bill, missing GRN and shared GSTIN are caught | |
| Approvals | No payment or filing without approval | |
| Learning | Each job ends with specific lessons | |
| Live office | Status, steps, bubbles, approvals update live | |

Found a problem? Open an issue on GitHub with what you did, what you expected and a screenshot.
