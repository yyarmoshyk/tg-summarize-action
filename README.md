# tg-summarize-action
This is the github action to run tg-summarize on the results of terragrunt plan. This action was created to be executed for pipelines that are being executed for pull requests in github so the results are being added to the GitHub PR as a comment.

# Pre-requisites
1. [tf-summarize](https://github.com/dineshba/tf-summarize?tab=readme-ov-file#install)
1. Make sure that terragrunt is producing the plan files. Te following construction should be in the root terragrunt.hcl 
```terragrunt
terraform {
  ...
  extra_arguments "auto_plan_file" {
    commands = [
      "plan",
    ]

    arguments = ["-out=tfplan.output"]
  }
  ...
}
```