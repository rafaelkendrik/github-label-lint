github-label-lint
=================

  Sometimes it is common to make some mistakes while assigning labels to issues, assigning together the ones that shouldn't be or even just forgetting to assign them.

**What it does**:

  - Should checks for existent issues mistakes, like:

    - Unset labels
    - Labels out of context

  - Should receives Github web-hooks, solving labels mistakes and/or sending notifications to an Issue ChatOps.

**Some rules examples**:

  - A issue that not contains a Type label assignment but contains label assignments to Categories, Priorities and Modules:

    ```
    Warning:

    issue-2001      group-not-assigned          Any issue should contains at least one group label assignment.

    Found: no Type assignment
    Expected: Bug|New-feature|Improvement
    ```

  - A Bugs, should be complemented with Priority high or highest:

    ```
    Warning:

    issue-2002      bugs-high-priority          Issues assigned with Bug type label are at least High priority.

    Found: Medium
    Expected: High|Highest
    ```

  - A Module label that references a Category, should be compemented with the same Category label. E.g:

    ```
    Pretend you have an issue that description is something like `A Frontend label, used to ...`
    ```

    ```
    Warning:

    issue-2003      same-reference-category     Modules should be assigned with referenced category label.

    Found: Backend
    Expected: Frontend
    ```

**Config file**:

  - like any other lint, rules can be disabled/enabled.

  - an area to define the used title format for labels:

    - word cases (String): `First letter capitalize`, `lowercase`, etc.
    - group prefix (Bool): e.g `bug` instead of `type: bug`.
    - group separator (String): e.g `-` to `type-bug`

  - future improvement: should possible to extend base patterns (like eslint AirBnb ones).
