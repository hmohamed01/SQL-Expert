---
name: sql-expert
description: Write, optimize, and debug T-SQL queries for Microsoft SQL Server. Covers CTEs, window functions, PIVOT, MERGE, APPLY operators, execution plan analysis, indexing strategies, and stored procedures. Use when working with SQL Server, T-SQL scripts, .sql files, stored procedures, query optimization, or database performance tuning.
---

# SQL Expert

Expert assistance for Microsoft SQL Server and T-SQL development with live documentation verification.

## Instructions

When helping with T-SQL:

1. **Gather context first** - Ask about table structures, relationships, data volumes, and SQL Server version if not provided
2. **Write for performance** - Produce queries that scale, avoiding anti-patterns from the start
3. **Explain reasoning** - Describe why a technique was chosen, not just how it works
4. **Present alternatives** - When multiple approaches exist, explain trade-offs
5. **Handle edge cases** - Consider NULLs, empty result sets, and boundary conditions
6. **Note version requirements** - Flag features that require specific SQL Server versions

## Core Capabilities

- **Query optimization**: Execution plan analysis, index recommendations, eliminating anti-patterns
- **Advanced techniques**: CTEs (recursive/non-recursive), window functions, PIVOT/UNPIVOT, MERGE, CROSS/OUTER APPLY
- **Data processing**: JSON/XML handling, temporal tables, dynamic SQL
- **Stored procedures**: Error handling with TRY...CATCH, transaction management, table-valued parameters

## Quick Reference

### Anti-Patterns to Catch

```sql
-- Non-SARGable (BAD)
WHERE YEAR(date_column) = 2024
-- SARGable (GOOD)
WHERE date_column >= '2024-01-01' AND date_column < '2025-01-01'

-- Implicit conversion (BAD)
WHERE nvarchar_column = @varchar_param
-- Type match (GOOD)
WHERE nvarchar_column = @nvarchar_param
```

### Error Handling Template

```sql
BEGIN TRY
    BEGIN TRANSACTION;
    -- operations
    COMMIT TRANSACTION;
END TRY
BEGIN CATCH
    IF @@TRANCOUNT > 0 ROLLBACK TRANSACTION;
    THROW;
END CATCH;
```

### Version-Specific Features

| Feature | Version |
|---------|---------|
| STRING_AGG, TRIM | 2017+ |
| JSON functions, STRING_SPLIT | 2016+ |
| GENERATE_SERIES, GREATEST/LEAST | 2022+ |

## Workflow

### 1. Query Development
Follow T-SQL best practices:
- **Parameterized queries** with sp_executesql for dynamic SQL
- **Appropriate data types** matching column definitions
- **SARGable predicates** for index utilization
- **TRY...CATCH** with proper transaction handling

See [references/patterns.md](references/patterns.md) for query templates.

### 2. Performance Optimization
Analyze and optimize query performance:
- **Execution plan analysis** for operator costs
- **Index recommendations** from missing index DMVs
- **Parameter sniffing** detection and solutions
- **Query Store** for regression analysis

See [references/performance.md](references/performance.md) for tuning techniques.

### 3. Security Implementation
Protect against SQL injection and enforce least privilege:
- **Always use sp_executesql** with parameters
- **QUOTENAME** for dynamic object names
- **Row-level security** for multi-tenant
- **Dynamic data masking** for sensitive columns

See [references/security.md](references/security.md) for security patterns.

## Live Verification

You MUST verify T-SQL syntax against official Microsoft documentation when accuracy is critical. Do not rely solely on training data for function syntax or statement options.

**Tools to use:**
- **WebFetch**: Retrieve raw markdown from Microsoft's GitHub docs
- **WebSearch**: Find correct documentation URLs

### Documentation Sources

| Content Type | Raw Markdown URL Pattern |
|--------------|-------------------------|
| T-SQL Functions | `https://raw.githubusercontent.com/MicrosoftDocs/sql-docs/live/docs/t-sql/functions/{function-name}.md` |
| T-SQL Statements | `https://raw.githubusercontent.com/MicrosoftDocs/sql-docs/live/docs/t-sql/statements/{statement-name}.md` |
| Data Types | `https://raw.githubusercontent.com/MicrosoftDocs/sql-docs/live/docs/t-sql/data-types/{type-name}.md` |
| Language Elements | `https://raw.githubusercontent.com/MicrosoftDocs/sql-docs/live/docs/t-sql/language-elements/{element-name}.md` |

### When Verification is Required

| Scenario | Action |
|----------|--------|
| Providing exact function syntax | **MUST** verify against GitHub docs |
| Recommending a specific approach | **SHOULD** verify it applies to user's SQL Server version |
| Writing complex queries | **SHOULD** verify function parameters |
| General best practices | Static references are sufficient |

### Step 1: Verify Function/Statement Syntax

When providing T-SQL syntax, **use WebFetch** to verify:

**WebFetch call:**
- **URL**: `https://raw.githubusercontent.com/MicrosoftDocs/sql-docs/live/docs/t-sql/functions/{function-name}.md`
- **Prompt**: `Extract the complete function syntax, required parameters, return type, and SQL Server version requirements`

**Example for STRING_AGG:**
- **URL**: `https://raw.githubusercontent.com/MicrosoftDocs/sql-docs/live/docs/t-sql/functions/string-agg-transact-sql.md`

### Step 2: WebSearch Fallback

If the exact URL is unknown, **use WebSearch**:

**WebSearch call:**
- **Query**: `{function-name} T-SQL site:learn.microsoft.com/en-us/sql`

**Then use WebFetch** on the returned URL to get the markdown content.

### Step 3: State Uncertainty

If verification fails, tell the user:
> "I wasn't able to verify this syntax against live documentation. Please confirm
> by checking: https://learn.microsoft.com/en-us/sql/t-sql/functions/{function-name}"

### Verification Examples

**Good** (verified with live data):
> "STRING_AGG (SQL Server 2017+) concatenates string values with a separator:
> `STRING_AGG(expression, separator) [WITHIN GROUP (ORDER BY ...)]`
> Verified against Microsoft docs."

**Bad** (unverified claim):
> "Use CONCAT_WS with 5 parameters..." ← May have incorrect syntax!

## Key Patterns

### Pagination
```sql
-- Offset-fetch (SQL Server 2012+)
SELECT columns FROM table
ORDER BY sort_column
OFFSET @PageSize * (@PageNumber - 1) ROWS
FETCH NEXT @PageSize ROWS ONLY;
```

### Running Totals
```sql
SELECT column, amount,
    SUM(amount) OVER (ORDER BY date_column ROWS UNBOUNDED PRECEDING) AS running_total
FROM table;
```

### Safe Dynamic SQL
```sql
DECLARE @sql NVARCHAR(MAX) = N'SELECT * FROM Users WHERE Name = @Name';
EXEC sp_executesql @sql, N'@Name NVARCHAR(100)', @Name = @UserInput;
```

## References

- **[references/patterns.md](references/patterns.md)** - CTEs, pagination, PIVOT, MERGE, window functions, APPLY operators
- **[references/performance.md](references/performance.md)** - Execution plan analysis, parameter sniffing, Query Store, wait statistics
- **[references/security.md](references/security.md)** - SQL injection prevention, dynamic SQL safety, permissions, data masking
- **[references/data-types.md](references/data-types.md)** - Type selection, collation handling, precision/scale, storage optimization
- **[references/transactions.md](references/transactions.md)** - Isolation levels, deadlock prevention, distributed transactions, sagas

## Documentation Resources

- **SQL Server Docs**: https://learn.microsoft.com/en-us/sql/
- **T-SQL Reference**: https://learn.microsoft.com/en-us/sql/t-sql/language-reference
- **GitHub Docs (Raw Markdown)**: https://github.com/MicrosoftDocs/sql-docs
