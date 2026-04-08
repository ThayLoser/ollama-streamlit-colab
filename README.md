<p align="center">
  <img src="https://raw.githubusercontent.com/ollama/ollama/main/docs/ollama.png" width="200" alt="Ollama Logo">
</p>

<h1 align="center">Gemma3-4B Colab Streamlit Chatbot</h1>

<p align="center">
  <a href="#"><img src="https://img.shields.io/github/stars/ThayLoser/ollama-streamlit-colab?logo=github&color=yellow" alt="Stars"></a>
  <a href="#"><img src="https://img.shields.io/github/forks/ThayLoser/ollama-streamlit-colab?logo=github&color=orange" alt="Forks"></a>
</p>

<p align="center">
  A multimodal educational chatbot running on Google Colab, powered by Ollama and Streamlit, tunneled instantly to the web.
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Python">
  <img src="https://img.shields.io/badge/Streamlit-FF4B4B?style=for-the-badge&logo=streamlit&logoColor=white" alt="Streamlit">
  <img src="https://img.shields.io/badge/Ollama-000000?style=for-the-badge&logo=ollama&logoColor=white" alt="Ollama">
  <img src="https://img.shields.io/badge/Google_Colab-F9AB00?style=for-the-badge&logo=googlecolab&logoColor=white" alt="Google Colab">
  <img src="https://img.shields.io/badge/Cloudflare-F38020?style=for-the-badge&logo=cloudflare&logoColor=white" alt="Cloudflare">
</p>

<br>

## Overview :milky_way:

This repository contains a unified Google Colab Notebook (`.ipynb`) that deploys a fully functional, multimodal web chatbot using Google's **Gemma 3 (4B parameters)**. Instead of requiring users to have powerful local GPUs or complex environment setups, it leverages Colab's cloud computing, serves the model locally inside the notebook using Ollama, builds the UI dynamically with Streamlit, and exposes it to the public internet using Cloudflare Tunnels.

This specific project is tailored as an educational assistant for the **Computational Thinking** course at the **University of Science, VNU-HCM**.

> Designed for students and developers who want a quick, transparent, and cost-free way to experiment with local multimodal LLMs on the web.

At a glance:
- **Zero-Config Setup:** Run entirely inside a browser via Google Colab.
- **Multimodal Support:** Process text and image inputs simultaneously.
- **Public URL Generation:** Instant web access through Cloudflare without port-forwarding.

## What makes this different :sparkles:

The point of this project is to eliminate the friction between "local LLM" and "accessible web app." Typically, sharing a local model requires a backend API, a frontend framework, and complex hosting infrastructure. 

By wrapping everything into a single `.ipynb` sequence, the infrastructure becomes invisible. It downloads the model, spins up a background inference server, generates the frontend code (`app.py`) on the fly, and securely tunnels the internal port to a public URL—all within a few code blocks that anyone can inspect and run.

## Feature atlas :rocket:

Rather than treating this like a standard Python script, the notebook acts as a complete deployment pipeline. Here are the major capabilities of the system:

<br>

<table>
  <tr>
    <td width="50%" valign="top">
      <br>
      <strong>🧠 Multimodal Intelligence</strong><br>
      Uses the <code>gemma3:4b</code> model via Ollama. It excels at reasoning, question answering, and can seamlessly analyze uploaded images alongside text prompts.<br><br>
      <code>Text Generation</code> <code>Image Analysis</code> <code>128K Context</code>
    </td>
    <td width="50%" valign="top">
      <br>
      <strong>🎨 Interactive Streamlit UI</strong><br>
      A clean, responsive web interface built directly into the notebook. Features chat sessions, sidebar information, and real-time streaming text.<br><br>
      <code>Chat History</code> <code>Session UUIDs</code> <code>Markdown Rendering</code>
    </td>
  </tr>
  <tr>
    <td width="50%" valign="top">
      <br>
      <strong>🌐 Cloudflare Tunneling</strong><br>
      The app bypasses Colab's restricted networking by establishing an outbound Cloudflare tunnel, granting you a temporary public <code>.trycloudflare.com</code> URL immediately.<br><br>
      <code>Localhost Exposure</code> <code>No Auth Required</code>
    </td>
    <td width="50%" valign="top">
      <br>
      <strong>🎓 Custom Persona</strong><br>
      The chatbot is pre-prompted with a specific system role: A Computational Thinking Lecturer at the University of Science, VNU-HCM. It answers contextually based on this identity.<br><br>
      <code>System Prompts</code> <code>Roleplay</code> <code>Academic Focus</code>
    </td>
  </tr>
</table>

## How the notebook is structured :compass:

The application is encapsulated entirely within standard Jupyter notebook cells. Here is what happens sequentially when you click "Run All":

<table>
  <tr>
    <td><strong>Cell Phase</strong></td>
    <td><strong>Responsibility</strong></td>
  </tr>
  <tr>
    <td><code>System Setup</code></td>
    <td>Installs required system packages (<code>zstd</code>, <code>pciutils</code>) and fetches the Ollama install script.</td>
  </tr>
  <tr>
    <td><code>Background Server</code></td>
    <td>Uses Python's <code>threading</code> to quietly launch <code>ollama serve</code> in the background without blocking the notebook.</td>
  </tr>
  <tr>
    <td><code>Model Pull</code></td>
    <td>Downloads the <strong>Gemma 3 (4B)</strong> model weights directly to the Colab environment.</td>
  </tr>
  <tr>
    <td><code>App Generation</code></td>
    <td>Uses the <code>%%writefile app.py</code> magic command to write the entire Streamlit application logic to disk.</td>
  </tr>
  <tr>
    <td><code>Tunnel & Launch</code></td>
    <td>Downloads <code>cloudflared</code>, runs Streamlit in the background, and establishes the tunnel to output your public Web URL.</td>
  </tr>
</table>

## Deployment & Usage :hammer_and_wrench:

There is no local environment configuration required. To deploy the chatbot:

1. Open the `.ipynb` file in **Google Colab**.
2. Make sure you are using a runtime with hardware acceleration (Go to *Runtime* > *Change runtime type* > Select **T4 GPU** for optimal speed).
3. Click **Run All** (`Ctrl + F9`).
4. Wait for the model to pull and the environment to install (approx. 2-3 minutes).
5. Scroll to the bottom cell. A Cloudflare link (e.g., `https://random-words.trycloudflare.com`) will be printed out. Click it to access your web app!

## Project Information :memo:

This project was developed for the **Tư duy tính toán** (Computational Thinking) course at VNUHCM-US. 

- **Developer:** Nguyễn Anh Thái
- **Student ID:** 24120224
- **Group:** CQ2024/2 [N1]

---

<p align="center">
  Made with 💜 using Google Colab & Ollama
</p>
