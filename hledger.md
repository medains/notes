# HLedger

Hledger is a financial tracking application based on ledger.

## Show data for a quarter

Useful to show the total VAT liability for instance.

```bash
hledger bal -b2018-07-01 -e2018-10-01 -fmain.ledger
```

