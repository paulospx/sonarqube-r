# SonarQube R
How to upload your R project *lintr* information into sonarqube.



# Dependencies 

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

To upload the `lintr_out.json`  to **SonarQube** add the following line to your properties file `sonar-project.properties` :

```properties
sonar.externalIssuesReportPaths=lintr_out.json
```















