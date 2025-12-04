# LLM Security: Red Teaming vs. Blue Teaming

This project demonstrates the security vulnerabilities of Large Language Models (LLMs) and implements a robust defense pipeline. It uses **TinyLlama-1.1B** as the target model and performs both adversarial attacks (Red Teaming) and defensive filtering (Blue Teaming).

## Project Overview

* **Target Model:** `TinyLlama/TinyLlama-1.1B-Chat-v1.0`
* **Dataset:** `Anthropic/hh-rlhf` (Harmful prompts)
* **Defense Model:** `s-nlp/roberta_toxicity_classifier` & `facebook/roberta-hate-speech-dynabench-r4-target`

## Red Team (Attacks)

Implemented strategies to bypass model safety:
1.  **Adversarial Rewrites:** Using a separate "Attacker LLM" logic to rewrite harmful prompts into hypothetical or theoretical scenarios to trick the model.
2.  **Suffix Injection:** Appending random noise tokens to the prompt to confuse the model's safety alignment.
3.  **Result:** Achieved an Attack Success Rate (ASR) of **25%** against the base model.

## Blue Team (Defense)

Implemented a multi-layered defense pipeline ("Safety Canary"):
1.  **Keyword Filtering:** Regex-based blocking of known threat categories (Critical Harm, Cyber Attack, Jailbreaks).
2.  **Obfuscation Detection:** Normalizing input to catch hidden keywords.
3.  **Semantic Sanitization:** Using a Roberta-based toxicity classifier to detect hostile intent even if keywords are missing.
4.  **LLM Neutralizer:** A system prompt that rewrites requests to be educational/defensive before passing them to the model.
5.  **Result:** Reduced the Attack Success Rate to **~1%**.

## Installation & Usage

1. **Clone the repository:**
   ```bash
   git clone [https://github.com/YOUR_USERNAME/LLM-Security-Red-Blue-Team.git](https://github.com/YOUR_USERNAME/LLM-Security-Red-Blue-Team.git)
   cd LLM-Security-Red-Blue-Team
