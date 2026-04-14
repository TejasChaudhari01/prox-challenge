# Prox Founding Engineer Challenge

<img src="product.webp" alt="Vulcan OmniPro 220" width="400" /> <img src="product-inside.webp" alt="Vulcan OmniPro 220 — inside panel" width="400" />

OmniPro 220 Garage Copilot
Multimodal reasoning assistant for the Vulcan OmniPro 220
Project README and evaluator guide
Project	Prox challenge submission
Runtime	Local FastAPI backend + browser UI
API configuration	The Anthropic API key belongs in .env only. .env.example should contain placeholders only. core.py should read the key from environment variables and should not hardcode a secret.

                                          Project summary
This application turns the Vulcan OmniPro 220 manuals into a practical garage-side assistant. It answers technical questions, renders visual artifacts such as setup diagrams and tables, and supports image upload for troubleshooting flows.
The goal is not only correctness, but better technical communication: when a question is easier to understand visually, the app renders a visual artifact instead of replying with text alone.
Core capabilities
Interactive chat interface with artifact workspace.
Polarity and setup diagrams.
Duty-cycle tables and recommended settings cards.
Manual evidence panel with supporting snippets.
Image upload flow for weld-analysis style interactions.
Voice input and output in supported browsers.
                                            
                                              Architecture
The backend uses an agent orchestration flow: core.py retrieves relevant context, planner.py selects tools, tool modules generate structured outputs, and the frontend renders those outputs in an artifact panel.
Tools are responsible for specific output types such as diagrams, tables, settings, evidence, and image galleries.
This separation makes the project easier to maintain and closer to a real product experience than a plain chatbot.
Environment and API key handling
Only .env.example should be committed. It should contain placeholder values such as ANTHROPIC_API_KEY=your_key_here and optionally ANTHROPIC_MODEL=your_model_here.
The real API key belongs in a local .env file that is never committed.
core.py should load environment variables with python-dotenv and read ANTHROPIC_API_KEY from the environment. The key should not appear anywhere in source code.
Recommended run flow

1. Clone the repo and enter the project folder and then unzip the file.
2. Copy .env.example to .env and add the Anthropic API key.
3. Install dependencies with pip install -r requirements.txt.
4. Run ingestion with python -m ingestion.pipeline.
5. Start the backend with python -m uvicorn app.main:app --reload.
6. Open ui/index.html in a browser.
   
Evaluator notes
The app is designed so the evaluator only needs one API key in .env.
If model availability differs by account, ANTHROPIC_MODEL can be changed in .env without changing the code.
The UI demonstrates multimodal behavior through diagrams, tables, evidence blocks, image galleries, and voice controls.
Submission deliverables
Deliverable	Included	Purpose
FastAPI backend	Yes	Serves chat and image endpoints.
Polished browser UI	Yes	Provides chat, artifact rendering, evidence view, upload, and voice controls.
Manual ingestion pipeline	Yes	Parses PDFs into searchable context and extracted images.
Environment placeholder file	Yes	Lets evaluators provide their own Anthropic API key.

Run commands

pip install -r requirements.txt
python -m ingestion.pipeline
python -m uvicorn app.main:app –reload

then open the ui/index.html


