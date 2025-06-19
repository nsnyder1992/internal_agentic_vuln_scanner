# 🛡️ LLM-Powered Code Review (Multi-Agent System)
Internal Tool – Proprietary Code Not Publicly Available

## 🔍 Overview
This is an internal AI-powered agent I developed to assist with static code analysis and security reviews. The goal was to augment manual code review with natural language insights and improve detection of insecure patterns, and compliance violations within our custom templating engine. 

## 🧠 Motivation
Our team frequently reviews Java and Python code for potential security issues, but limited bandwidth made deep reviews difficult. I proposed and built an internal tool that leverages a local LLM backend to provide automated summaries, issue detection, and recommendations based on our internal codebase.

## 🔧 Features
- Designed specifically to handle our custom templating language, which traditional SAST tools like Veracode struggled to parse
- Connects to full codebase
- Parses context and provides:
  - Vulnerability summaries
  - Common vulnerability detection (e.g., SQLi, XSS)
  - Highlights risky patterns based on custom rules and OWASP Top 10
  - Offers Fix suggestions in developer-friendly natural language
  - Supports interactive CLI and Cron Job deployment
  - COMMING SOON: git and interactive CI/CD integration

## 🔄 Process Flow

The LLM-powered code review tool follows a multi-stage process designed to scale and streamline secure code review in environments with non-standard templating and constrained on-premise LLM resources.

All LLM interactions are guardrailed through a layered defense: levenshtein distance algorithm, an LLM firewall, and dedicated security agents trained to detect prompt injections, jailbreaks, and other known exploits

### 1. 🧹 Regex-Based Pre-Scan  
Quickly scans for known patterns and our custom template syntax using regular expressions.  
This helps isolate templated code blocks and high-risk constructs that traditional tools like Veracode might overlook.

### 2. 🕵️ Vulnerability Classifier Agent  
Prescanned segments are passed to an LLM-based agent trained to classify potential vulnerabilities  
(e.g., SSRF, LFI, auth bypass) using prompt-engineered logic and OWASP-aligned heuristics.

### 3. 🛠️ Fix Suggestion Agent  
For confirmed or high-confidence issues, a secondary agent proposes secure remediations or refactors,  
embedding inline comments that explain the logic behind the fix — tailored to our stack (Java, Python, etc.).

### 4. 👀 Human-in-the-Loop Review  
Software engineers review both the vulnerability classification and suggested remediations.  
Prompts and outputs are versioned to allow reuse, improve agent prompts, and build a knowledge base over time.

### 5. 📚 Iterative Prompt Tuning  
As reviews accumulate, saved prompts and examples help fine-tune future agent behavior,  
creating a feedback loop that improves accuracy, context awareness, and developer trust.

### 6. ✅ Apply or Save Fixes  
Reviewed fixes can either be directly applied to a working copy or staged for further testing.  
All actions are tracked and saved to ensure auditability and transparency.

### 7. 🧾 Final Save and Completion  
The full session (findings, timestamps, code diffs, user notes) is saved to a local SQLite database  
for traceability, training future agents, or compliance reviews.

## 📊 Results & Impact
- Increased security review coverage by ~40% in sprint cycles
- Encouraged cross-team usage (used by 2+ squads)
- Led to earlier identification of issues like SQLi and XSS Vulnerabilities

## 🛠️ Tech Stack
- Python, LangChain (agent orchestration)
- Local LLM backend (CodeLlama 7B for speed + privacy)
- SQLite for scan history and context caching

## 🔒 Note
This tool is proprietary and not open source, but I’d be happy to discuss the design and development process in an interview setting.
