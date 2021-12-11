# How to install and setup PACTA as a first-time user
- - -
## Overview:
In this tutorial first-time users will achieve:
* running a PACTA_analys with example data
* running a PACTA analysis with new data
* generating interactive reports

**Keywords:** PACTA analysis, interactive reports, onboarding

## Before you start:
### System requirements:
|           | Recommended   | Minimum               |
|-----------|---------------|-----------------------|
| RAM       | 16 GB or more | 8 GB                  |
| Windows   | 64-bit        | 32-bit                |
| Mac OS    | current OS    | -                     |
| Linux     | current OS    | -                     |
| R version | 3.6.1         | no earlier than 3.4.3 |

### Software Requirements:
* GitHub (ex. [GitHub Desktop](https://desktop.github.com/))
* A GitHub account added to the [2DegreesInvesting GitHub](https://github.com/2DegreesInvesting) organization
* [RStudio (recommended version 1.1.456)](https://rstudio.com/products/rstudio/)
* MikTeX- a distribution of the LaTeX typesetting system; includes TeXworks (preferably version 2.9)

### Required libraries and packages:
Necessary packages:
```
tidyr, dplyr, scales, reshape2, tidyverse, readxl, tidyselect (and dependencies).
Further R packages needed: grid, ggplot2, ggthemes, dplyr, reshape2, gridExtra, scales,
stringr, extrafont, tidyr, knitr, RColorBrewer, matrixStats, rworldmap, ggmap, cowplot,
ggrepel, readxl, tidyverse, ggforce, sitools , countrycode
```
- - -
## How to run a PACTA analysis with a test portfolio:
### Step 1 — Create local copies of the repositories:
Clone all repositories into the **same local directory**.

#### To create a local copy:
1. [Fork](https://docs.github.com/en/get-started/quickstart/fork-a-repo) the [PACTA_analysis](https://github.com/2DegreesInvesting/PACTA_analysis) repository
2. Fork the [PACTA-data](https://github.com/2DegreesInvesting/PACTA-data) repository
3. From your Git software, [clone](https://docs.github.com/en/get-started/quickstart/fork-a-repo#cloning-your-forked-repository) the public PACTA_analysis repository
4. Clone the PACTA_data private repository

> Every time you work on local copies, [pull](https://docs.github.com/en/get-started/using-git/getting-changes-from-a-remote-repository) updates through your method of Git to ensure you’re working with the most recent versions. Check that you’re working in the master branch—this is suitable when you are only running analyses.

### Step 2 — Launch RStudio:
To launch RStudio with the required PACTA_analysis files:
* From your local directory open` PACTA_analysis > R > PACTA_analysis.rproj `

### Step 3 — Install the required packages
Install all the required packages listed in Getting Started.

### Step 4 — Running web_tool_script1 and web_tool_script2:
The scripts use the example files located in `working_directory'
* `20_Raw_Inputs > TestPortolio_Input.csv`
* `10_Parameter_File > TestPortfolio_Input_PortfolioParameters.yml`
	* The `portfolio_name_in` variable must match the `.csv` file name

#### To run web_tool_script_1.r:
1. Open `web_tool_script_1.r` in RStudio
2. Click Source to run the script
3. To confirm the script was successful, navigate to: `working_directory > 30_Processed_Inputs > TestPortfolio_Input`. The generated folder should contain new data and objects.
4. Inspect these two files before moving on:
	* `audit_file.csv`
	* `invalidsecurities.csv`

> These files are your first indication if something has gone wrong with a portfolio. They identify what data is valid or invalid for the analysis.

#### To run web_tool_script_2.r:
1. Open `web_tool_script_2.r` in RStudio
2. Click Source to run the script
3. To confirm the script was successful, navigate to: `working directory > 40_Results > TestPortfolio_Inputs`. Confirm it contains the following 6 files:
	* `Bonds_results_company.rda`
	* `Bonds_results_map.rda`
	* `Bonds_results_portfolio.rda`
	* `Equity_results_company.rda`
	* `Equity_results_map.rda`
	* `Equity_results_portfolio.rda`

> To open the `.rda` files: `R> readRDS(“”) `
> ***This is a specific method to this application only due to error. `.rda` files are click to open in all other cases.***

- - -
# Next Steps:
Use your own portfolio data and generate interactive reports.
## Running an analysis with your new data:
### Step 1 — Reset the environment:
1. Restart R
2. Manually delete the generated `TestPortfolio_Input` folders from the `working_directory`. Keep one copy for reference.

### Step 2 — Load your portfolio files:
1. Copy your working portfolio into `20_Raw_Inputs`
2. Go to `10_Parameter_Files`. Make a copy of `Portfolio_Input_PortfolioParamaters.yml`. Rename the file to `PORTFOLIONAME_PortfolioParameters.yml.`
3. View the file in RStudio and edit the following variables:
	* `portfolio_name_in`: your file name without `.csv`
	* `investor_name_in:` anything
	* `peergroup:` anything
	* `language:`anything
	* `project_code:` GENERAL
4. Save your changes

### Step 3 — Run `web_tool_script1.r` and `web_tool_script2.r`:
#### To run `web_tool_script1.r`:
1. Open `web_tool_script_1.r` in RStudio
2. Edit line 12 `{portfolio_name_ref_all “PORTFOLIONAME”}`
3. Click save
4. Click Source to run the script
5. Check the results in `working_directory > 30_Processed_Inputs`

#### To run `web_tool_script2.r`:
1. Open `web_tool_script_2.r` in RStudio
2. Edit line line 14 `{portfolio_name_ref_all “PORTFOLIONAME”}`
3. Click save
4. Click Source to run the script
5. Check the results in `working_directory > 40_Outputs`

> Note: The `web_tools_scripts` can't be run out of order, i.e., you can’t run #3 before you run #2. They must be run successively and each depend on the outputs each script generates.

## Generating an Interactive Report:
### Step 1 — Create local copies of the repositories:
It is recommended to clone all repositories into the **same local directory**.

1. From your Git software [fork](https://docs.github.com/en/get-started/quickstart/fork-a-repo) and [clone](https://docs.github.com/en/get-started/quickstart/fork-a-repo#cloning-your-forked-repository) the [create_interactive_report](https://github.com/2DegreesInvesting/create_interactive_report), [2dii.climate.stress.test.data](https://github.com/2DegreesInvesting/r2dii.climate.stress.test) and 2dii.stress.test repositories.

> Every time you work with the local copy, [pull](https://docs.github.com/en/get-started/using-git/getting-changes-from-a-remote-repository) updates through your method of Git to ensure you’re working with the most recent version. Check that you’re working in the master branch—this is suitable when you are only running analyses.

### Step 2: Run web_tool_script_3.r
1. Open `web_tool_script_3.r` in RStudio
2. Edit line line 9 `{portfolio_name_ref_all “PORTFOLIONAME”}`
3. Click save
4. Click Source to run the script
5. Check the results in `working_directory > 50_Outputs > PortfolioName > Report > index.html`

> All the outputs in the folder are required for the `.html `file to display properly; zip the folder  to send out if required.

If something goes wrong with `web_tool_script_3.r`, take the following steps to ensure you're working from a clean copy:
1. Quit R
2. Re-open the `.rproj` directory
3. Delete all previously generated outputs
4. Delete the interactive report repository and clone it fresh
