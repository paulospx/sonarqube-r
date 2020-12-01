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















