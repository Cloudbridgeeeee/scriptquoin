# ScriptQuoin — proposed AWS architecture

ScriptQuoin uses AWS to read screenplays securely, extract structured breakdowns and keep every project confidential — scripts never leave your project space.

## Request flow

1. Screenplay
2. Amazon S3
3. Textract
4. Bedrock
5. DynamoDB
6. Producer review
7. Scene boards

## Services

### Amazon Bedrock

**Role:** Parse scenes and extract resources

Splits screenplays into scenes, classifies them and extracts cast, props, locations, wardrobe and effects — always citing the line each element came from.

### Amazon Textract

**Role:** Read script pages

Extracts text and layout from PDFs and scanned drafts, preserving screenplay formatting such as scene headings, dialogue and action lines.

### Amazon S3

**Role:** Store scripts securely

Keeps every draft encrypted and versioned in a project-specific location, so unreleased scripts stay confidential.

### Amazon DynamoDB

**Role:** Hold scenes and breakdowns

Stores scenes, elements, review edits and draft comparisons for fast access in the breakdown workspace.

### AWS Lambda

**Role:** Run the breakdown pipeline

Orchestrates parsing for each upload, compares new drafts with previous ones and generates planning reports.

## Principles

- **Scripts stay private** — Your scripts are never used to train shared models.
- **Cited elements** — Every tagged element links to its line in the script.
- **Creative untouched** — We organise the script; we never edit it.

## Safeguards

- **Producers approve** — Breakdowns are drafts until your AD or producer approves them.
- **Confidential projects** — Scripts are encrypted, access-controlled per project and never used for training.
- **Estimates, not budgets** — Resource lists support budgeting; final budgets stay with your producers.
- **Line-level evidence** — Every element shows the script line it came from.

## MVP scope

Bring a script in development. We break it down scene by scene, your producer reviews and corrects it, and you receive breakdown reports and scene boards ready for scheduling.

- Screenplay upload and parsing
- Scene classification
- Resource extraction (8 categories)
- Producer review workflow
- Breakdown reports and exports
