# UI lab results

Tool parts that I chose: Part 3 Robot Framework, Part 4 Cypress

## Part 0
- Step 0.1, Chrome version: 158.0.8127.38 (Official Build) (arm64)
- Step 0.3, ChromeDriver version: 158.0.8127.38
- Step 0.4, locator of Pizza, Please!: button[name="pizza-please"]
- Step 0.4, locator of Excluded tools: select
- Step 0.4, locator of Must be vegetarian: #default-checkbox
- Step 0.4, locator of Custom Pizza Name: input#pizza-name
- Step 0.5, pizza name, tool and calories of the run by hand: Lab Pizza 20261124-2035, Pizza cutter, 450

| Step | Actual result | Pass or fail |
|------|---------------|--------------|
| 1    | Heading reads "Looking to break out of your pizza routine?" | Pass |
| 2    | The four advanced fields appear | Pass |
| 3    | Fields show 600, Knife, vegetarian ticked, Lab Pizza 20261124-2035 | Pass |
| 4    | Name: Lab Pizza 20261124-2035, Tool: Pizza cutter, Calories per slice: 450 | Pass |
| 5    | "Please log in first." appears | Pass |
| 6    | Page shows "Latest pizza recommendations" | Pass |
| 7    | "Lab Pizza 20261124-2035 (tool=Pizza cutter, ingredients_number=6)" in the list | Pass |

## Part 3: Robot Framework
- robot --version: Robot Framework 7.5.1 (Python 3.12.2 on darwin)
- Step 3.2, failure message for the wrong title: Title should have been 'Web Form' but was 'Web form'.
- Step 3.8, run 1, result, elapsed time and pizza name: PASS, 00:00:15.828, Lab Pizza 20261124-211321
- Step 3.8, run 2, result, elapsed time and pizza name: PASS, 00:00:16.274, Lab Pizza 20261124-211701

## Part 4: Cypress
- node --version, npm --version and npx cypress version: v24.13.0, 11.6.2, Cypress package version 16.2.1, Cypress binary version 16.2.1
- Step 4.3, failure message for the wrong title: Timed out retrying after 10000ms, expected 'Web form' to equal 'Web Form' (- 'Web form' actual, + 'Web Form' expected)
- Step 4.6, tool and calories in the answer of POST /api/pizza: tool Pizza cutter, calories 800
- Step 4.7, the line of the admin list that shows your pizza: Lab Pizza 20261124-220838 (tool=Scissors, ingredients_number=5)
- Step 4.8, run 1, result, duration and pizza name: PASS, pizza-scenario.cy.js 00:11 and web-form.cy.js 00:02, Lab Pizza 20261124-xxxxxx
- Step 4.8, run 2, result, duration and pizza name: PASS, pizza-scenario.cy.js 00:11 and web-form.cy.js 00:04, Lab Pizza 20261124-xxxxxx

Note: running both specs in one `npx cypress run --browser chrome` stopped at the start of the second spec with "Error: * is not a valid URL" from inside Cypress 16.2.1 with Chrome 158, so each spec was run on its own.

## Part B
1. The three number boxes have the same id, `floating_filled`, so the id cannot find only one box. That is why the tests find the box by the text of its label. If each box had its own id, like `id="max-calories"`, the locator would be short and would not break when the page changes.

2. It is a consistency oracle, because it checks that two parts of the same system show the same thing. It compares the tool in the recommendation with the tool in the admin list. It would find a bug where the server saves a different tool from the one the customer saw.

3. The test could check that all the ingredients of the pizza are vegetarian. The page does not show this, but the answer of POST /api/pizza has a `vegetarian` value for each ingredient. In Cypress, the test can read this answer with `cy.wait('@pizza')` and check that every value is true.

4. In Robot Framework I had to write `Wait Until ...` keywords, but Cypress waited by itself for up to 10 seconds. Cypress was faster to write, and one run of QP-01 took about 11 seconds, while Robot Framework took about 16 seconds (15.828 s and 16.274 s). The Robot log showed every step with screenshots, and Cypress made a video, but it stopped with "Error: * is not a valid URL" when I ran both specs together.

5. I would choose Robot Framework for Project 2. First, it runs on Python and uses Selenium WebDriver with ChromeDriver, the same tools that my group already uses with pytest. Second, our test cases need a staff user and a customer in one test, and Robot Framework can open two browsers with `Open Browser` aliases, while Cypress can control only one browser in a test.

6. (Part 3) I would change only the variable `${MAX CALORIES}` in `resources/quickpizza.resource`. The test file only uses keywords like `Fill In The Pizza Request` and has no locators. So I do not need to change the test file at all.

7. (Part 4) A cookie keeps the browser on one QuickPizza server, and Cypress deletes the cookies before each test. If steps 6 and 7 were a new test, the browser could go to another server, and the admin list would not show my pizza. The new test would also lose `pizzaName` and `@tool`, because they only exist in the first test.