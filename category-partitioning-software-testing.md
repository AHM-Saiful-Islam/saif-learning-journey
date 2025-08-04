# Category Partitioning in Software Testing

Category Partitioning is a black-box test design technique used to systematically generate test cases by dividing input parameters into categories and selecting representative test values. It helps reduce redundant testing while ensuring good coverage.

## Why Use Category Partitioning?

- Structures the test design process.
- Reduces total number of test cases while maintaining effectiveness.
- Encourages analysis of both valid and invalid input scenarios.
- Helps discover corner cases and interactions.

## Steps of Category Partitioning

1. **Function Analysis**  
   Understand the function or feature under test.

2. **Identify Parameters**  
   List the inputs and conditions that affect the behavior of the function.

3. **Define Categories**  
   Divide each input into groups of similar values (e.g., valid, invalid, boundary).

4. **Specify Choices**  
   Select representative values for each category.

5. **Determine Constraints**  
   Identify logical dependencies or illegal combinations between choices.

6. **Generate Test Cases**  
   Combine compatible choices to create test scenarios.

## Example: Login Form

Let’s assume we want to test a simple login form with the following inputs:

- Username
- Password

### Categories and Choices

**Username**:
- Valid username: `"john_doe"`
- Non-existing username: `"non_user"`
- Empty: `""`
- Special characters: `"$$$"`

**Password**:
- Correct password: `"correct123"`
- Incorrect password: `"wrongpass"`
- Empty: `""`
- Special characters: `"#secure!"`

### Constraints

- If username is empty, password is ignored.
- Only combination of `"john_doe"` and `"correct123"` is successful.

### Example Test Cases

| Username     | Password      | Expected Result       |
|--------------|---------------|------------------------|
| john_doe     | correct123     | Login successful       |
| john_doe     | wrongpass      | Invalid credentials    |
| non_user     | correct123     | Invalid credentials    |
| ""           | any            | Username required      |
| $$$          | #secure!       | Invalid username       |

## Tools

While Category Partitioning can be done manually, there are tools that assist in automating the process:

- Hexawise
- PICT (Pairwise testing, similar approach)
- Excel or test case management tools for manual setups

## Summary

Category Partitioning helps testers:
- Think critically about input domains
- Avoid redundant test cases
- Ensure broad and meaningful test coverage

It's a valuable technique for anyone working in software QA or test case design.

---

*Happy Testing!*
