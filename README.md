# BIOL7180--Code-Review

## Code Review: DNA Methylation Workflow

* Paper: [Smart-RRBS for single-cell methylome and transcriptome analysis](https://www.nature.com/articles/s41596-021-00571-9) 
* Git Hub Repository: [Link for the GitHub codes](https://github.com/Matioli-amoc/bisulfite-seq-tools.git)

### Why I Chose This Repository

I chose this repository because it provides a complete, reproducible workflow for DNA methylation analysis with clear documentation and example datasets. It allows for evaluation of code organization, workflow structure, reproducibility, and integration with R-based downstream analysis, making it ideal for a code review.

This protocol describes a reproducible workflow for analyzing DNA methylation data, including preprocessing, alignment, methylation calling, quality control, and aggregation.

---


## 1. Repository overview

* **Objective:** This repository provides tools and scripts for processing bisulfite sequencing (BS-seq) data to extract DNA methylation information.It supports key steps in the workflow, including data preprocessing, alignment, and methylation profiling.

---

## 2. Repository Organization

The repository has a relatively simple and functional structure. The scripts are grouped according to their purpose, focusing on different steps of bisulfite sequencing data analysis. However, the structure is not highly orginized, even with the separeted directories still have lots of files and documentations that are not in one specific directory and that made the navigation throught the repository less intuitive for reproducibility purposes.

---

## 3. Code and Scripts

The repository contains scripts designed to process bisulfite sequencing data. The code appears to focus on practical execution rather than extensive documentation, some scripts are not well commented to explain each step. Some considerations about the code and scripts:

* Input and output formats are not always explicitly described;
* The code is functional but could benefit from improved readability and reproducibility.

Despite this, the scripts demonstrate a clear understanding of bisulfite sequencing data processing.

### Repository code exemple to review:

[Code QC report link](https://github.com/Matioli-amoc/bisulfite-seq-tools/blob/main/Rscripts/qc_report_2.R)

This script is designed to perform quality control (QC) analysis for bisulfite sequencing (BS-seq) data using R. The objective of the code is clearly defined by the title, and the functions and packages used are appropriate for methylation analysis of bisulfite sequencing data. The visualization outputs are also very important, such as bar plots for mapped and unmapped reads.

However, the code lacks comments and documentation. The inputs and outputs are not well described, including the input data format and the expected structures and files. There are also many reproducibility issues, such as hardcoded library paths (e.g., 1) and undefined objects in that script (e.g., 2).

e.g 1:
```
lib.loc='/apps/lab/aryee/R/R-3.2.3/lib64/R/site-library'
```
e.g 2:
```
load(paste0(Dir,bsseq))
# The object Dir is not defined in that code. It may be an object created earlier during the analysis in other code, but that is not well documented.
```
We also have some parts of the code that are difficult to follow, such as repeated object assignments, complex transformations without explanation, and outdated packages and practices.

Considerations about the code: The script appears to be part of a larger pipeline but is not fully self-contained. It depends on external files and a predefined directory structure. If we follow all the steps in the repository, this code would work well. However, if we need only the QC analysis, we can't use this code directly without the full pipeline and other codes. Without these, the script cannot be executed independently, which limits reproducibility.

Suggestions for Enhancement: The script would benefit from additional comments explaining each code segment, especially regarding input files and variables. Including a brief guide on how to execute the script and the expected data format would be useful. Improving reproducibility by avoiding hardcoded library paths or environment variables is recommended, as it makes sharing and running the script more straightforward. Clearly defining all components within the script and providing example datasets would facilitate its use. Additionally, adopting clearer variable names and avoiding variable reuse would enhance readability. Utilizing more recent packages like tidyr and dplyr instead of older ones would modernize the code. Converting the script into an R Markdown document could also enhance clarity and ease of understanding during analysis.

---

## 4. Reproducibility

Reproducibility is partially supported.

The repository provides reusable scripts. However, there is limited information about:

  - Required dependencies
  - Exact workflow steps
  - Example datasets
  - absolute file path
  - lack of comments guiding the following steps

Without a fully documented pipeline or example execution, reproducing the analysis may require additional effort.

---

## 5. Documentation

The documentation is minimal:

- There is limited explanation of how to run the scripts
- Dependencies and software requirements are not fully specified
- There are no detailed step-by-step instructions

Improving the README with usage examples, installation instructions, and expected outputs would significantly improve the usability.

---

## 6. Strengths

- Focused on DNA methylation and bisulfite sequencing analysis
- Provides practical scripts for data processing
- Useful for users with prior experience in bioinformatics

---

## 7. Limitations and Suggestions

* Add a more detailed README with:

  - Installation instructions
  - Dependencies
  - Example commands
- Include sample data or test cases
- Improve code comments and documentation
- Organize files into clearer directories
- Consider modifiying into a more reproducible workflow

---

## 8. Final Evaluation

This repository provides useful tools for bisulfite sequencing data analysis and demonstrates a solid understanding of DNA methylation workflows. However, limitations in documentation, code clarity, and overall organization reduce its accessibility and reproducibility. While the scripts appear to function well within the full pipeline, their dependency on external components and lack of detailed guidance make independent use more challenging. Improving documentation, standardizing the workflow, and enhancing code readability would significantly increase the usability of this repository.

---

