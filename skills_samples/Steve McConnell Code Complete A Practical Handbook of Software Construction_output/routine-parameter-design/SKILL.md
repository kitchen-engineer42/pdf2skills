---
name: routine-parameter-design
description: "Refactor and design function/method parameter lists for clarity and maintainability. Use when the user has too many arguments, needs to choose between positional and keyword parameters, wants to consolidate parameters into objects, or is designing new API method signatures."
---

# Routine Parameter Design

Apply structured parameter design when defining new functions or refactoring existing method signatures to reduce complexity, improve readability, and enforce clear interfaces.

## When to Use

- Function has more than 3-5 parameters
- User asks about argument ordering or naming
- Designing a new public API or library interface
- Refactoring a method with confusing or inconsistent parameters

## Workflow

### 1. Analyze Current Signature

Identify issues in the existing parameter list:

```python
# BEFORE: Too many parameters, unclear ordering, mixed concerns
def create_report(title, start_date, end_date, format, include_charts,
                  chart_color, output_path, compress, email_to, verbose):
    ...
```

**Red flags:**
- More than 5 parameters
- Boolean flags that change behavior (`include_charts`, `compress`, `verbose`)
- Related parameters that belong together (`start_date`/`end_date`, `chart_color`/`include_charts`)

### 2. Apply the Input-Modify-Output Order

Arrange parameters in this sequence:

1. **Input** — data the function reads but does not change
2. **Modify** — data the function reads and updates in place
3. **Output** — data the function writes but does not read

```java
// BEFORE: random ordering
void processData(List<Result> output, Config config, List<Item> input, Logger log)

// AFTER: input → modify → output
void processData(List<Item> input, Config config, Logger log, List<Result> output)
```

### 3. Consolidate into Parameter Objects

Group related parameters into a single object:

```python
# AFTER: Related parameters grouped into objects
@dataclass
class DateRange:
    start: date
    end: date

@dataclass
class ChartOptions:
    include: bool = False
    color: str = "blue"

@dataclass
class OutputOptions:
    path: str = "./report"
    format: str = "pdf"
    compress: bool = False

def create_report(title: str, date_range: DateRange,
                  charts: ChartOptions = ChartOptions(),
                  output: OutputOptions = OutputOptions()):
    ...
```

### 4. Apply Modifiers and Defaults

```typescript
// Use readonly/const for input-only parameters
function calculateTotal(readonly items: Item[], taxRate: number = 0.0): number

// Use sensible defaults to reduce required arguments
function connect(host: string, port: number = 5432, timeout: number = 30): Connection
```

### 5. Validate the Result

**Checklist:**

- [ ] Parameter count is 5 or fewer (or uses a parameter object)
- [ ] Parameters follow input → modify → output ordering
- [ ] Related parameters are grouped into objects
- [ ] Boolean flags are replaced with enums or option objects where possible
- [ ] All parameters are actually used in the function body
- [ ] Defaults are provided for optional parameters
- [ ] Names are descriptive and consistent with similar functions in the codebase
