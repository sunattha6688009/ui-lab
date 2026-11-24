# UI lab results

Tool parts that I chose: Part 3 Robot Framework, Part 4 Cypress

## Part 0
- Step 0.1, Chrome version: 158.0.8127.38 (Official Build) (arm64)
- Step 0.3, ChromeDriver version: 158.0.8127.38
- Step 0.4, locator of Pizza, Please!: button[name="pizza-please"]
- Step 0.4, locator of Excluded tools: select
- Step 0.4, locator of Must be vegetarian: #default-checkbox
- Step 0.4, locator of Custom Pizza Name: input#pizza-name
- Step 0.5, pizza name, tool and calories of the run by hand: Lab Pizza 20261124-2035, Pizza cutter, 550

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
- robot --version:
- Step 3.2, failure message for the wrong title:
- Step 3.8, run 1, result, elapsed time and pizza name:
- Step 3.8, run 2, result, elapsed time and pizza name:

## Part 4: Cypress
- node --version, npm --version and npx cypress version:
- Step 4.3, failure message for the wrong title:
- Step 4.6, tool and calories in the answer of POST /api/pizza:
- Step 4.7, the line of the admin list that shows your pizza:
- Step 4.8, run 1, result, duration and pizza name:
- Step 4.8, run 2, result, duration and pizza name:

## Part B
1.
2.
3.
4.
5.
6.
7.