#  Aave Wallet Credit Scoring – README

##  Objective

This script assigns a **credit score (0–1000)** to each wallet based on transaction history on the Aave V2 protocol. Higher scores reflect safer, more responsible behavior (like repaying on time); lower scores indicate risky usage (e.g., frequent liquidations or excessive borrowing).

---

##  Feature Engineering

From the raw JSON transaction log, we compute the following for each `userWallet`:

###  Aggregated Features:
- `deposit_amount`, `borrow_amount`, `repay_amount`, `liquidationcall_count`
- Transaction counts for each action
- `repayment_ratio = total_repay / total_borrow`
- `deposit_borrow_ratio = total_deposit / total_borrow`

###  Why These Features?
- Repayment ratio helps assess how responsibly a user repays debt.
- Frequent liquidations indicate risk or poor collateral management.
- Deposits vs borrow ratio shows conservative vs aggressive usage.

---

### Scoring Logic (Rule-Based Model)

```python
raw_score = (
    (total_deposit * 0.3) +
    (repayment_ratio * 500 * 0.3) +
    (deposit_borrow_ratio * 0.2) -
    (liquidation_count * 100 * 0.2) -
    (total_borrow * 0.1)
)

This raw score is then scaled between 0–1000 using MinMaxScaler.

If there’s no variation in scores, users are assigned a neutral score of 500.
