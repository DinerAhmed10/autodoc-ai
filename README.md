wjdiwjdwideAutoDoc-AI
A tool that uses AI to generate documentation. Reads any project's code and spits out README, API docs, CHANGELOG — the whole thing.
What it does
Auto-generates README
API docs for every function, class, method
CHANGELOG template
CONTRIBUTING guide
Adds inline comments to source files
Output as Markdown, HTML, or JSON
Supports 16+ languages
Skips node_modules, pycache, build dirs, etc.
Dry-run mode — preview before writing anything
Supported Languages
Language
Extension
Python
.py
JavaScript
.js, .jsx
TypeScript
.ts, .tsx
Go
.go
Rust
.rs
Java
.java
C / C++
.c, .cpp
C#
.cs
Ruby
.rb
PHP
.php
Swift
.swift
Kotlin
.kt
Scala
.scala
Bash
.sh
R
.r
Installation
Needs Python 3.9+ and an Anthropic API key.
pip install autodoc-ai
Or from source:
git clone https://github.com/yourusername/autodoc-ai.git
cd autodoc-ai
pip install -e .
Quick Start
export ANTHROPIC_API_KEY=your-api-key

# Generate docs for current directory
autodoc .
Markdown files land in ./docs/.
Usage
Basic
# Document a specific folder
autodoc ./my-project

# Custom output directory
autodoc . --output ./documentation
Output Formats
autodoc . --format markdown   # default
autodoc . --format html       # HTML site with index
autodoc . --format json       # single JSON file
Selective Generation
autodoc . --readme-only       # only README
autodoc . --comments          # add inline comments to source
autodoc . --lang python       # force language detection
autodoc . --dry-run           # preview, no files written
autodoc . --verbose           # show scanned files
autodoc . --model claude-opus-4-5-20251101
autodoc . --api-key sk-ant-...
CLI Reference
Argument
Short
Default
Description
path
—
.
Project directory to document
--output
-o
./docs
Output directory
--format
-f
markdown
markdown / html / json
--lang
-l
auto
Force language detection
--readme-only
—
false
Generate only README
--comments
—
false
Add inline comments
--api-key
—
env var
Anthropic API key
--model
—
claude-opus-4-5-20251101
Claude model to use
--verbose
-v
false
Show detailed scan output
--dry-run
—
false
Preview without writing files
Output Structure
Markdown (default)
docs/
├── README.md
├── API.md
├── CHANGELOG.md
├── CONTRIBUTING.md
└── commented/          # only with --comments
    ├── main.py
    └── utils.py
HTML
docs/
├── index.html
├── README.html
├── API.html
├── CHANGELOG.html
└── CONTRIBUTING.html
JSON
docs/
└── docs.json
How It Works
1. Scan — CodeScanner walks the directory, reads source files, detects language, grabs metadata. Capped at 100KB per file.
2. Generate — DocGenerator sends code summaries to Claude API, gets docs back. Separate API call for each doc type.
3. Write — DocWriter saves files, converts Markdown to HTML with an index page if needed.
API Key Setup
Reads from environment variable:
# Linux / macOS
export ANTHROPIC_API_KEY=sk-ant-...

# Windows PowerShell
$env:ANTHROPIC_API_KEY = "sk-ant-..."

# Or pass per run
autodoc . --api-key sk-ant-...
Get a key at console.anthropic.com
Running Tests
pip install pytest
pytest tests/ -v
Tests cover scanner, writer (all three formats), and a full end-to-end flow — no real API calls.
Contributing
PRs welcome. Run tests before submitting.
git clone https://github.com/yourusername/autodoc-ai.git
cd autodoc-ai
pip install -e .
pytest tests/ -v
License
MIT © AutoDoc-AI Contributors
hello 
