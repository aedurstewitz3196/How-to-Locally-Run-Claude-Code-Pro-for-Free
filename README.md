# How to Locally Run Claude-Code for Free

<h3>Prerequisites</h3>
-Git
-Ollama (Run through the .exe file, the terminal install is so much more work)
(These are in the downloads folder)

<h3>Instructions</h3>
<h4>1. Install Ollama</h4>
-Install Ollama from Ollama.com or Downloads folder
-When added to system path run "Ollama --version" in Windows Powershell to confirm install is completed and working

<h4>2. Install Claude CLI</h4>
-Paste this command into Windows Powershell: "irm https://claude.ai/install.ps1 | iex"
-Fix Path (Crucial): If Claude is not recognized, the installer likely put it in an hidden folder. Add it to your path.
<ul>
  <li>Open Enviormental Variables (search for it in the Start menu)</li>
  <li>Edit your User Path and add: "%USERPROFILE%\.local\bin</li">
  <li>Click "OK" on everything and restart Windows Powershell</li>
</ul>

<h4>3. Download a Coding Model</h4>
You need a model designed for coding to handle Claude's agentic tasks. Qwen 2.5 Coder (specifically the 7B or 32B versions) is the current gold standard for this setup.
<ul>
  <li>Pull the Model: "ollama pull qwen2.5-coder:7b"</li>
</ul>

<h4>4. Permanently Redirect Claude to Ollama</h4>
By default, the Claude CLI tries to connect to Anthropic's servers. You must tell it to look at your local Ollama server (localhost:11434) instead. To make this permanent so you don't have to re-type it every time.
<ul>
  <li>Run: "notepad $PROFILE" in Windows Powershell</li>
  <li>Paste these three lines at the bottom of the file:
    $env:ANTHROPIC_BASE_URL = "http://localhost:11434"
    $env:ANTHROPIC_AUTH_TOKEN = "ollama"
    $env:ANTHROPIC_API_KEY = "ollama"</li>
  <li>Save, exit, and restart Windows PowerShell.</li>
</ul>

<h4>5. Launch Claude Code</h4>
-Navigate to your project folder and start the agent: "claude --model qwen2.5-coder:7b"

<h3>Enjoy!</h3>

