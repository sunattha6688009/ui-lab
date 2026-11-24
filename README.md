# ui-lab

ITCS386 Lab, Automated UI Testing. The tool parts that I chose are
**Part 3, Robot Framework** and **Part 4, Cypress**. Both automate test case
QP-01, A custom pizza reaches the admin list, on QuickPizza.
Results and answers are in [RESULTS.md](RESULTS.md).

## robot (Part 3)

Robot Framework tests with SeleniumLibrary. `first.robot` and `web_form.robot`
test Selenium's web form, `pizza_scenario.robot` automates QP-01, and
`resources/quickpizza.resource` keeps the locators and keywords of the
QuickPizza pages. `results/run1` and `results/run2` hold the log, report and
screenshots of two full runs.

Needs ChromeDriver in the environment variable `CHROMEDRIVER`. Run from the
`robot` folder:

```bash
python3 -m venv .venv && source .venv/bin/activate && pip install -r requirements.txt
robot -d results/run1 -v BROWSER:headlesschrome pizza_scenario.robot
```

## cypress (Part 4)

Cypress specs. `cypress/e2e/web-form.cy.js` tests Selenium's web form,
`cypress/e2e/pizza-scenario.cy.js` automates QP-01, and
`cypress/support/commands.js` holds the custom command `adminLogin`.
`cypress/videos` and `cypress/screenshots` hold the evidence of the last full run,
and `evidence/run1` and `evidence/run2` keep the screenshots and videos of both runs.

Run from the `cypress` folder:

```bash
npm install
npx cypress run --browser chrome --spec cypress/e2e/pizza-scenario.cy.js
npx cypress run --browser chrome --spec cypress/e2e/web-form.cy.js
```