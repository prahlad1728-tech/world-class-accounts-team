# Contributing

Thank you for helping build the World Class Accounts Team. Accountants, Chartered Accountants, developers and translators are all welcome.

**Hinglish:** Aap accountant ho, CA ho, developer ho ya translator, sabka swagat hai. Chhota sa sudhaar bhi kaam ka hai.

## Ways to help

| You are | You can |
|---|---|
| **Accountant or CA** | Check the rules in `SKILL.md` against current law, add checks the team should run, report wrong due dates or form numbers |
| **Developer** | Connect the office page to another database (Firebase, Supabase), add an ERP adapter (Tally, Zoho Books, ERPNext), fix bugs in `office/ai-office.html` |
| **Translator** | Add a language to the office page (Gujarati, Marathi, Tamil, Bengali and others) |
| **User** | Run the tests in [TESTING.md](TESTING.md) and open an issue with what happened |

New here? Pick an issue labelled [good first issue](https://github.com/prahlad1728-tech/world-class-accounts-team/labels/good%20first%20issue).

## How to send a change

1. Fork the repo and make a branch.
2. Make your change. Keep the three languages (English, हिंदी, Hinglish) in step when you change text on the office page.
3. Run the relevant tests from [TESTING.md](TESTING.md). For the office page, open it in a browser, run **Watch demo** and switch all three languages.
4. Open a pull request that says what you changed, why, and how you tested it.

No GitHub experience? Open an issue and describe the change in your own words. That helps too.

## Rules that never change

These keep the team safe for real businesses. A pull request that weakens them will not be merged.

- No payment, transfer, external message, ERP posting, master change or return filing without the owner's approval.
- AI employees never type passwords, OTPs, DSC PINs, bank or card numbers.
- Every number comes from a source document. Nothing is guessed.
- Tax rules and due dates come from official sources only, with a link.

## Tax and legal content

Laws change often. When you change a rate, due date, form or section number:

- link the official source (for India: CBIC, GST portal, Income Tax Department, CBDT, MCA, ICAI, RBI, EPFO, ESIC),
- say from which date it applies,
- keep the old rule if it still applies to earlier periods.

## Sample data

Everything in `examples/` must stay made up. Never add real names, GSTINs, PANs, bank details or figures from a real business. Expected test results go in `TESTING.md`, not in `examples/`, so that an AI employee working on the sample files cannot read the answers.

## License

By contributing, you agree that your work is released under the [MIT License](LICENSE) of this project, with credit to the original author kept as the license requires.
