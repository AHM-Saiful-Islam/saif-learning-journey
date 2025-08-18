# Testability, Test Levels, and Mocking in Software Testing

## Learning Outcomes

By the end of this post, you should be able to:

* Understand the differences between different test levels (unit, integration, and system tests).
* Evaluate what makes a system more or less testable.
* Propose refactoring opportunities for increasing testability.
* Apply mock objects in order to unit test a class.
* Understand when not to apply mock objects and instead go for integration tests.

---

## 1. Test Levels

### Unit Testing

* Focuses on testing individual components (classes or functions) in isolation.
* Fast execution, detects small and localized bugs.
* Example:

```java
@Test
public void testAddition() {
    Calculator calc = new Calculator();
    assertEquals(5, calc.add(2, 3));
}
```

### Integration Testing

* Tests the interaction between multiple components.
* Ensures that different modules or services work together correctly.
* Martin Fowler’s definition: <a href="https://martinfowler.com/bliki/IntegrationTest.html" target="_blank">Integration Test</a>

### System Testing

* Verifies the system as a whole against requirements.
* Often performed in staging environments before release.

### The Testing Pyramid

* Popularized by Mike Cohn and expanded by Ham Vocke.
* Emphasizes having more unit tests, fewer integration tests, and even fewer UI/system tests.
* Practical view-full setup: <a href="https://martinfowler.com/articles/practical-test-pyramid.html" target="_blank">The Practical Test Pyramid</a>

### Hard-to-Test Dependencies

* Dependencies like databases, external APIs, file systems, and third-party services make tests brittle.
* Such dependencies often require mocking or stubbing.

---

## 2. Mock Objects

### What are Mocks?

* Mock objects simulate real dependencies, allowing controlled test environments.
* Example using **Mockito**:

```java
@Test
public void testServiceWithMock() {
    Repository mockRepo = Mockito.mock(Repository.class);
    Mockito.when(mockRepo.getData()).thenReturn("mocked data");

    Service service = new Service(mockRepo);
    assertEquals("mocked data", service.fetch());
}
```

### Controllability and Observability

* **Controllability**: The ability to set up a system state for testing.
* **Observability**: The ability to observe outputs or states to verify behavior.

When mocks increase controllability and observability, they improve unit test quality.

### When Not to Mock

* Avoid mocks when verifying integration with real components.
* Overuse of mocks can create brittle tests tied too closely to implementation details.

**Further Reading:**

* ThoughtWorks: <a href="https://www.thoughtworks.com/insights/blog/mockists-are-dead-long-live-classicists" target="_blank">Mockists vs Classicists</a>
* Martin Fowler: <a href="https://martinfowler.com/articles/is-tdd-dead/" target="_blank">Is TDD Dead?</a>

---

## 3. Designing for Testability

### Untestable Parts

* Legacy code with hidden dependencies.
* Static methods, singletons, tightly coupled classes.

### Design for Testability

* Encourages architectures that allow easy testing.
* Achieved by reducing coupling and increasing cohesion.

### Principles of Testable Architectures

* Use **Dependency Injection (DI)** to pass dependencies instead of hardcoding them.
* **Dependency Inversion Principle (DIP)** ensures higher-level modules are not dependent on lower-level modules.

**Example: Dependency Injection in Java**

```java
class Service {
    private Repository repo;

    // Dependency injected via constructor
    public Service(Repository repo) {
        this.repo = repo;
    }
}
```

**Further Reading:**

* Robert Martin: <a href="http://condor.depaul.edu/dmumaugh/OOT/Design-Principles/oodmetrc.pdf" target="_blank">OO Design Quality Metrics</a>
* Brett Schuchert: <a href="https://martinfowler.com/articles/dipInTheWild.html" target="_blank">DIP in the Wild</a>
* R. C. Martin: *Agile Software Development: Principles, Patterns, and Practices* (2002)

---

## 4. Pragmatic Sides of Mocking

### To Mock or Not to Mock?

* Spadini et al. (2017, 2018) showed that mocks are widely used but introduce coupling between test code and production code.
* Changing implementation details may require updating tests.

**References:**

1. Spadini et al. (2017) - *To mock or not to mock?* \[MSR Conference].
2. Spadini et al. (2018) - *Mock Objects For Testing Java Systems* \[Empirical Software Engineering Journal].

### Pragmatic Advice

* Use mocks when infrastructure makes testing slow or unreliable.
* Prefer integration tests when verifying external systems.
* Avoid shallow tests that verify implementation rather than behavior.

---

## 5. Further Reading

* Graham, D., Van Veenendaal, E., & Evans, I. (2008). *Foundations of Software Testing: ISTQB Certification*.
* Osherove, R. (2015). *The Art of Unit Testing*.
* Freeman, S., & Pryce, N. (2009). *Growing Object-Oriented Software, Guided by Tests*.
* Evans, E. (2004). *Domain-Driven Design*.
* Gamma, E., Helm, R., Johnson, R., & Vlissides, J. (1993). *Design Patterns*.

---
