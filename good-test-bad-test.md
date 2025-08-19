# Writing Good Tests: Properties, Patterns, and Pitfalls

## Learning Outcomes

By the end of this post, you should be able to:

* Understand the **FIRST** properties of good tests.
* Recognize examples of bad tests and common test smells.
* Apply the **Test Data Builder** pattern to improve test maintainability.
* Understand flaky tests, their causes, and mitigation strategies.
* Improve **test readability** through structured approaches.

---

## 1. Properties of Good Tests (FIRST)

A good test should follow the **FIRST** principles:

* **Fast**: Tests should run quickly to provide rapid feedback.
* **Isolated**: Tests should run independently of each other.
* **Repeatable**: Tests should give the same results every time, regardless of environment.
* **Self-validating**: Tests should clearly pass or fail without manual interpretation.
* **Timely**: Tests should be written at the right time, ideally during development (e.g., TDD).

---

## 2. Bad Test Examples (Test Smells)

Common problems that reduce the quality of tests include:

* **Duplicate code**: Test setup code repeated in multiple places.
* **Assertion roulette**: Too many assertions in one test, making it unclear why it fails.
* **Slow tests**: Tests depending on external infrastructure (DBs, APIs) that slow feedback.
* **Resource problems**: Tests not cleaning up resources (files, sockets, DB connections). Use mocking to avoid this.
* **Concurrency issues**: Tests that fail when run in parallel.
* **General fixture**: Setting up more than what is needed, reducing clarity.
* **Indirect tests**: Tests that verify other classes indirectly instead of the one under test.
* **Sensitive equality**: Using strict equality for complex objects where it isn’t needed.

---

## 3. Test Data Builder Pattern

### The Problem

Creating test fixtures is often complex and repetitive:

```java
Invoice i1 = new Invoice(100.0, new User("Mauricio", new Address("Netherlands")), ...);
```

When the constructor changes, all tests using it must be updated.

### The Solution

Encapsulate object creation into a **Test Data Builder**, derived from the Builder pattern:

```java
public class InvoiceBuilder {
    private double amount = 100.0;
    private User user = new User("Mauricio", new Address("Netherlands"));

    public InvoiceBuilder withAmount(double amount) {
        this.amount = amount;
        return this;
    }

    public Invoice build() {
        return new Invoice(amount, user);
    }
}
```

Usage in a test:

```java
Invoice invoice = new InvoiceBuilder().withAmount(200.0).build();
```

### Related Concepts

* **Object Mother Pattern**: Provides prebuilt objects for tests but can lead to bloated fixtures.
* <a href="http://www.natpryce.com/articles/000714.html" target="_blank">**Test Data Builders: Nat Pryce**</a>

* **Frameworks**:

  * <a href="https://github.com/thoughtbot/factory_bot" target="_blank">factory\_bot (Ruby)</a>
  * <a href="https://github.com/six2six/fixture-factory" target="_blank">Fixture Factory (Java)</a>

---

## 4. Flaky Tests

### Causes

* **External infrastructure**: DBs, APIs, networks.
* **Shared resources**: Tests interfering with each other.
* **Timeouts**: Overly strict timing assumptions.
* **Resource leakage**: Open connections or files.
* **Non-determinism**: Random values, unordered collections.
* **Lonely vs interacting tests**: Behavior changes when tests run alone vs in suite.

### Real-World Examples

* <a href="https://testing.googleblog.com/2016/05/flaky-tests-at-google-and-how-we.html" target="_blank">Google: Tackling Flaky Tests</a>
* <a href="https://www.youtube.com/watch?v=Stjc80e15-c#t=1h11m25s" target="_blank">Facebook: Removing Flaky Tests (Video)</a>
* <a href="https://jonbell.net/publications/deflaker" target="_blank">DeFlaker Research by Bell et al. (2018)</a>

### Flakiness Decision Table

Gerard Meszaros provides a detailed decision tree to identify flaky tests:

* <a href="http://xunitpatterns.com/Erratic%20Test.html" target="_blank">Erratic Test (xUnit Patterns)</a>

---

## 5. Test Readability

Readable tests are easier to maintain and understand. Guidelines include:

* Use meaningful names (e.g., `shouldCalculateInvoiceTotal`).
* Follow **Arrange-Act-Assert (AAA)** structure.
* Avoid long setup methods by using builders or factory methods.
* Keep tests small and focused.

---

✅ By applying FIRST principles, avoiding bad practices, using **Test Data Builders**, and managing flaky tests, you can significantly improve the quality, maintainability, and reliability of your test suites.
