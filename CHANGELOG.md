# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/).

## [1.2.0] - 2026-04-12

### Changed

- **Live Verification** - Rewrote verification section with clearer conditional tiers (MUST/SHOULD/Skip) to prevent over-verification of stable syntax
- **Documentation URL patterns** - Fixed raw GitHub URL patterns to include `-transact-sql.md` suffix matching Microsoft's actual file naming
- **Verification workflow** - Consolidated into a unified 3-step flow: WebFetch → WebSearch fallback → state uncertainty
- **Result handling** - Added "What to Extract" guidance so verified docs are used consistently (syntax, parameters, return type, version, deprecations)

### Removed

- Invalid WebFetch "Prompt" parameter from tool usage instructions

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
