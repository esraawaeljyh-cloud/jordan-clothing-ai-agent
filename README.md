# Jordan Clothing AI Agent (RAG + Memory + Escalation)

This project is an AI customer support agent for an online-only clothing store operating in the Jordanian market.
It answers common questions about orders, delivery, returns, and store policies using Retrieval-Augmented Generation (RAG),
conversation memory, and safety/escalation guardrails.

## Scenario
- Scenario: AI Customer Support Chatbot / Agent (RAG + Memory)
- Target users:
  - Primary: End customers (Arabic-first, English supported)
  - Secondary: Support agents (Agent-Assist summary + suggested replies)

## Key Store Policies (Core Rules)
- Returns are allowed only within 48 hours of delivery.
- Returns are accepted only for: (1) defective item OR (2) unsuitable size.
- Discounted/promotional items are NOT returnable.
- No direct exchange: return first, then reorder.
- Cancellation allowed only before dispatch. No cancellation/refusal once out-for-delivery.
- Delivery inside Jordan only. Delivery time: 2–3 business days. Delivery fee: 2 JOD.

## Repository Structure
- `notebook/`: Main Colab notebook (end-to-end pipeline + demo UI)
- `data/`: Knowledge base CSV (FAQs + policies), and optional dataset samples
- `prompts/`: Prompt versions (v1 → v2 → v3 final)
- `diagrams/`: System architecture diagram
- `outputs/`: Example screenshots/logs (no personal data)

## How to Run (Recommended: Google Colab)
1. Open `notebook/Jordan_Clothing_AI_Agent.ipynb` in Google Colab.
2. Install dependencies (the notebook contains install cells).
3. Add your OpenAI key securely:
   - In Colab: set `OPENAI_API_KEY` as an environment variable (do NOT hardcode).
   - Or locally: create a `.env` file (see `.env.example`) and load it via `python-dotenv`.
4. Run all cells.
5. Launch the Gradio UI cell to chat with the agent.

## Safety & Escalation
The system escalates to human support when:
- Sensitive data is requested (OTP, card details, passwords)
- Out-of-scope topics (medical/legal/financial advice)
- Low intent confidence (classifier uncertainty)
- Weak/no retrieval evidence
- Highly negative tone or repeated unresolved complaints

## Data Sources
- Twitter Customer Support dataset (Kaggle): used for initial exploration/cleaning.
- Store FAQs/Policies adapted from a real clothing e-commerce site, then generalized to fit a Jordanian online clothing store.
  (See report references for citations.)

## Notes on Privacy
- The logging module stores metadata only (timestamp, session_id, intent, policy_triggered, top_score, latency, escalated).
- It does not store full user messages or sensitive identifiers.

## Outputs
See `outputs/` for:
- sample logs (no user text)
- sample screenshots of the UI and policy enforcement

## License
For educational use (course project).
Reproducibility (How to Run the Project)

##This project is fully reproducible using Google Colab.

Requirements
	•	Google account
	•	OpenAI API key (added via Colab Secrets)
	•	Required data files placed in the data/ folder

Required Data Files

The following files must be included in the repository:
	•	data/jordan_clothing_rag.csv
(Jordan Clothing FAQs + store policies used for RAG)
	•	data/swt_questions_tweets.csv
(Questions & tweets dataset from Kaggle used for exploration/cleaning)

Steps to Run
	1.	Open notebook/Jordan_Clothing_AI_Agent.ipynb in Google Colab.
	2.	Run the dependency installation cells.
	3.	Add the API key securely:
	•	Colab → Secrets (🔑) → add OPENAI_API_KEY
	4.	Run all cells from top to bottom.
	5.	Run the final cell to launch the Gradio chat UI.

Notes
	•	The notebook is optimized for Colab execution.
	•	The API key is never hardcoded and is read from environment variables.
	•	If file paths change, update them in the data loading section of the notebook.
