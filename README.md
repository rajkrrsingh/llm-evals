# llm-evals

How do you know if an LLM's answer is any good? This is a set of hands-on
notebooks that work through the common ways people measure that — each built
from scratch, every formula a small cell you can run and poke at.

They're meant to be read in order. Each one starts where the last hit its
limits, so by the end you understand not just how each metric works, but *when*
to reach for it and where it lets you down.

## The notebooks

1. **[bleu.ipynb](bleu.ipynb)** — counts overlapping word sequences (n-grams).
   Fast and precise, but it only sees exact words, so a good answer worded
   differently scores near zero.
2. **[rouge.ipynb](rouge.ipynb)** — the recall side of the same coin: how much
   of the reference did the answer cover? Still lexical, still blind to
   paraphrase.
3. **[bertscore.ipynb](bertscore.ipynb)** — compares *meaning* using
   embeddings, so synonyms finally count. Rescues the paraphrase case the first
   two fail — but shrugs at word order and negation.
4. **[llm_as_judge.ipynb](llm_as_judge.ipynb)** — let another model grade the
   answer against a rubric. Handles open-ended questions with no single right
   answer, at the cost of the judge's own biases (which we demo and defend
   against).
5. **[g_eval.ipynb](g_eval.ipynb)** — a sharper judge: it writes its own grading
   steps and keeps its uncertainty instead of collapsing to one integer, for
   scores that track humans more closely.
6. **[human_eval.ipynb](human_eval.ipynb)** — the gold standard the rest are all
   approximating. Covers doing it properly: rubrics, multiple annotators,
   agreement, and checking whether your cheap metric actually agrees with people.

## Running them

Sections that matter run on `numpy` and the standard library alone, with
`matplotlib` for the plots. The optional "cross-check" and "real model" cells
use extras (`nltk`, `bert-score`, a local [Ollama](https://ollama.com) server)
and skip cleanly if you don't have them.

```bash
pip install numpy matplotlib
jupyter lab            # or: jupyter notebook
```
