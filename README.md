# Automation Engineer Assessment

Welcome! We are building our automation infrastructure from the ground up, and this assessment is designed to evaluate your ability to architect clean, scalable, and resilient test frameworks. 

Please use the testing framework of your choice (e.g., Playwright, Cypress, WebdriverIO) to complete the following tasks.

## The Tasks

### Part 1: API Automation (State & Data Chaining)
Demonstrate how you handle authentication, data extraction, and schema validation. We will use the public DummyJSON API for this task.

**The Flow:**
1. **Authenticate:** Send a `POST` request to `https://dummyjson.com/auth/login` with the credentials `emilys` / `emilyspass`. Extract the authentication token and the user's `id` from the response.
2. **Fetch Data:** Using the extracted `id`, send a `GET` request to fetch the user's current cart (`https://dummyjson.com/carts/user/{id}`).
3. **Mutate Data:** Send a `POST` request to `https://dummyjson.com/carts/add` to add a new product (e.g., Product ID: 1, Quantity: 2) to that user's cart. 
4. **Assert:** Write assertions to verify:
   * The HTTP status code of the final request is `200` or `201`.
   * The final response accurately reflects the added product, and the total price calculates correctly based on the quantity.
   * The response payload matches an expected JSON schema structure.

---

### Part 2: UI Automation (Resilience & Logic)
Demonstrate how you handle UI interactions, dynamic waits, and page object structures. We will use the public demo site Sauce Demo.

**The Flow:**
1. Navigate to `https://www.saucedemo.com/` and log in using the `standard_user` credentials provided on the homepage.
2. On the inventory page, sort the products by **"Price (high to low)"**.
3. Write an assertion to verify that the sorting actually worked (the first item should be the most expensive).
4. Add the top two most expensive items to the cart.
5. Navigate to the cart, click checkout, fill in the shipping information, and complete the order.
6. Assert that the "Thank you for your order" confirmation message is displayed successfully.

---

### Part 3: Infrastructure & CI/CD
Because you will be establishing our testing practices, how the tests run is just as important as the tests themselves.

1. **Documentation:** Update this `README.md` with clear instructions on how to install dependencies and run the tests locally.
2. **CI Configuration:** Include a basic pipeline configuration file (e.g., a `.github/workflows/test.yml` for GitHub Actions, or a Dockerfile) that demonstrates how these tests would execute in a headless CI/CD environment.
3. **Reporting:** Configure your framework to generate a test report (HTML, Allure, default framework reporter, etc.) upon completion.

## What We Look For

We review submissions based on production-ready standards:
* **Dynamic Data Handling:** Passing extracted tokens dynamically rather than hardcoding them.
* **Environment Management:** Using `.env` files or configuration files for base URLs rather than hardcoding them in test files.
* **Smart Waits:** Utilizing framework-native dynamic waits (waiting for elements to be visible or network requests to complete) rather than using hardcoded `sleep()` or `pause()` commands.
* **Code Organization:** Clean separation of concerns (e.g., Page Object Models, custom commands, or utility functions).
* **Reproducibility:** The ability to clone the repository, install dependencies, and run the suite flawlessly without manual debugging.

## Submission Guidelines

1. Fork this repository or create your own public repository on GitHub/GitLab.
2. Commit your code frequently so we can see your progression.
3. Reply to our initial email with the link to your repository once you have completed the assessment. 

Good luck! We look forward to reviewing your code.