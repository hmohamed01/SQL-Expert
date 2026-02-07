# SQL Expert

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![SQL Server](https://img.shields.io/badge/SQL%20Server-2016--2022-CC2927.svg)](https://www.microsoft.com/sql-server)
[![Claude Code](https://img.shields.io/badge/Claude%20Code-Skill-blueviolet.svg)](https://claude.ai/code)

A Claude Code skill for Microsoft SQL Server and T-SQL development expertise.

## Overview

This skill provides guidance for writing, optimizing, and debugging T-SQL queries. It covers advanced querying techniques, performance tuning, security best practices, and transaction management.

## Features

- **Live Documentation Verification** - Verifies T-SQL syntax against Microsoft's official [sql-docs](https://github.com/MicrosoftDocs/sql-docs) repository using WebFetch, with WebSearch fallback when exact URLs are unknown
- **Structured Workflows** - Guided workflows for query development, performance optimization, and security implementation
- **Quick-Reference Patterns** - Inline examples for common tasks like pagination, running totals, and safe dynamic SQL
- **Anti-Pattern Detection** - Catches non-SARGable predicates, implicit conversions, and other performance pitfalls
- **Comprehensive References** - Five detailed reference docs covering query patterns, performance tuning, security, data types, and transactions

## Installation

Clone this repository, then copy the `sql-expert` folder to your skills directory:

### User-level (all projects)

**macOS/Linux:**
```bash
cp -r sql-expert ~/.claude/skills/
```

**Windows (PowerShell):**
```powershell
Copy-Item -Recurse sql-expert $HOME\.claude\skills\
```

### Project-level (current project only)

**macOS/Linux:**
```bash
cp -r sql-expert .claude/skills/
```

**Windows (PowerShell):**
```powershell
Copy-Item -Recurse sql-expert .claude\skills\
```

## Repository Structure

```
SQL-Expert/
├── README.md
└── sql-expert/                   # <- Copy this folder to your skills directory
    ├── SKILL.md                  # Main skill definition with core instructions
    └── references/
        ├── patterns.md           # Query patterns: CTEs, pagination, PIVOT, MERGE, window functions
        ├── performance.md        # Execution plans, parameter sniffing, Query Store, wait statistics
        ├── security.md           # SQL injection prevention, dynamic SQL, permissions, data masking
        ├── data-types.md         # Type selection, collation, precision/scale, storage optimization
        └── transactions.md       # Isolation levels, deadlocks, distributed transactions, sagas
```

## Usage

Once installed, Claude Code will automatically use this skill when you ask about:
- T-SQL query writing or optimization
- SQL Server stored procedures
- Database performance tuning
- Query execution plans
- SQL security and injection prevention

## SQL Server Version Support

The skill covers features from SQL Server 2016 through 2022, with version annotations where applicable.

## License

MIT
