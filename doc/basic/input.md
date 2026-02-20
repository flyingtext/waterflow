# Input Part Specification

## Purpose
Define how data enters the scaffolding workflow through the **Model–View–Control** structure.

## Model
- Capture incoming entities, attributes, and constraints.
- Validate required fields and enforce type/format rules.
- Persist raw input and normalized input states for traceability.

## View
- Provide user-facing input forms or API request schemas.
- Show mandatory/optional indicators and validation feedback.
- Support draft saving before final submission.

## Control
- Orchestrate input validation and transformation.
- Route valid input to assessment workflow.
- Return actionable errors for invalid input.
