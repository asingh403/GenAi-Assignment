# Feature: Visual Regression Review Service

## Summary

The Visual Regression Review Service is an API-first QA workflow for validating screenshots across two primary use cases: a new feature/page in the current sprint and a regression check against a baseline image. The feature is implemented across the project’s backend services, frontend app, and configurable provider/reporting stack.

## Problem it solves

Teams need a fast, repeatable way to validate UI changes without relying on brittle manual inspection alone. The service helps QA teams detect visual drift, semantic UI issues, and reportable findings using deterministic image comparison plus AI-assisted interpretation.

## Core user flows

### 1) Current Sprint

- User uploads a single screenshot for a new or updated page.
- The system validates the upload and analyzes the image for probable UI issues.
- Results are produced as a normalized comparison result and can be exported as HTML, PDF, or JSON.

### 2) Regression

- User uploads a baseline image and a current image.
- The app supports three review modes:
  - Pixel: deterministic comparison of visual differences
  - Text: semantic comparison of text/UI content
  - Hybrid: combined pixel and text analysis
- The system calculates mismatches, highlights differences, and prepares a report for review.

## Key capabilities

- Deterministic pixel comparison using Resemble.js and Canvas
- Configurable multimodal AI providers for screenshot interpretation and reporting
- Provider fallback strategy between Gemini and OpenAI
- Normalized result model shared by all report types
- Downloadable reports in HTML, PDF, and JSON
- Activity logging for comparison history and provider usage
- Theme and workflow toggles driven by environment configuration

## Implementation structure

- Backend API layer: server/src
- Frontend UI: client/src
- Config and environment flags: .env / .env.example
- Report generation and comparison orchestration: server/src/services/
- Client experience: client/src/pages and client/src/components

## Expected outcome

This feature gives QA and product teams a single workflow for reviewing both new screens and existing page regressions. It combines deterministic validation with AI-assisted explanation so findings are both objective and understandable, while keeping provider selection and report formats configurable for different environments.

## Success criteria

- Current sprint image analysis works with one uploaded screenshot
- Regression checks work for pixel, text, and hybrid modes
- Reports are generated from the same normalized result model
- Provider routing and fallback behavior remain configurable
- Users can review activity history and export reports easily
