# Sample data for testing

All names, numbers, GSTINs and references here are made up for testing. They do not belong to any real company.

| File | Use it to test |
|---|---|
| `sample-bank-statement.csv` | Bank & Cash employee: bank reconciliation (BRS) |
| `sample-bank-ledger.csv` | The books side of the same bank account |
| `sample-vendor-bills.csv` | Accounts Payable employee: bill checks (it contains a deliberate duplicate bill, a bill without GRN, and a reused GSTIN to catch) |

Expected findings a good run should report:

- **BRS:** bank charges ₹590 and interest ₹1,250 are in the bank but not in the books; cheque 000124 for ₹7,800 is in the books but not yet in the bank. Adjusted balances should agree at ₹2,51,360 (books ₹2,50,700 + interest ₹1,250 − charges ₹590; bank ₹2,59,160 − unpresented cheque ₹7,800).
- **Vendor bills:** bill DS-501 appears twice (duplicate); FS-09 has no GRN, so it cannot be cleared for payment; Fictional Stationers uses the same GSTIN as Demo Supplies, which needs checking.
