---
name: anonimizator-datos
description: Anonymize, pseudonymize, redact, inspect, or prepare sensitive PDF and DOCX documents using the Anonimizator MCP connector without opening their contents in the chat. Use when Codex needs to anonymize a document or folder, review a document for personal data, preserve legal formatting, or remove names, DNI/NIE/CIF, emails, phones, addresses, IBAN, identifiers, health data, minors' data, or other private information before sharing or processing it with another AI.
---

# Anonimizator Datos

## Overview

Use this skill to anonymize sensitive PDF and DOCX files with the Anonimizator connector before they are reused, published, or sent to another AI.

The privacy boundary is strict: never open, extract, quote, summarize, or reproduce the contents of an original document before Anonimizator has processed it. Pass only the file or folder path to the connector and report only its status, counts, warnings, and output paths.

## Connector

- Public entry page: `https://anonimizator.org/conector`

Use the configured Anonimizator MCP connector when it is available in the tool list. Do not print private connector URLs or tokens in user-facing answers.

Expected tools:

- `anonimizar_documento`: anonymize one file.
- `anonimizar_carpeta`: anonymize supported files in a folder.
- `revisar_documento`: detect and count personal data without exposing document contents.

If these tools are unavailable, explain that the connector is not active. Do not read the original as a fallback. Offer manual anonymization only after warning that this would expose the document contents to the current chat and obtaining the user's explicit approval.

## Workflow

1. Ask for or identify the local path to the file or folder. Do not inspect its contents.
2. Determine the requested operation: review, anonymize one document, or anonymize a folder.
3. Call only the corresponding Anonimizator tool with the path and the user's requested options.
4. Preserve dates of events, amounts, procedure numbers, cited laws, courts, facts, legal reasoning, tables, notes, numbering, styles, margins, fonts, seals, and graphical signatures unless the user explicitly asks to remove them.
5. Let Anonimizator replace personal data consistently using the selected mode: label, pseudonym, hash, or real PDF redaction.
6. Report the output path, detected categories and counts, and any residual-data warning returned by the connector. Never reveal original values.
7. Recommend a final professional review because no detector guarantees complete identification of personal data.

## Handling Files

- Treat PDF and DOCX as the connector's primary supported formats, including headers, footers, notes, tables, and numbering.
- For PDF, require real redaction that removes underlying glyphs rather than drawing a recoverable black rectangle.
- For DOCX, preserve the original XML structure and formatting while replacing entities in place.
- Handle names, companies, postal addresses, DNI, NIE, CIF, passports, IBAN, cards, phone numbers, email addresses, Social Security numbers, vehicle registrations, cadastral references, health data, criminal-history data, and minors' data.
- For folders, use `anonimizar_carpeta`; do not enumerate or open each document through the chat.

## Output Guidance

- Keep the final answer concise.
- Do not reveal original sensitive values after anonymization.
- If the connector offers an equivalence spreadsheet, explain that retaining it makes the result pseudonymized rather than irreversibly anonymized; keep the mapping separate and protected.
- Mention the anonymization certificate when returned, including its file hash and processing metadata, without exposing personal data.
- If the user requests maximum privacy, pass stricter options to remove rare contextual combinations while preserving only what is necessary for the intended use.
