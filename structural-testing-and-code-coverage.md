# Structural Testing and Code Coverage

Structural testing (also known as **white-box testing**) focuses on analyzing the **internal structure of source code** to design test cases. Instead of only checking outputs for given inputs (black-box testing), structural testing ensures that the internal paths, conditions, and logic of the program are exercised by tests.

---

## Code Coverage Metrics

Coverage metrics provide **quantitative measures** of how much code is executed by test cases. The most common types are:

### 1. Line Coverage

* Measures whether each line of code is executed at least once.
* **Example:**

  ```java
  if (x > 0) {
      System.out.println("Positive");
  }
  ```

  * Test with `x = 1` → covers the line inside `if`.
  * Test with `x = -1` → does not cover it.

### 2. Statement Coverage

* Checks whether every statement in the code is executed at least once.
* Similar to line coverage, but considers **individual statements**, not just physical lines.

### 3. Branch Coverage

* Ensures every **decision branch** (true/false outcomes) is executed.
* **Example:**

  ```java
  if (x > 0) { ... } else { ... }
  ```

  * Requires `x = 1` (true branch) and `x = -1` (false branch).

### 4. Condition Coverage

* Evaluates **each boolean sub-expression** independently.
* **Example:**

  ```java
  if (A && B) { ... }
  ```

  * Requires: (A=true, B=false), (A=false, B=true), (A=true, B=true).

### 5. Path Coverage

* Ensures all possible **execution paths** through the program are tested.
* Quickly becomes infeasible as paths grow **exponentially**.

### 6. Modified Condition/Decision Coverage (MC/DC)

* Each condition in a decision must be shown to **independently affect** the decision’s outcome.
* Widely used in safety-critical domains (e.g., aviation).

#### MC/DC Example

Expression: **(A && B) || C**

| A | B | C | Expression | Effect                                   |
| - | - | - | ---------- | ---------------------------------------- |
| T | T | F | T          | Shows A and B together make outcome true |
| F | T | F | F          | Shows A independently affects outcome    |
| T | F | F | F          | Shows B independently affects outcome    |
| F | F | T | T          | Shows C independently affects outcome    |

* Each variable (A, B, C) is demonstrated to independently change the overall result.

---

## Loop Boundary Criteria

The **loop boundary adequacy criterion** ensures tests cover critical cases for loops:

* **Zero iterations** (loop not entered).
* **One iteration**.
* **Max-1 iterations**.
* **Max iterations**.

**Example:**

```java
for (int i = 0; i < n; i++) { ... }
```

* Test with `n = 0`, `n = 1`, `n = 2`, `n = max`.

---

## Data-Flow Testing

* Focuses on **variable definitions and uses**.
* Ensures paths between variable assignment (definition) and its usage are tested.
* Types:

  * **Def-Use Coverage**: every definition reaches at least one use.
  * **Def-Clear Coverage**: test ensures no unintended redefinitions before use.

---

## JaCoCo Tool

[JaCoCo](https://www.jacoco.org/) is a popular Java code coverage library.

From its [official documentation](https://www.jacoco.org/jacoco/trunk/doc/counters.html):

* **Instructions**: Count JVM bytecode instructions.
* **Branches**: Count decision branches (if/else, switch).
* **Lines**: Map bytecode instructions to source lines.
* **Complexity**: Measures cyclomatic complexity.
* **Methods/Classes**: Percentage of executed methods/classes.

Example in a Maven project:

```xml
<plugin>
  <groupId>org.jacoco</groupId>
  <artifactId>jacoco-maven-plugin</artifactId>
  <version>0.8.12</version>
  <executions>
    <execution>
      <goals>
        <goal>prepare-agent</goal>
      </goals>
    </execution>
    <execution>
      <id>report</id>
      <phase>verify</phase>
      <goals>
        <goal>report</goal>
      </goals>
    </execution>
  </executions>
</plugin>
```

---

## Testing with Coverage in IntelliJ IDEA

1. Open project in IntelliJ IDEA.
2. Right-click on the test class or package → **Run 'Tests with Coverage'**.
3. Coverage panel shows percentage of covered lines, branches, and methods.
4. Covered code is **highlighted green**, partially covered is **yellow**, and uncovered is **red**.

---

## Recommended References

* 📄 [Slides: Structural Testing – University of Edinburgh](http://www.inf.ed.ac.uk/teaching/courses/st/2017-18/Ch12.pdf) — based on *Pezze and Young, Software Testing and Analysis: Process, Principles and Techniques*, Wiley, 2007.
* 🎧 [Interview with Marc Hoffmann](http://www.se-radio.net/2018/05/se-radio-episode-324-marc-hoffmann-on-code-test-coverage-analysis-and-tools/) — key developer behind JaCoCo.

---

## 📌 Summary

Structural testing ensures that **the internal logic of the code is well tested**, beyond just input/output behavior. Code coverage metrics like line, statement, branch, condition, path, and MC/DC guide us in designing stronger test suites. Tools like **JaCoCo** and IDE integrations (IntelliJ IDEA) make it practical to measure and improve coverage. For advanced study, resources such as **Pezze & Young’s book** and the **University of Edinburgh slides** provide deep insights into theory and practice.
