# Model / API Integration — Scam Message Classifier Prototype

**Internship:** SWYNEX Technologies — Artificial Intelligence Internship
**Task:** Task 2 — Model or API Integration

## What This Is
A working prototype that integrates a TF-IDF + Logistic Regression model (scikit-learn) into the scam-message classification problem defined in Task 1. No external AI API is used — the model is trained and run entirely locally, so there are no API keys involved.

## How It Works
1. A small labeled dataset of SMS-style messages (scam vs. legitimate) is vectorized using TF-IDF (unigrams + bigrams).
2. A Logistic Regression classifier is trained on the vectorized text.
3. For any new message, the model predicts a label (Scam / Legitimate) with a confidence score and a risk level (Low / Medium / High).
4. An explainability layer surfaces the top words that most influenced the prediction, based on the model's learned coefficients for the words present in that specific message.

## Evaluation (held-out test set)
| Metric | Legitimate | Scam |
|---|---|---|
| Precision | 0.75 | 1.00 |
| Recall | 1.00 | 0.67 |
| F1-score | 0.86 | 0.80 |

Overall accuracy: **0.83**

*(Small dataset for prototype purposes — accuracy will improve with a larger, more diverse training set.)*

## Example Inputs and Outputs

**Input:** "Congratulations! You've been selected to receive a free vacation package. Click now to claim."
→ **Prediction:** SCAM (confidence: 0.57) — Flagged words: `click`, `congratulations`, `claim`

**Input:** "Hey, can you send me the notes from today's lecture?"
→ **Prediction:** LEGITIMATE (confidence: 0.52)

**Input:** "URGENT: Your card has been blocked. Verify your PIN immediately at this link."
→ **Prediction:** SCAM (confidence: 0.57) — Flagged words: `verify`, `card`, `immediately`, `link`, `blocked`

**Input:** "Your Zomato order has been delivered. Enjoy your meal!"
→ **Prediction:** LEGITIMATE (confidence: 0.51)

## Files
- `scam_classifier.py` — full training, evaluation, and prediction script

## How to Run
```bash
pip install scikit-learn
python scam_classifier.py
```
