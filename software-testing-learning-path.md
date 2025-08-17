# Software Testing

This document outlines key concepts, Target outcomes, and core topics in **Software Testing**. It is designed as a GitHub post to help learners and practitioners build structured knowledge of testing techniques, strategies, and tools.

---

## 🎯 Target Outcomes

You must be able to:

* **O1.** Analyze requirements to determine appropriate testing strategies.
* **O2.** Design and implement comprehensive test plans with instrumented code.
* **O3.** Apply a wide variety of testing techniques and compute test coverage and yield according to a variety of criteria.
* **O4.** Evaluate the limitations of a given testing process, using statistical methods where appropriate, and summarise outcomes.
* **O5.** Conduct reviews and inspections and design and implement automated testing processes.

---

## 📘 Topics should be covered

### 1. Testing Techniques and Principles

* **Defects vs. Failures**: A **defect** is a flaw in the system, while a **failure** is the manifestation of a defect when the software does not behave as expected.
* **Equivalence Class Partitioning (ECP)**: Dividing input data into valid and invalid classes to minimize test cases.
* **Boundary Value Testing (BVT)**: Testing values at, just below, and just above the boundaries.

<a href="https://www.youtube.com/watch?v=P1Hv2sUPKeM" target="_blank">🔗 Boundary Value Analysis and Equivalence Partitioning (Video)</a>

---

### 2. Types of Defects

* **Functional Defects**: Incorrect or missing functionality.
* **Performance Defects**: System runs slow or fails under load.
* **Usability Defects**: Poor user experience.
* **Compatibility Defects**: Issues across browsers, OS, or devices.

---

### 3. Black-Box vs. Structural Testing

* **Black-Box Testing**: Focuses on input/output without knowledge of internal code.
* **Structural (White-Box) Testing**: Tests designed based on internal code structure.

---

### 4. Testing Strategies

* **Unit Testing**: Tests individual functions or modules (e.g., JUnit for Java).
* **Integration Testing**: Ensures modules interact correctly.
* **Profiling**: Analyzing performance hotspots.
* **Test Driven Development (TDD)**: Writing tests before implementing code.

<a href="https://www.youtube.com/watch?v=Jv2uxzhPFl4" target="_blank">🔗 TDD in Java with JUnit (Video)</a>


---

### 5. State-Based, Configuration, and Compatibility Testing

* **State-Based Testing**: Validates system behavior under different states.
* **Configuration Testing**: Verifies performance under different configurations (OS, DB, network).
* **Compatibility Testing**: Ensures functionality across devices/browsers.

---

### 6. Alpha, Beta, and Acceptance Testing

* **Alpha Testing**: Internal testing by developers/QA before external release.
* **Beta Testing**: Released to limited external users for feedback.
* **Acceptance Testing**: Validates the system against business requirements.

---

### 7. Coverage Criteria

* **Line Coverage**: Each line executed.
* **Statement Coverage**: Each statement executed.
* **Branch Coverage**: Each decision outcome executed.
* **Condition Coverage**: Each boolean condition tested.
* **Path Coverage**: Each path through code tested.
* **MC/DC**: Each condition independently affects decision outcomes.

<a href="https://github.com/AHM-Saiful-Islam/saif-learning-journey/blob/main/structural-testing-and-code-coverage.md" target="_blank">🔗 structural-testing-and-code-coverage (Github post, saif-learning-journey)</a>

<a href="https://www.jacoco.org/jacoco/trunk/doc/counters.html" target="_blank">🔗 JaCoCo Counters (Official Manual)</a>

---

### 8. Test Instrumentation and Tools

* Instrumentation inserts extra code for measuring execution.
* Popular tools:

  * **JaCoCo** (Java)
  * **Istanbul** (JavaScript)
  * **Coverage.py** (Python)

<a href="http://www.se-radio.net/2018/05/se-radio-episode-324-marc-hoffmann-on-code-test-coverage-analysis-and-tools/" target="_blank">Interview with Marc Hoffmann (JaCoCo Developer)</a>

---

### 9. Developing Test Plans

A **test plan** includes:

* Test objectives
* Scope and features to test
* Test cases and expected results
* Tools required
* Roles and responsibilities

<a href="https://www.guru99.com/download-sample-test-plan.html" target="_blank">Sample Test Plan Template (Guru99)</a>

---

### 10. Managing the Testing Process: Development Lifecycles

* Testing must align with **SDLC models**:

  * Waterfall
  * V-Model
  * Agile (Scrum, Kanban)
  * DevOps (continuous testing)

---

### 11. Problem Reporting, Tracking, and Analysis

* Defects tracked using tools like **Jira**, **Bugzilla**, or **Azure DevOps**.
* A good bug report includes:

  * Summary
  * Steps to reproduce
  * Expected vs. actual results
  * Environment details

<a href="https://www.youtube.com/watch?v=GWxMTvRGIpc" target="_blank">Jira Tutorial for Beginners</a>

---

## 📌 Summary

This post covers core concepts of software testing, including testing principles, defect management, strategies, coverage criteria, and tools. By applying these techniques and outcomes, you’ll be able to design effective test plans, evaluate processes, and conduct automated testing effectively.

---

✅ For deeper reading: *Pezze and Young, Software Testing and Analysis: Process, Principles and Techniques*, Wiley, 2007.

<a href="http://www.inf.ed.ac.uk/teaching/courses/st/2017-18/Ch12.pdf" target="_blank">Slides: Structural Testing (University of Edinburgh)</a>

<a href="https://www.youtube.com/playlist?list=PL9ooVrP1hQOEx3hECzXbp3l5gIoHCtMwG" target="_blank">Software Testing Tutorials (YouTube Playlist)</a>
