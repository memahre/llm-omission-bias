# Are Large Language Models Sensitive to Omission vs Commission in Moral Evaluation?

This project tests whether large language models exhibit human-like omission bias, defined as the tendency to judge harmful actions (commissions) as more morally wrong than equally harmful failures to act (omissions). Rather than asking models for explicit moral judgments, moral expectation is operationalized here using surprisal to measure how expected a moral evaluation word is given a scenario context.

---

## Key Finding

LLMs do not reproduce the human omission bias. Instead, moral disapproval ("wrong") was more expected following omission scenarios than commission scenarios across models and conditions, which is a reversed pattern compared to human moral judgment. This suggests LLMs rely on statistical co-occurrence patterns in moral language rather than human-like moral reasoning.

---

## Study Design

**Models evaluated:**
- GPT-2, GPT-2-Medium, GPT-2-Large (to test effect of model scale)
- GPT-Neo-125M (to test effect of training data differences)

**Stimulus conditions:**

| Condition | Target Word | Intent Framing |
|---|---|---|
| 1 | "wrong" | None |
| 2 | "wrong" | Explicit ("intentionally" / "failed to") |
| 3 | "acceptable" | None |
| 4 | "acceptable" | Explicit |

**Stimuli:** 14 commission-omission minimal pairs adapted from moral psychology experiments (Spranca et al., 1991; Jamison et al., 2020). Each pair holds knowledge and intent constant, varying only whether the agent acted or failed to act.

**Metric:** Surprisal — the negative log probability of the target word given the sentence prefix. Lower surprisal indicates the word is more expected in context.

---

## Results Summary

- Across three of four conditions, "wrong" was more expected following omissions than commissions, which is opposite to the human pattern
- The "acceptable + intent" condition showed a small reversal, suggesting LLM moral expectations are sensitive to subtle lexical and syntactic differences
- Larger models (GPT-Neo, GPT-2-Large) were the only ones to show higher omission surprisal in the intent conditions, partially mirroring human judgment
- Findings are only descriptive as no formal significance testing was conducted 

---

## Setup and Usage

**Environment:** Runs locally or on Colab. No GPU required.

**Install dependencies:**
```bash
pip install transformers torch pandas matplotlib seaborn numpy tqdm
```

**Run the notebook:**

Open `llm_omission_bias.ipynb` and run cells in order. The notebook loads all four models, computes surprisal across all conditions, and generates visualizations.

**Note:** First run will download model weights from Hugging Face (~1-2GB total). Subsequent runs use cached weights.

---

## Limitations

- Smaller GPT-family models only and results may not generalize to larger modern LLMs
- Single-word moral labels ("wrong", "acceptable") capture word-level expectations rather than deeper moral reasoning
- No formal statistical significance testing
- Surprisal measures prediction, not explicit judgment or belief

---

## References

Baron, J., & Ritov, I. (2004). Omission bias, individual differences, and normality. *Organizational Behavior and Human Decision Processes*, 94(2), 74–85.

Jamison, J., Karlan, D., & Raffler, P. (2020). Aspirational goal setting and moral licensing. *Journal of Economic Behavior & Organization*, 177, 504–521.

Spranca, M., Minsk, E., & Baron, J. (1991). Omission and commission in judgment and choice. *Journal of Experimental Social Psychology*, 27(1), 76–105.
