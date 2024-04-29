---
title: NBConvert Pre-commit Hook for Saving Notebook Reports
date: 2024-04-26 14:51:00 +0330
categories: [Tools, Jupyter]
tags: [jupyter, pre-commit, nbconvert]
---

I usually have a `notebooks` directory in my data science project repositories that contains my whole analysis and experimentations in jupyter notebook format (checkout my [mlproject template](https://github.com/arashabzd/mlproject)). I try to keep my notebooks clean, relatively short and with one purpose to avoid having gigantic notebooks that even myself can't understand.

Notebooks are hard to track in git since they contain outputs that makes git diffs imposible. One solution is to clear outputs before commiting changes. This can easily be done using a `pre-commit` hook that runs `jupyter nbconvert --clear-output` on all notebooks.

The main problem that I have with this solution is that you lose all of your analysis results that might be useful to you later and is the basis of the decisions you made in that project. You may need to report those to someone later so it makes sense to keep track of the outputs somewhere. Ok, so lets add another `pre-commit` hook to export notebook outputs to an accessible format before crearing the output (`jupyter nbconvert --no-prompt --to markdowon` can the job).

There is a problem with this again. Let's say you made a new notebook and want to make your commit. In the first step of pre-commit you export your notebook outputs, then in the second step you clear the output. Pre-commit fails since your notebook file has been overwritten with a notebook with no outputs. You stash your notebook again and make your commit and done. Your exported report will have nothing in it since it ran again and overwrote the previous one!

I wrote a simple `pre-commit` hook to solve this issue. The way it works is that if the notebook is already cleared out, it wont export it again, so no overwriting will happen. I put it in this repo [pre-commit-nbconvert](https://github.com/arashabzd/pre-commit-nbconvert).

You can add it to your project by adding the following to your `.pre-commit-config.yaml` file:

```yaml
-   repo: https://github.com/arashabzd/pre-commit-nbconvert
    rev: "0.0.2"
    hooks:
    -   id: convert-notebooks
        args: [--format=markdown, --output-dir=reports]
    -   id: clear-notebook-outputs
```

If you want to export to `pdf` format you need to install `pandoc` and `texlive` (refer to installation instructions in [pre-commit-nbconvert](https://github.com/arashabzd/pre-commit-nbconvert))

That's about it.
