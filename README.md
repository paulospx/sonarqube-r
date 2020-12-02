# SonarQube R
How to upload your R project *lintr* information into sonarqube.



# Dependencies 

You need to have the following 

- R (tested with version 4.0.3). 

You need to have the following R libraries:

- lintr
- devtools
- roxygen2

# Usage

Install *lintr* packages and R.

```bash
Rscript -e 'install.packages("lintr")'
Rscript -e 'install.packages("devtools")'
Rscript -e 'install.packages("roxygen2")'
```

To generate the file `lintr_out.json` execute the command:

```bash
rscript .\run_lintr.R
```

The *lintr* generates a json file  `lintr_out.json`  with the issues found on your code. 
This format is not compatible with SonarQube and needs to follow the format: 

- https://docs.sonarqube.org/latest/analysis/generic-issue/

So that *Sonar Scanner* is able to import the issues to *SonarQube*.

Issue fields description for Sonar.

- `engineId` - string
- `ruleId` - string
- `primaryLocation` - Location object
- `type` - string. One of BUG, VULNERABILITY, CODE_SMELL
- `severity` - string. One of BLOCKER, CRITICAL, MAJOR, MINOR, INFO
- `effortMinutes` - integer, optional. Defaults to 0
- `secondaryLocations` - array of Location objects, *optional*



Translating from *lintr json* into SonarQube *json format* can be done online via in this site: 

- https://paulospx.github.io/sonarqube-r/



To upload the `lintr_out.json`  to **SonarQube** add the following line to your properties file `sonar-project.properties` :

```properties
sonar.externalIssuesReportPaths=lintr_sonar_out.json
```



| Linter                             | Issue Type | Effort Minutes | Severity |
| ---------------------------------- | ---------- | -------------- | -------- |
| `object_usage_linter`              | CODE_SMELL | 5              | MINOR    |
| `absolute_path_linter`             | CODE_SMELL | 5              | MINOR    |
| `nonportable_path_linter`          | CODE_SMELL | 5              | MINOR    |
| `pipe_continuation_linter`         | CODE_SMELL | 5              | MINOR    |
| `assignment_linter`                | CODE_SMELL | 5              | MINOR    |
| `camel_case_linter`                | CODE_SMELL | 5              | MINOR    |
| `closed_curly_linter`              | CODE_SMELL | 5              | MINOR    |
| `commas_linter`                    | CODE_SMELL | 5              | MINOR    |
| `commented_code_linter`            | CODE_SMELL | 5              | MINOR    |
| `cyclocomp_linter`                 | CODE_SMELL | 5              | MINOR    |
| `equals_na_linter`                 | CODE_SMELL | 5              | MINOR    |
| `extraction_operator_linter`       | CODE_SMELL | 5              | MINOR    |
| `function_left_parentheses_linter` | CODE_SMELL | 5              | MINOR    |
| `function_left_parentheses_linter` | CODE_SMELL | 5              | MINOR    |
| `implicit_integer_linter`          | CODE_SMELL | 5              | MINOR    |
| `infix_spaces_linter`              | CODE_SMELL | 5              | MINOR    |
| `line_length_linter`               | CODE_SMELL | 5              | MINOR    |
| `no_tab_linter`                    | CODE_SMELL | 5              | MINOR    |
| `object_length_linter`             | CODE_SMELL | 5              | MINOR    |
| `object_name_linter`               | CODE_SMELL | 5              | MINOR    |
| `open_curly_linter`                | CODE_SMELL | 5              | MINOR    |
| `paren_brace_linter`               | CODE_SMELL | 5              | MINOR    |
| `semicolon_terminator_linter`      | CODE_SMELL | 5              | MINOR    |
| `seq_linter`                       | CODE_SMELL | 5              | MINOR    |
| `single_quotes_linter`             | CODE_SMELL | 5              | MINOR    |
| `spaces_inside_linter`             | CODE_SMELL | 5              | MINOR    |
| `spaces_left_parentheses_linter`   | CODE_SMELL | 5              | MINOR    |
| `todo_comment_linter`              | CODE_SMELL | 5              | MINOR    |
| `trailing_blank_lines_linter`      | CODE_SMELL | 5              | MINOR    |
| `trailing_whitespace_linter`       | CODE_SMELL | 5              | MINOR    |
| `T_and_F_symbol_linter`            | CODE_SMELL | 5              | MINOR    |
| `undesirable_function_linter`      | CODE_SMELL | 5              | MINOR    |
| `undesirable_operator_linter`      | CODE_SMELL | 5              | MINOR    |
| `unneeded_concatenation_linter`    | CODE_SMELL | 5              | MINOR    |
| other non specified in the table   | CODE_SMELL | 5              | MINOR    |

The mapping table is used to generate issue type, effort and severity.



 