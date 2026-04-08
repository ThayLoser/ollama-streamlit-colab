<p align="center">
  <img src="https://raw.githubusercontent.com/gradio-app/gradio/main/guides/assets/logo.png" width="200" alt="Gradio Logo">
</p>

<h1 align="center">Gemma3-4B Gradio Chatbot</h1>

<p align="center">
  <a href="#"><img src="https://img.shields.io/github/stars/ThayLoser/ollama-streamlit-colab?logo=github&color=yellow" alt="Stars"></a>
  <a href="#"><img src="https://img.shields.io/github/forks/ThayLoser/ollama-streamlit-colab?logo=github&color=orange" alt="Forks"></a>
</p>

<p align="center">
  A multimodal educational chatbot running on Google Colab, powered by Ollama and beautifully rendered using Gradio.
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Python">
  <img src="https://img.shields.io/badge/Gradio-FF7C00?style=for-the-badge&logo=gradio&logoColor=white" alt="Gradio">
  <img src="https://img.shields.io/badge/Ollama-000000?style=for-the-badge&logo=ollama&logoColor=white" alt="Ollama">
  <img src="https://img.shields.io/badge/Google_Colab-F9AB00?style=for-the-badge&logo=googlecolab&logoColor=white" alt="Google Colab">
</p>

<br>

## Overview :milky_way:

This repository contains a unified Google Colab Notebook (`.ipynb`) that deploys a fully functional, multimodal web chatbot using Google's **Gemma 3 (4B parameters)**. Instead of requiring complex frontend web development, this version utilizes **Gradio's** highly efficient `ChatInterface` to generate a sleek, interactive UI directly from Python.

This specific project is tailored as an educational assistant for the **Computational Thinking** course at the **University of Science, VNU-HCM**.

> Designed for students and developers who want a rapid, code-light way to experiment with local multimodal LLMs using Python-native UI tools.

At a glance:
- **Zero-Config Setup:** Run entirely inside a browser via Google Colab.
- **Multimodal Support:** Native image and text processing through Gradio.
- **Python-Native UI:** No separate frontend codebase required.

## What makes this different :sparkles:

The point of this project is rapid prototyping and minimal boilerplate. By switching the frontend architecture to Gradio, the application removes the need to write separate file generation scripts or manually manage chat histories and state dictionaries. 

Gradio handles the message history, file uploads, and streaming automatically. The entire infrastructure—from downloading the model via Ollama to launching the public-facing UI—happens seamlessly within a single notebook execution flow.

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
      <strong>🎨 Gradio ChatInterface</strong><br>
      A clean, responsive web interface built directly with Gradio's high-level abstractions. Features native streaming (<code>slow_echo</code>) and history saving.<br><br>
      <code>Auto-History</code> <code>Native Streaming</code> <code>File Uploads</code>
    </td>
  </tr>
  <tr>
    <td width="50%" valign="top">
      <br>
      <strong>⚡ Background Threading</strong><br>
      The Ollama backend server is spun up silently in a Python background thread, preventing the notebook from blocking while the UI boots up.<br><br>
      <code>Subprocess</code> <code>Threading</code>
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
    <td><code>Dependency Install</code></td>
    <td>Installs the required Python libraries: <code>ollama</code> and <code>gradio</code>.</td>
  </tr>
  <tr>
    <td><code>App Launch</code></td>
    <td>Defines the system prompt, formats the Gradio <code>ChatInterface</code>, and launches the UI.</td>
  </tr>
</table>

## Deployment & Usage :hammer_and_wrench:

There is no local environment configuration required. To deploy the chatbot:

1. Open the `.ipynb` file in **Google Colab**.
2. Make sure you are using a runtime with hardware acceleration (Go to *Runtime* > *Change runtime type* > Select **T4 GPU** for optimal speed).
3. Click **Run All** (`Ctrl + F9`).
4. Wait for the model to pull and the environment to install.
5. In the final cell, Gradio will generate a live interface directly inside the notebook, along with a **public Gradio live URL** (if supported by your current Colab session) that you can share with others.

## Project Information :memo:

This project was developed for the **Tư duy tính toán** (Computational Thinking) course at VNUHCM-US. 

- **Developer:** Nguyễn Anh Thái
- **Student ID:** 24120224
- **Group:** CQ2024/2 [N1]

---

<p align="center">
  Made with 💜 using Google Colab & Gradio
</p>
