# humant

Human Access Orchestrator

Automated onboarding & offboarding for modern teams

1. Problem Statement

Onboarding and offboarding employees in modern companies is fundamentally broken.

Most companies today use between 10 and 40 SaaS tools, including:

Google Workspace

Slack

GitHub

Notion

Jira

Linear

Figma

Cloud providers

Internal dashboards

When a new person joins, someone must manually:

Create accounts in every system

Assign the correct permissions

Add them to the right groups

Remember what a “developer” or “designer” needs

When someone leaves, someone must:

Revoke access everywhere

Hope nothing is forgotten

Trust that security risks are handled

This process is:

Manual

Error-prone

Time-consuming

A major security risk

At small scale it is annoying.
At medium scale it becomes chaotic.
At larger scale it becomes dangerous.

2. Existing Solutions & Gaps
Enterprise IAM (Okta, Azure AD, JumpCloud)

Heavy setup

Expensive

Overkill for startups and SMBs

Poor UX

Complex mental model

HR Platforms (Rippling, Deel, BambooHR)

HR-first, not engineering-first

Limited SaaS coverage

Black-box automation

Slow integrations

Internal Scripts

Everyone builds them

They break

No UI

No audit

No ownership

No maintainability

There is a massive gap between:

Manual chaos
and
Enterprise IAM systems

3. Product Vision

Human Access Orchestrator is a single source of truth for the entire human → SaaS access lifecycle.

It automates:

Onboarding

Role-based access

Offboarding

Auditing

Visibility

Think of it as:

Terraform for human access
Or
Infrastructure as code, but for people

4. Core Concepts
User

A real human joining or leaving the company.

{
  "name": "Jane Doe",
  "email": "jane@company.com",
  "role": "Backend Developer",
  "start_date": "2026-03-01",
  "end_date": null
}

Role Template

A role defines what access someone should have.

Example: Backend Developer

Contains:

Google groups

Slack channels

GitHub org + teams

Notion workspace

Jira roles

Linear teams

Cloud permissions

Plugin

Each SaaS integration is a plugin.

Every plugin implements:

interface SaaSPlugin {
  name: string
  connect(auth)
  createUser(user, template)
  assignPermissions(user, template)
  disableUser(user)
  audit(user)
}

Lifecycle Engine

The system that executes actions.

On start_date → provision

On end_date → deprovision

Manual trigger available

Full audit log

5. Core Features
Onboarding Automation

Create a user once.
The system provisions them everywhere.

Offboarding Automation

Disable a user once.
The system revokes access everywhere.

Role-Based Access

Roles define access, not individuals.

Scheduling

Pre-schedule onboarding and offboarding.

Audit Log

Full history of:

Who was created

Where

When

By which plugin

Visibility Dashboard

Answer questions like:

Who has access to what?

Which tools does this person have?

Which roles are over-permissioned?

6. Plugin Architecture (Key Differentiator)

The entire system is built around plugins.

Core system:

Users

Roles

Lifecycle

Audit

UI

Everything else:

External plugins

This allows:

Community-built integrations

Internal company plugins

MSP / agency plugins

Enterprise connectors

The product becomes:

A platform, not just a tool.

7. MVP Scope

A realistic, sellable MVP:

Core

User management

Role templates

Scheduling

Audit log

Web UI

Initial Plugins

Google Workspace

Slack

GitHub

This already solves ~70% of the problem for tech teams.

8. Ideal Customer Profile

Primary:

Startups (10–200 people)

Tech companies

Remote-first teams

Agencies

Secondary:

MSPs

Consultancies

Security teams

9. Pricing Logic

This is infrastructure software.

Strong pricing characteristics:

High retention

Low churn

Critical system

Clear ROI

Possible pricing:

€20–€50 / month (small teams)

€100–€300 / month (growing teams)

Usage-based per active user

10. Strongest Value Proposition

Everyone sells onboarding.

Offboarding is the real killer feature.

Main homepage line:

Never forget to revoke access again.

This speaks directly to:

Founders

CTOs

Security officers

Auditors

Compliance teams

11. Expansion Opportunities

Once data exists:

You can build:

Access intelligence

SaaS usage analytics

License optimization

Security posture reports

SOC2 / ISO27001 automation

At that point the product evolves into:

Access Intelligence Platform

12. Strategic Advantages

This idea has:

Real pain

High frequency usage

High impact

High willingness to pay

Clear MVP

Natural upsell path

Strong platform effects

Strong community potential

Extremely defensible

13. Why This Works Now

This problem is accelerating because:

SaaS sprawl is exploding

Remote work is default

Zero Trust is mainstream

Compliance pressure is rising

AI tools add even more accounts

The problem is getting worse every year.

14. Summary

Human Access Orchestrator is not a tool.
It is infrastructure.

It replaces:

Spreadsheets

Checklists

Scripts

Tribal knowledge

Human memory

With:

Automation

Roles

Audit

Security

Visibility

It is Terraform for people.
