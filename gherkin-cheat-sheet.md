# Gherkin

Behavior Driven Development (BDD) is a software development approach that emphasizes collaboration between developers,
testers, and business stakeholders. It uses a natural language format to describe the expected behavior of the software,
making it easier for non-technical stakeholders to understand and participate in the development process.

## Gherkin syntax

In Behavior Driven Development (BDD), scenarios are written in a natural language format using Gherkin syntax. Gherkin
syntax uses several keywords to structure the scenarios and make them more readable.

### Given

This keyword is used to describe the initial state or context of the scenario. It sets up the preconditions for the
test.

### When

This keyword is used to describe an action or event that triggers a change in the system. It represents the test steps.

### Then

This keyword is used to describe the expected outcome or result of the scenario. It represents the test’s expected
result.

### And

This keyword is used to connect multiple steps or conditions within a Given, When, or Then statement.

### But

This keyword is used to introduce a negative condition within a Given, When, or Then statement.

### Feature

This keyword is used to describe a high-level feature or functionality of the software being tested. It provides context
for the scenarios that follow.

### Background

This keyword is used to describe a set of steps that are common to all scenarios within a feature. It helps to reduce
duplication and make the scenarios more readable.

### Scenario

This keyword is used to introduce a new scenario or test case. It provides a title or description for the scenario.

### Scenario Outline

This keyword is used to define a template for multiple scenarios that follow the same pattern but use different data. It
allows you to write more concise and reusable scenarios.

### Examples

This keyword is used in conjunction with Scenario Outline to provide the data for each instance of the scenario.

### Rule

This keyword is used to group related scenarios together under a common business rule or requirement. It helps to
organize the scenarios and make them easier to understand.

### @tag

This is not a keyword per se, but a way to add tags or labels to scenarios or features. Tags can be used to categorize,
filter, or organize scenarios in various ways.