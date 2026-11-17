# Ollama-Terminology-Bank-
A small, privacy-first word definition web application powered by a locally running LLM through Ollama.

Enter a word to receive its definition and an example sentence, then save words locally so they can be revisited later.

**Privacy:** The application is designed to run locally. The LLM request is sent to your local Ollama instance rather than a cloud AI API.

**Features**

- 🔍 Look up definitions for words
- ✍️ Generate a short example sentence for each word
- 💾 Save words, meanings and examples locally
- 📖 View a dedicated saved-words page
- 🗑️ Delete individual saved words
- 🧹 Clear the complete saved-word list
- ❤️ Health check for the local Ollama service
- 🔒 No API key or cloud LLM service required
- 📚 FastAPI's automatically generated API documentation

**Technologies Used**

<div class="joplin-table-wrapper"><table><tbody><tr><th><p><strong>Technology</strong></p></th><th><p><strong>Purpose</strong></p></th></tr><tr><td><p>Python 3.10+</p></td><td><p>Application/backend language</p></td></tr><tr><td><p>FastAPI</p></td><td><p>REST API and web server framework</p></td></tr><tr><td><p>Uvicorn</p></td><td><p>ASGI server used to run FastAPI</p></td></tr><tr><td><p>Pydantic</p></td><td><p>Request/response data validation</p></td></tr><tr><td><p>Requests</p></td><td><p>HTTP communication with Ollama</p></td></tr><tr><td><p>Ollama</p></td><td><p>Local LLM runtime</p></td></tr><tr><td><pre><code>llama3.2:3b</code></pre></td><td><p>Local language model used for definitions</p></td></tr><tr><td><p>HTML</p></td><td><p>Frontend structure</p></td></tr><tr><td><p>JavaScript</p></td><td><p>Frontend interaction and API requests</p></td></tr><tr><td><p>JSON</p></td><td><p>Local persistence for saved words</p></td></tr></tbody></table></div>

The original project uses plain HTML and JavaScript rather than a CSS framework. The saved-word data is stored in words_history.json.

<hr> 

##Installation Process##
<h1>Installing Ollama </h1>
curl -fsSL https://ollama.com/install.sh | sh
ollama pull llama3.2:3b for definition-style tasks, <b>or</b> ollama pull qwen2.5:3b for instruction-based tasks.

<h1>Step 1: Navigate to Your Project Folder</h1>
bash
cd /Users/your/project/pathway/ollama-dictionary
<h1>Step 2: Check the Folder Contents</h1>
Let's verify what's actually in your project folder and where the virtual environment is:
bash
ls -la
You should see something like:
<ul>
<li>llm_env/ (your virtual environment)</li>
<li>main.py or definition-api.py (your API file)</li>
<li>static/ (your HTML files)</li>
</ul>

<h1>Step 3: Create and activate the Virtual Environment</h1>
<b>Important:</b> The activation command must be on <b>ONE line</b>:

bash
python3 -m venv llm_env
source llm_env/bin/activate → On Windows: llm_env\Scripts\activate
pip install fastapi uvicorn requests
After this, your prompt should show (llm_env) at the start.
<b>Verify it worked:</b>
bash
which python
which uvicorn
You should see paths inside llm_env/bin/.

<h1>Step 4: If the Virtual Environment is Missing</h1>
If llm_env doesn't exist, recreate it:
bash
cd /Users/your/project/pathway/ollama-dictionary

<h2>Create virtual environment</h2>
python3 -m venv llm_env

<h2>Activate it</h2>
source llm_env/bin/activate

<h2>Install dependencies</h2>
pip install fastapi uvicorn requests pydantic

<h1>Step 5: Check Your API File Name</h1>
Your earlier error said uvicorn definition-api:app, but in the code you shared it was main.py with app = FastAPI(...).
<b>Check what files you have:</b>
bash
ls *.py
<ul>
<il>If the file is main.py → use uvicorn main:app --reload | change ‘main’ to ‘definition-api’<il>
<il>If the file is definition-api.py → rename it (hyphens aren't valid in Python module names): bash</il>
</ul>  mv definition-api.py definition_api.py  Then run: uvicorn definition_api:app --reload

<h1>Step 6: Start Ollama (if not already running)</h1>
Check if Ollama is running:
bash
curl http://localhost:11434/api/tags
<b>If you get a JSON response → Ollama is running; skip to Step 7.</b>
<b>If you get "Connection refused" → Start the Ollama Mac/Windows app from Applications, or run ollama serve in a separate terminal.</b>

<h1>Step 7: Start the FastAPI Server</h1>
bash
uvicorn main:app --reload --host 0.0.0.0 --port 8000
uvicorn definition-api:app --reload --host 0.0.0.0 --port 8000
You should see:
text
INFO:     Uvicorn running on http://0.0.0.0:8000 (Press CTRL+C to quit)
INFO:     Started reloader process
INFO:     Application startup complete.

<h1>Step 8: Open in Browser</h1>
<ul>
<li>Search page: http://localhost:8000/static/index.html </li>
<li>Saved words: http://localhost:8000/static/saved_words.html </li>
<li>API docs: http://localhost:8000/docs </li>
</ul>


