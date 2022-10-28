**Please read this information carefully!**

Compliance with the requirements below will significantly increase your passing score!


# Introduction

Test task includes development of Jenkins shared library code. Please find all supporting files in this repo.


# Pipeline requirements

Pipeline should be implemented as a shared library (initial shared library code can be found [here](https://github.com/genadiikruglenko-nbcuni/test-shared-library)).

Your code should be added into [Pipeline class](https://github.com/genadiikruglenko-nbcuni/test-shared-library/blob/master/src/com/example/Pipeline.groovy). 

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
    * e.g. commands, folders, test steps
6. `notifications` logic should honor event settings defined in configuration file.
    * i.e. *on_start: "never"*, *on_failure: "always"*, etc.


# Do's and Don'ts

- Task **must** be implemented as a *scripted* pipeline.
- **Do not** implement as a *declarative* pipeline.
- **Do not** implement using *vars functions*.
- Your code **must** be added to *src/com/example/Pipeline.groovy* **only**.
- **Do not** send you implementation as a groovy/pdf/word/txt file via email.
- Your solution should be presented as a Github repository (please create your own private repository or [clone](https://docs.github.com/en/github/creating-cloning-and-archiving-repositories/duplicating-a-repository) the initial shared library repository mentioned above) and provide an url. **Do not fork** as it cannot be made private.
- Your repository (or clone) **must not be public**. Please add the following Github users with read permissions when task is done:
  - https://github.com/gfonk
  - https://github.com/Brialius
  - https://github.com/genadiikruglenko-nbcuni
  - https://github.com/evgeniipomnikov-nbcuni
- You may be asked to provide a demo. Be ready to share your screen and show how it works in your test Jenkins environment.


# Willing to go the extra mile? (non-mandatory requirements)

- Try to make your code reusable and config-driven. For example, if `database` section is missng in config do not run `database` stage.
- Try to make your `test` stage be universal regardless of the number of tests defined in the config file.
- Introduce new classes/methods if you find it useful.


# Recommended documentation sources:

* https://jenkins.io/doc/book/pipeline/shared-libraries/
* https://jenkins.io/doc/pipeline/steps/ 
* https://github.com/jenkinsci/pipeline-utility-steps-plugin/blob/master/docs/STEPS.md (make sure you installed this plugin)
* http://groovy-lang.org/syntax.html Groovy syntax


# Good luck!
