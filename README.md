# Preamble
Test task includes developing of jenkins pipeline. Please find all supporting files in this repo.

# Pipeline requirements

Pipeline should be implemented as a shared library (initial shared library code could be found [here](https://github.com/Brialius/test-pipeline-library)), your code should be added into [Pipeline class](https://github.com/Brialius/test-pipeline-library/blob/master/src/com/example/Pipeline.groovy). 
The pipeline should be able to:

1. read `config.yml` file
2. run steps according to `config.yaml`
3. steps to be implemented: `notifications`, `build`, `database`, `deploy`, `test`
    * each step (except `notifications`) should be defined in its own [Stage](https://jenkins.io/doc/pipeline/steps/pipeline-stage-step/)
    * all steps (except `notifications`) are strictly ordered: `build`, `database`, `deploy`, `test`.
    * if any step is failed, the pipeline should not execute the next step and `notifications` step should be triggered with name of the failed step
    * each step should be executed in appropriate folder defined in config (deploy command should use the same folder as build command)
4. all tests (regression, performance, integration) should run in parallel
    * note: one of tests defined in `config.yaml` contains `exit 1` to simulate error condition
5. values in `config.yml` can be changed without changes in pipeline code
    * e.g commands, folders, test steps
6. pipeline should be presented as a demo

# Recommended documentation sources:

* https://jenkins.io/doc/book/pipeline/shared-libraries/
* https://jenkins.io/doc/pipeline/steps/ 
* https://github.com/jenkinsci/pipeline-utility-steps-plugin/blob/master/docs/STEPS.md (make sure you installed this plugin)
* http://groovy-lang.org/syntax.html Groovy syntax
