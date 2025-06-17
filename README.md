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
