# Project Waterflow

Waterflow is an automation tool for corporate assessment in recurring buy-out workflows.  
It supports the end-to-end process of collecting public market share and corporate bond information, evaluating company health with LLM-assisted analysis, and producing an actionable corporate report for decision-makers.

## Project Goal

Waterflow is designed around this operating model:

1. Collect open market share and corporate bond data.
2. Analyze annual reports (10-K and related materials) to assess corporate health.
3. Apply general private equity style assessment logic to identify opportunities for management soundness improvement.
4. Generate a final report to support buy-out and exit planning decisions.

## Core Features

- **Document ingestion**
  - Upload Annual Reports, 10-K, and supporting documents.
  - Normalize text and metadata for downstream analysis.
- **LLM-based corporate assessment**
  - Connect to **Ollama API**.
  - Use `gpt-oss:20b` (or another supported model) to evaluate business quality, financial soundness, risk, and strategic fit.
- **Automated report generation**
  - Produce a structured report with findings, risk signals, and recommendations.
- **Web application architecture**
  - **Backend:** Flask
  - **Frontend:** Blueprinted HTML templates, CSS, and JavaScript

## Proposed Architecture

```text
[User Uploads Documents]
        |
        v
[Flask Backend]
  - File handling
  - Pipeline orchestration
  - API endpoints
        |
        v
[Analysis Layer]
  - Parsing 10-K / annual report
  - Prompt building
  - Ollama API calls (gpt-oss:20b or alternative)
        |
        v
[Report Generator]
  - Summary
  - Financial/risk highlights
  - Buy-out suitability signals
        |
        v
[Frontend (HTML/CSS/JS)]
  - Input dashboard
  - Analysis status
  - Download/view report
```

## Tech Stack

- **Backend:** Python, Flask
- **Frontend:** HTML templates (Blueprint-style), CSS, JavaScript
- **Model Serving:** Ollama API
- **Default LLM Target:** `gpt-oss:20b`

## Suggested Flask Project Structure

```text
waterflow/
├── app/
│   ├── __init__.py
│   ├── routes/
│   │   ├── upload.py
│   │   ├── analyze.py
│   │   └── report.py
│   ├── services/
│   │   ├── parser_service.py
│   │   ├── ollama_service.py
│   │   └── report_service.py
│   ├── templates/
│   │   ├── base.html
│   │   ├── upload.html
│   │   ├── analysis.html
│   │   └── report.html
│   └── static/
│       ├── css/
│       │   └── style.css
│       └── js/
│           └── app.js
├── uploads/
├── reports/
├── requirements.txt
├── run.py
└── README.md
```

## High-Level Workflow

1. **Upload** Annual report/10-K and related files.
2. **Parse** and segment content into analysis-ready sections.
3. **Evaluate** with Ollama LLM prompts focused on:
   - Financial condition
   - Management quality and governance
   - Market and credit risk
   - Buy-out viability and potential exit paths
4. **Generate** and store a corporate assessment report.
5. **Present** report in web UI and optionally export.

## API Integration Note (Ollama)

Typical configuration fields:

- `OLLAMA_BASE_URL` (e.g., `http://localhost:11434`)
- `OLLAMA_MODEL` (default: `gpt-oss:20b`)
- `OLLAMA_TIMEOUT` (optional request timeout)

## Report Output (Example Sections)

- Executive Summary
- Corporate Profile
- Financial Health Review
- Open Market Share / Bond Position Snapshot
- Risk Assessment
- Value Creation Opportunities
- Buy-out Suitability Score (or tier)
- Recommended Opponents / Exit Scenarios
- Final Recommendation

## Development Roadmap

- [ ] Build Flask app skeleton and blueprints
- [ ] Implement document upload and parser pipeline
- [ ] Integrate Ollama model inference service
- [ ] Add report rendering and export
- [ ] Add authentication/role model (if required)
- [ ] Add testing and evaluation harness

## License

This repository is licensed under the terms in [LICENSE](LICENSE).
