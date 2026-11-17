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

## Installation Process⚒️⚙️ ##
<h1>Installing Ollama </h1>
<p>curl -fsSL https://ollama.com/install.sh</p>
<i>sh ollama pull llama3.2:3b</i> for definition-style tasks, <b>or</b> <i>ollama pull qwen2.5:3b</i> for instruction-based tasks.

<h1>Step 1: Navigate to Your Project Folder</h1>
cd  /Users/your/project/pathway/ollama-dictionary

<h1>Step 2: Check the Folder Contents</h1>
Let's verify what's actually in your project folder and where the virtual environment is:
<p>bash</p>
<p>ls -la</p>

You should see something like:
<ul>
<li>llm_env/ (your virtual environment)</li>
<li>main.py or definition-api.py (your API file)</li>
<li>static/ (your HTML files)</li>
</ul>

<h1>Step 3: Create and activate the Virtual Environment</h1>
<b>Important:</b> The activation command must be on <b>ONE line</b>:
<p>
 bash 
  <ol>
  <li>python3 -m venv llm_env</li>
  <li>source llm_env/bin/activate → On Windows: llm_env\Scripts\activate</li>
  <li>pip install fastapi uvicorn requests</li> 
  </ol>
</p>

After this, your prompt should show (llm_env) at the start.
<p>
<b>Verify it worked:</b>
<p>bash</p>
<p>which python</p>
<p>which uvicorn </p> 
</p>

You should see paths inside llm_env/bin/.

<h1>Step 4: If the Virtual Environment is Missing</h1>
If llm_env doesn't exist, recreate it:
<p>bash: cd /Users/your/project/pathway/ollama-dictionary</p>

<h2>Create virtual environment</h2>
python3 -m venv llm_env

<h2>Activate it</h2>
source llm_env/bin/activate

<h2>Install dependencies</h2>
pip install fastapi uvicorn requests pydantic

<h1>Step 5: Check Your API File Name</h1>
<b>Check what files you have:</b>
bash: ls *.py
<ul>
<il>The file is definition-api.py → use uvicorn definition-api:app --reload <il>
</ul>

<h1>Step 6: Start Ollama (if not already running)</h1>
Check if Ollama is running:
<p>
bash
<p>curl http://localhost:11434/api/tags</p>
</p>
<ul>
  <li><b>If you get a JSON response → Ollama is running; skip to Step 7.</b></li>
  <li><b>If you get "<i>Connection refused</i>" → Start the Ollama Mac/Windows app from Applications, or run ollama   serve in a separate terminal.</b></li>
</ul>

<h1>Step 7: Start the FastAPI Server</h1>
bash: uvicorn definition-api:app --reload --host 0.0.0.0 --port 8000
<p>You should see:</p>
text
<ul>
  <li>INFO:     Uvicorn running on http://0.0.0.0:8000 (Press CTRL+C to quit)
  <li>INFO:     Started reloader process</li>
  <li>INFO:     Application startup complete.</li>
</ul>


<h1>Step 8: Open in Browser</h1>
<ul>
<li>Search page: <a href="http://localhost:8000/static/index.html">http://localhost:8000/static/index.html</a></li>
<li>Saved words: <a href="http://localhost:8000/static/saved_words.html">http://localhost:8000/static/saved_words.html</a></li>
<li>API docs: <a href="http://localhost:8000/docs">http://localhost:8000/docs</a></li>
</ul>


