---

abstract: "Large language models (LLMs) are increasingly used to generate data for research. Typical use cases are classifications, annotations, information extraction, and generation of numerical scores. Unlike conventional measurements, LLM outputs can vary across repeated requests even when the prompt and apparent model settings remain unchanged. This variation arises from deliberate sampling, silent model updates, numerical rounding, or expert routing. Setting a dedicated temperature parameter to zero removes deliberate sampling when that option is available, but it does not eliminate the other sources of randomness. Exact reproduction is therefore generally not possible when using proprietary application programming interfaces. Local execution of open-weight models offers greater control, but reproducibility still depends on the complete hardware and software stack. We illustrate these issues through sentiment classifications of corporate filings and examine their consequences for downstream regression results. We then propose a reporting standard for articles and replication packages, as well as guidance for data editors and authors. Together, these findings and recommendations establish that LLM outputs should be treated as draws from a distribution rather than as fixed measurements."

authors:
- Guillaume Coqueret
- Joan Llull
- Florian Oswald
- Christophe Pérignon
- Christoph Scheuch
- Lars Vilhuber
categories: []
date: "2026-07-27"
draft: false
publication: arXiv preprint

publication_types: ["3"]



image:
  caption: Distribution of the t-statistic on the sentiment coefficient across repeated runs, served by API versus run locally
  focal_point: Smart

tags:
- econ
- research
- wip
title: "Randomness in Large Language Models: What Researchers Need to Know (and Report)"

url_pdf: "https://arxiv.org/abs/2607.24372"
url_slides: "/pdf/llm-randomness-slides.pdf"
url_code: ""
url_video: ""
---

Joint with Guillaume Coqueret (EMLYON), Joan Llull (IAE-CSIC and BSE), Christophe Pérignon (HEC Paris), Christoph Scheuch (Humboldt) and Lars Vilhuber (Cornell).

## Status

✅ Preprint available on [arXiv](https://arxiv.org/abs/2607.24372).

## Summary

LLM outputs are draws from a distribution, not fixed measurements. Four sources of non-determinism survive a fixed prompt:

1. **Deliberate sampling** — removable by setting the temperature to zero, where that option is still exposed.
2. **Silent model updates** — the provider swaps the weights behind an unchanged public name.
3. **Numerical rounding** — finite precision arithmetic is not associative, so the order of operations changes the answer.
4. **Expert routing** — in mixture-of-experts models, whether your token reaches its preferred expert can depend on other users' requests.

Only the first disappears at temperature zero. The paper proposes a reporting standard for papers and replication packages, plus verification guidance for data editors.
