# Database Engineering Lab Assignment Report

## Objective
Implemented change tracking via audit triggers, hierarchical category trees using recursive CTEs, and configured automated versioned migrations and least-privilege security roles.

## Step 2: Audit Log Execution Verification Results
The trigger dynamically captured data mutations inside the `students` table as structured history logs:

| tbl      | op     | was        | now     | at                            |
| -------- | ------ | ---------- | ------- | ----------------------------- |
| students | DELETE | Charlie C. |         | 2026-10-10 12:35:09.486689+00 |
| students | UPDATE | Alice A.   | Kofi M. | 2026-10-10 12:35:09.485864+00 |

## Step 3: Hierarchical Category Tree Verification Results
The recursive CTE walked parent-to-child data nodes and mapped structural indentation matching the relational matrix:

| tree_hierarchy |
| -------------- |
| Electronics    |
|   Computers    |
|   Phones       |
|     Laptops    |

## Step 4 & 5: Production Architecture Projections
* **Flyway Tracking Pipeline:** Migration changes are arranged by sequential alphanumeric prefix strings (`V1`, `V2`, `V3`). Executing `flyway migrate` checks a tracking history state schema map to execute structural adjustments incrementally without manual pipeline interruption.
* **Least Privilege Isolation:** Separate operational accounts are isolated into read-only (`app_read`) and execution data manipulation (`app_write`) roles. This prevents basic query APIs from modifying structure schema trees, mitigating data destruction or injection leaks.

