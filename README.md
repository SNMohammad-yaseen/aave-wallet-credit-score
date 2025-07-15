aave-wallet-credit-score
Aave Wallet Credit Score System A rule-based system to assign DeFi credit scores (0-1000) to wallets using Aave V2 transaction data. Includes scoring logic, data pipeline, and analysis of wallet behavior.


Wallet-Based Credit Scoring Project

This project analyzes wallet-level transaction data to assign credit scores based on user behavior. It includes both rule-based scoring and optional extensions like machine learning and clustering.

Files Included

| File                                     | Description                              |
|-------------------------------           |------------------------------------------|
| `user-wallet-transactions.json`          | Input JSON with all wallet transactions |
| `wallet_credit_score_generator.py`       | Rule-based credit score script         |
| `wallet_credit_scores.csv`               | Output file with scores                 |
