# In search of the perfect prompt
### Soft and hard prompt strategies for conversational abstract generation

My MSc thesis (October 2023, Master's Programme in ICT Innovation — Human-Computer Interaction and Design major, Aalto University), in industry collaboration with [Iris.AI](https://iris.ai).

**[Read the full thesis (Aaltodoc)](https://aaltodoc.aalto.fi/items/170a001d-4e04-4a82-af04-ba386023ced4)**

The work investigates how two prompting approaches — **soft prompts** (PEFT/LoRA fine-tuning) and **hard prompts** (manually written instructions) — affect the quality of scientific abstracts generated through a **Conversational Recommender System (CRS)**. The study combined LLM fine-tuning with a user evaluation involving academic researchers generating abstracts for their own work.

Supervisor: Lauri Juvela (Aalto) · Thesis advisors: Ronin Wu & Victor Botev (Iris.AI)

## Approach

The CRS is a chat-based system wrapping a fine-tuned LLM (Falcon-7B with LoRA adapters), exposed to users through a Streamlit interface. Six academic participants used it to iteratively generate scientific abstracts. The study measured:

- **Objective:** ROUGE and F1 scores on generated abstracts
- **Subjective:** Cognitive load, response time, and satisfaction during use

## Key findings

- Academic users tended to prefer **fact-focused, Q&A-style interactions** over more expansive conversational ones — challenging a common assumption that more conversational AI is always more useful
- Prompting techniques applied to text generation often produced abstracts that were **broader and less precise** than what users actually wanted — surfacing a real tension between what prompts encourage and what users need
- Customizing prompt strategies to **user preferences and domain demands** was identified as the most important factor for usability

## What's in this repo

### `frontend/` — the CRS

The Streamlit chat application used in the user evaluation study.

| File | What it is |
|---|---|
| `Home.py` | Main Streamlit app |
| `streaming.py` | Token streaming for chat responses |
| `utils.py` | Helper functions |
| `prompts.txt` | Hard prompt templates used in the study |
| `requirements.txt` | Python dependencies |

### `notebooks/` — model fine-tuning

Originally run in Google Colab on T4 GPUs.

| Notebook | What it does |
|---|---|
| `falcon7b_peft_finetuning.ipynb` | Falcon-7B-instruct fine-tuned with PEFT/LoRA in 4-bit quantization on the unarXive scientific papers dataset |

> Note: other model variants (SciBERT, GPT-2) were explored during the thesis but not included in the final user evaluation. They're not in this repo.

## Built with

- **Models:** Falcon-7B-instruct with PEFT/LoRA adapters (Hugging Face `peft` + `transformers`)
- **Quantization:** bitsandbytes (4-bit NF4)
- **Dataset:** [unarXive_citrec](https://huggingface.co/datasets/saier/unarXive_citrec)
- **Frontend:** Streamlit, Python
- **Hardware:** T4 GPU (Google Colab)

## Citation

> Frîncu, I. (2023). *In search of the perfect prompt.* Master's thesis, Aalto University. URN: [NBN:fi:aalto-202310156390](https://urn.fi/URN:NBN:fi:aalto-202310156390)

## Status

Completed October 2023. Kept public as a research artifact — not actively maintained.
