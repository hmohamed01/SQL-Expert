# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/).

## [1.1.0] - 2026-02-06

### Added

- **Live Verification** - WebFetch/WebSearch workflow for verifying T-SQL syntax against Microsoft's official GitHub documentation (`MicrosoftDocs/sql-docs`)
- **Documentation Sources** - Raw markdown URL patterns for T-SQL functions, statements, data types, and language elements
- **Verification guidance** - Decision matrix for when verification is required vs. optional
- **Structured Workflows** - Three guided workflows for query development, performance optimization, and security implementation
- **Key Patterns** - Inline quick-reference examples for pagination, running totals, and safe dynamic SQL
- **Documentation Resources** - Links to official SQL Server docs, T-SQL reference, and GitHub raw docs

## [1.0.0] - 2025-05-15

### Added

- Initial skill with SKILL.md and five reference documents
- Query patterns reference (CTEs, pagination, PIVOT, MERGE, window functions, APPLY)
- Performance tuning reference (execution plans, parameter sniffing, Query Store, wait statistics)
- Security reference (SQL injection prevention, dynamic SQL safety, permissions, data masking)
- Data types reference (type selection, collation, precision/scale, storage optimization)
- Transactions reference (isolation levels, deadlock prevention, distributed transactions, sagas)
- README with installation instructions for macOS/Linux/Windows
- Support for SQL Server 2016-2022
