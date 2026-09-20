
# Final Project — Modernize the Sakila DB for a Streaming Service

**Course:** TKIF2203 – Database Technology  
**Instructor:** Dr. Guntur D Putra  
**Due Date:** Thursday, 1 October 2026 at **12.59**  
**Interview:** Thursday, 1 October 2026 from **13.00** till drop.  
**Location**: TBD

## Overview
[Sakila](https://github.com/jOOQ/sakila) is a classic sample database originally designed to model a DVD rental store. For your final project, adapt and extend the Sakila schema to design a relational database for a modern streaming service (video-on-demand). Your design must support streaming‑specific features and include analytics-ready structures for business insights.

This is a capstone: combine data modeling, SQL DDL, and analytics query design, which you should have learned from the Datacamp courses.

> **Note:** This is an **individual project**. Each student must design, build, submit their own deliverables, and attend the final interview.

## Goals
- Map the existing [Sakila schema](https://github.com/jOOQ/sakila) to a streaming domain and justify each change.  
- Add new entities/relationships typical for streaming (user profiles, subscriptions, streaming sessions, episodes, availability windows, content licensing, devices, DRM/licensing metadata, recommendations, watch history, playlists).  
- Design analytics artifacts (aggregated tables, event logs, or schemas suitable for time-series analysis) to support metrics such as plays, session length, retention, churn prediction, and content popularity.  
- Provide SQL DDL for the final schema and example analytic queries.
- You will need to setup your `postgres` environment on your own machine to work on and complete this final project. Please refer to [my quick tutorial](../extras/docker-compose-setup.md) on how to setup a Docker-based `postgres` environment.

## Requirements
1. Mapping (20%):
	- A table-by-table mapping from Sakila to your new schema (what you keep, rename, split, or drop), with a brief justification for each change.  
2. Logical Schema & ERD (20%):
	- Final relational schema (table list with attributes, PKs, FKs, NOT NULL/UNIQUE constraints).  
	- An ERD (Crow's Foot) showing cardinalities and important relationships.  
3. SQL DDL (20%):
	- `CREATE TABLE` statements for all final tables including PKs, FKs, indexes for analytic workloads, and any CHECK constraints.  
4. Analytics Design & Example Queries (20%):
	- At least 6 useful analytics queries (e.g., daily active users, average watch time by content, retention cohort query, top content by region, churn indicator query, recommendation‑ready co‑watch matrix).  
	- If you design summary/aggregate tables or event schemas, include their DDL and an example ETL/aggregation SQL.  
5. Sample Data & Demonstration (10%):
	- Provide sample INSERTs (at least 20 rows spread across key tables) or a small SQL dump that demonstrates your schema and queries.  
6. Write-up & Rationale (10%):
	- A short report (1–2 pages) explaining major design choices, normalization tradeoffs, indexing/partitioning strategy for analytics, and privacy / legal considerations (e.g., data retention, PII minimization).

## Suggested Schema Extensions
You are free to come up with your own ideas for the data analytics purposes. However, you may want to refer to some of these examples below:
- `user_profiles` (multiple profiles per account, parental controls)  
- `subscriptions` (plan, start/end, payment method, status)  
- `devices` (device_id, type, os, last_seen)  
- `streaming_sessions` (session_id, profile_id, content_id, start_ts, end_ts, bitrate, device_id)  
- `content` (movie/series flag), `series`, `episodes` (for episodic content)  
- `content_availability` (region, start_date, end_date, license_id)  
- `content_providers` and `licenses` (rights window, territory)  
- `watch_history` / `play_events` (event-level logs for analytics)  
- `ratings`, `reviews`, `watchlists`, `playlists`  
- `recommendation_metrics` (co_watch counts, item similarity)  
- `ads` and `ad_impressions` (if modelling ad-supported tiers)  
- `transcode_profiles` and `cdn_locations` for delivery metadata

## Example Feature Ideas
From the following examples, pick at least three of them to implement conceptually in your solution:
- Personalized recommendations (collaborative filtering signals stored as co-watch counts).  
- Adaptive bitrate tracking and quality-of-experience metrics (store average bitrate per session).  
- Regional licensing windows and geo-restriction enforcement in availability tables.  
- Offline downloads tracking (device-level entitlements and expiry).  
- Retention/cohort analysis tables and churn prediction features (labels + feature store).  
- A/B testing support (experiment_id, variant, exposure events) to evaluate UI changes and content placements.

Students should also show how the schema supports them (tables, example queries, and an explanation of how data is collected/stored).

## Submission Instructions
- Package your deliverables into a single PDF containing:
    - mapping table
    - ERD image
    - SQL DDL
    - example queries with results (screenshots or sample output), and
    - the short report.
- Include any SQL files or sample dumps as supplementary attachments (ZIP).  
- Submit via eLOK by the due date. Include your name and student ID on the first page.

## Final Interview
Every student will go through a short **3-minute interview session** on **Thursday, 1 October 2026, starting at 13.00**. Location: TBA. Please be aware of the following:
- The interviewers will be the course instructor (GDP) and the teaching assistant (Theo '24).
- Interviews are conducted one-on-one and are mandatory for everyone, not just a random selection.
- You will need your final database implementation ready to query live. Bring a device with you. The interviewers will ask you to run a query or briefly walk through part of your schema on the spot.
- Track your position using the **online queue monitor**: [https://gdputra.dev/tbd-queue](https://gdputra.dev/tbd-queue). The page shows a timer for the ongoing interview and a look-ahead list of the next 10 students, so plan to be nearby once you're within that window.
- Arrive on time. If you miss your turn, you lose all the grades and there will be no make up interview.

### Potential Interview Questions
The interviewers will select a subset of questions from the pool below (not all questions will be asked, and follow-ups may be improvised based on your answers):

**Design & Mapping**
- Which Sakila tables did you keep, rename, split, or drop, and why?
- Walk me through how a `rental` row in Sakila maps to your `streaming_session` (or equivalent) design.
- What was the trickiest modeling decision you made, and what alternatives did you consider?

**Schema & Constraints**
- Point to a foreign key in your schema and explain what business rule it enforces.
- Where did you apply normalization, and is there a place you deliberately denormalized for analytics? Why?
- What would break if you removed a NOT NULL or UNIQUE constraint from a specific column of your choice?

**SQL & Querying**
- Run one of your analytics queries live — explain what it measures and why it's useful to the business.
- How would you modify this query to filter by a specific region or date range?
- Which of your tables would you index first for performance, and why?

**Analytics & Features**
- Which of the three+ streaming features did you implement, and how does your schema support it end-to-end?
- How would you compute churn or retention from your schema? Walk through the tables involved.
- If the business wanted a new metric tomorrow (e.g., "average session length per device type"), how would your schema support that?

**Data & Demonstration**
- Show me a row of sample data and trace it through two related tables.
- If a user deletes their account, which tables are affected, and how does your schema handle that (cascade, soft delete, etc.)?

**Trade-offs & Reflection**
- What privacy or PII consideration did you account for in your design?
- If you had one more week, what would you change or add?
- What's one thing you'd do differently if you started this project over?

### Evaluation Criteria

| Criteria | Description | Points |
|---|---|---|
| Design & Mapping | Your Sakila-to-streaming mapping is correct and justified: you can explain what was kept, renamed, split, or dropped, and defend your key modeling decisions and the alternatives you considered. | 15 |
| Schema & Constraints | Your logical schema is complete and sound: appropriate PKs, FKs, NOT NULL/UNIQUE/CHECK constraints, sensible normalization (with any deliberate denormalization justified), and you can explain the business rule behind each constraint. | 20 |
| SQL & Querying | Your DDL runs and your queries are correct: you can run a query live, explain what it measures, adapt it on the spot (e.g., filter by region or date), and justify your indexing choices. | 15 |
| Analytics & Features | Your schema supports at least three streaming features end-to-end and provides analytics-ready structures; the example queries are useful, and you can show how new metrics such as churn or retention would be computed. | 25 |
| Data & Demonstration | Your sample data (at least 20 rows across key tables) demonstrates the schema and queries, and you can trace records across related tables and explain behavior such as deleting an account. | 10 |
| Trade-offs & Reflection | You can discuss design trade-offs, privacy and PII considerations, and what you would improve or do differently, supported by a clear written report. | 15 |
| **Total** | | **100** |
