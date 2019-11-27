# Preamble
Test task includes developing of jenkins pipeline. Please find all supporting files in this repo.


# Pipeline requirements

1. should be implemented as a shared library (please create your own repository)
2. should read `config.yml` file
3. should run steps according to `config.yaml`
4. steps to be implemented: `notifications`, `build`, `database`, `deploy`, `test`
* note1: each step (except `notifications`) should be defined in its own [Stage](https://jenkins.io/doc/pipeline/steps/pipeline-stage-step/)
* note2: all steps (except `notifications`) are strictly ordered: `build`, `database`, `deploy`, `test`.
* note3: if any step is failed, the pipeline should not execute the next step and `notifications` step should be triggered with name of the failed step
5. all tests (regression, performance, integration) should be run in parallel
* note: one of tests defined in `config.yaml` contains `exit 1` to simulate error condition
6. pipeline should be presented as demo


# Recommended documentation sources:

* https://jenkins.io/doc/book/pipeline/shared-libraries/
* https://jenkins.io/doc/pipeline/steps/ 
* https://github.com/jenkinsci/pipeline-utility-steps-plugin/blob/master/docs/STEPS.md (make sure you installed this plugin)
