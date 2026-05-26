```markdown
# redis Development Patterns

> Auto-generated skill from repository analysis

## Overview

This skill teaches you the core development patterns and workflows used in the `redis` codebase, a high-performance in-memory data store. You'll learn about the repository's coding conventions, how to implement new features, fix bugs, update configurations, improve documentation, manage dependencies, and maintain the test infrastructure. Each workflow is documented with clear step-by-step instructions and practical examples to help you contribute effectively.

## Coding Conventions

- **File Naming:**  
  Use `snake_case` for file names.  
  _Example:_  
  ```
  redis_server.py
  config_parser.py
  ```

- **Import Style:**  
  Use relative imports within modules.  
  _Example:_  
  ```python
  from .utils import parse_config
  from .models import RedisCommand
  ```

- **Export Style:**  
  Use named exports (explicitly listing what is exported).  
  _Example:_  
  ```python
  __all__ = ['RedisServer', 'ConfigParser']
  ```

- **Commit Messages:**  
  Freeform style, typically around 64 characters.

## Workflows

### Feature Implementation with API and Tests
**Trigger:** When adding a new feature or API to Redis core or modules  
**Command:** `/new-feature-api`

1. Update or add implementation files in `src/` (e.g., `.c`, `.h`).
2. Update or add related header files in `src/`.
3. Update or add test files in `tests/unit/` or `tests/modules/`.
4. Update `Makefile` or test infrastructure if new tests or modules are added.

_Example:_
```c
// src/newfeature.c
void NewFeature() {
    // Implementation
}
```
```tcl
# tests/unit/newfeature.tcl
test {New feature works as expected} {
    # test logic
}
```

---

### Config or Command Addition or Change
**Trigger:** When adding or modifying a configuration option or command  
**Command:** `/change-config-command`

1. Update implementation in `src/config.c`, `src/server.c`, or related files.
2. Update `redis.conf` and/or `tests/assets/default.conf`.
3. Update or add related header files.
4. Update or add tests in `tests/unit/` or `tests/integration/`.
5. Update documentation/comments in code.

_Example:_
```c
// src/config.c
addConfigOption("my-new-option", ...);
```
```conf
# redis.conf
my-new-option yes
```

---

### Bugfix with Test
**Trigger:** When fixing a bug and preventing regressions  
**Command:** `/bugfix-with-test`

1. Fix the bug in `src/*.c` or `src/*.h`.
2. Update or add a test in `tests/unit/` or `tests/integration/` to cover the bug scenario.

_Example:_
```c
// src/server.c
if (ptr == NULL) return ERROR_NULL_POINTER;
```
```tcl
# tests/unit/bugfix.tcl
test {Bug is fixed} {
    # test logic
}
```

---

### Documentation or Comment Improvement
**Trigger:** When clarifying code or updating documentation  
**Command:** `/improve-docs-comments`

1. Edit or add comments in `src/*.c` or `src/*.h`.
2. Update documentation files or scripts in `utils/` or `docs/`.
3. Optionally update related test comments.

_Example:_
```c
// src/server.c
/* This function handles client disconnection logic */
void disconnectClient() { ... }
```
```md
# docs/new_feature.md
This document describes the new feature...
```

---

### Third-Party Dependency Upgrade
**Trigger:** When bumping or updating a third-party dependency  
**Command:** `/upgrade-dependency`

1. Update files in `deps/<dependency>/`.
2. Update related documentation (e.g., `deps/README.md`).
3. Update `Makefile` or build scripts if needed.
4. Update `src/` files if integration points change.

_Example:_
```diff
- deps/hiredis/hiredis.c (updated)
- deps/README.md (document new version)
```

---

### Test Infrastructure or Skip Tag Update
**Trigger:** When adjusting test running conditions or infrastructure  
**Command:** `/update-test-infra`

1. Update or add skip tags in `tests/unit/*.tcl` or `tests/integration/*.tcl`.
2. Update test helper scripts in `tests/support/` or `tests/test_helper.tcl`.
3. Update `Makefile` or test runner scripts if needed.

_Example:_
```tcl
# tests/unit/example.tcl
test {This test is skipped on Windows} {
    tags {skip:windows}
    # test logic
}
```

## Testing Patterns

- **Framework:** Unknown (tests are mainly `.tcl` scripts).
- **File Pattern:** Test files are named with `.tcl` extension and located in `tests/unit/`, `tests/integration/`, and `tests/modules/`.
- **Test Example:**
  ```tcl
  test {SET and GET work as expected} {
      r set mykey myvalue
      assert_equal [r get mykey] myvalue
  }
  ```
- **Test Infrastructure:** Uses Makefile and helper scripts for running tests. Skip tags are used to conditionally skip tests.

## Commands

| Command                | Purpose                                               |
|------------------------|-------------------------------------------------------|
| /new-feature-api       | Start a new feature or API implementation workflow    |
| /change-config-command | Add or modify a configuration option or command       |
| /bugfix-with-test      | Fix a bug and add/update a test for it                |
| /improve-docs-comments | Improve code comments or documentation                |
| /upgrade-dependency    | Upgrade a third-party dependency                      |
| /update-test-infra     | Update test infrastructure or skip tags               |
```