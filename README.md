# 🌐 LLM Agent — Browser-Based Multi-Tool Reasoning

This project is a **proof-of-concept (POC)** for building a **browser-based LLM agent** that can combine **natural language reasoning** with **external tools** like search engines, pipelined APIs, and even **live JavaScript execution**.  

Modern LLM agents aren’t limited to text — they dynamically integrate multiple tools and loop until tasks are solved. This app demonstrates that idea with a **minimal, hackable UI + JavaScript agent core**.

---

## 🚀 Features

✅ **Multi-Provider Model Picker**  
- Choose between different AI providers (OpenAI, Gemini, Claude, custom APIs, etc.).  
- Dynamic dropdown for switching providers & models.  

✅ **Reasoning Loop Agent**  
- Takes user input, queries the LLM, and loops with tool calls until the task is done.  
- Uses **OpenAI-style tool/function calls** for tool invocation.  

✅ **Supported Tools**  
- 🔎 **Search Integration** – Fetch relevant web info.  
- 🔗 **Custom API Proxy** – Flexible AI workflows & pipelines.  
- ⚡ **JavaScript Sandbox** – Execute JS code securely inside the browser.  

✅ **Robust UI/UX**  
- Clean, minimal design.  
- Streaming-style chat window with file upload.  
- Graceful error handling with alerts.  
- Performance monitor & tool action logging for debugging.  

---

## 📋 Project Overview

### Goal
Build a minimal JavaScript-based agent that can:
1. Accept user input in the browser.
2. Query an LLM for reasoning.
3. Dynamically trigger **tool calls** (search, AI workflows, code execution).
4. Loop until the LLM decides no more tools are needed.

### Agent Logic (Conceptual)
```python
def loop(llm):
    msg = [user_input()]
    while True:
        output, tool_calls = llm(msg, tools)
        print("Agent: ", output)
        if tool_calls:
            msg += [handle_tool_call(tc) for tc in tool_calls]
        else:
            msg.append(user_input())
