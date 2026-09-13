# Buy or Wait? AI-Powered Financial Decision Agent

## Project Overview
This project is a solution for the HackerRank "Buy or Wait?" AI challenge. It is an intelligent financial agent that evaluates whether a user can afford a requested expense by simulating their daily cash flow over a 90-day horizon. 

## Core Logic & Features
* **Data Preprocessing:** Merges 8 separate datasets, normalizes currencies using fixed exchange rates, and handles missing values.
* **OCR Integration:** Uses the `google-genai` SDK and `gemini-3.6-flash` to extract missing transaction amounts from financial receipts (with a manual fallback strategy to gracefully handle free-tier API rate limits).
* **Message Parsing:** Reads user messages to identify and apply transaction cancellations or refunds before running projections.
* **90-Day Cash Flow Simulator:** Projects future daily balances by aggregating historical events, pending transactions, and recurring installments. Ensures the daily balance never drops below the user's strict `minimum_balance_to_keep`.
* **Decision Engine:** Evaluates full payments, partial payments, and installment options. Ranks valid, safe plans based on the strict tie-breaker hierarchy:
  1. Completing on or before the desired date.
  2. Lowest total amount paid.
  3. Earliest start date.
  4. Fewest number of payments.
  5. Lowest option ID.

## Folder Structure
* `code/buy_or_wait_solution.ipynb`: The main notebook containing the pipeline and simulation logic.
* `evaluation/usage_report.md`: Token usage and cost analysis for the Gemini API OCR calls.
* `output.csv`: Final predictions and evaluated decisions for all requests.

## Author
Sapna Rani
