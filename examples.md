# Scenarios With Gherkin

## Login

In this example, we use several Gherkin keywords to structure and organize our BDD scenarios.  
The Feature keyword provides a high-level description of the functionality being tested.  
The Scenario keyword introduces each individual test case. The Given, When, Then, and And keywords are used to describe
the steps and expected outcomes of each scenario.  
The Scenario Outline and Examples keywords are used to define a template for multiple scenarios that follow the same
pattern but use different data.  
Finally, we use tags (e.g., @login, @regression) to categorize and organize our scenarios.

```gherkin
Feature: Login

  @login @regression
  Scenario: Successful login with valid credentials
    Given the user is on the login page
    When the user enters a valid username and password
    And the user clicks the login button
    Then the user should be successfully logged in
    And the user should be redirected to the homepage

  @login @edgecase
  Scenario: Failed login with invalid credentials
    Given the user is on the login page
    When the user enters an invalid username and password
    And the user clicks the login button
    Then the user should see an error message
    And the user should not be logged in

  @login @edgecase
  Scenario Outline: Failed login with invalid <field>
    Given the user is on the login page
    When the user enters a valid username and <field_value> in the <field> field
    And the user clicks the login button
    Then the user should see an error message
    And the user should not be logged in

    Examples:
      | field    | field_value      |
      | username | invalid_username |
      | password | invalid_password |
```

## Shopping Cart

In this example, we use several Gherkin keywords to structure and organize our BDD scenarios.  
The Feature keyword provides a high-level description of the functionality being tested.  
The Background keyword defines a set of steps that are common to all scenarios within this feature.  
The Scenario keyword introduces each individual test case. The Given, When, Then, And, and But keywords are used to
describe the steps and expected outcomes of each scenario.  
The Scenario Outline and Examples keywords are used to define a template for multiple scenarios that follow the same
pattern but use different data.  
The Rule keyword is used to group related scenarios together under a common business rule or requirement. Finally, we
use tags (e.g., @cart, @smoke) to categorize and organize our scenarios.

```gherkin
Feature: Shopping Cart

  Background:
    Given the user is logged in
    And the user has an empty shopping cart

  @cart @smoke
  Scenario: Add item to shopping cart
    Given the user is on the product page for "Sneakers"
    When the user clicks the "Add to Cart" button
    Then the shopping cart should contain 1 item
    And the item should be "Sneakers"

  @cart @edgecase
  Scenario: Remove item from shopping cart
    Given the user has added "Sneakers" to their shopping cart
    When the user clicks the "Remove" button for "Sneakers"
    Then the shopping cart should be empty

  @cart @edgecase
  Scenario Outline: Update quantity of item in shopping cart
    Given the user has added "<item>" to their shopping cart
    When the user updates the quantity of "<item>" to <quantity>
    Then the shopping cart should contain <quantity> "<item>"

    Examples:
      | item     | quantity |
      | Sneakers | 2        |
      | T-Shirt  | 3        |

  Rule: Shopping cart total

    @cart @regression
    Scenario: Calculate total for single item
      Given the user has added "Sneakers" to their shopping cart
      When the user views their shopping cart
      Then the total should be "$50.00"

    @cart @regression
    Scenario: Calculate total for multiple items
      Given the user has added "Sneakers" and "T-Shirt" to their shopping cart
      When the user views their shopping cart
      Then the total should be "$80.00"

```