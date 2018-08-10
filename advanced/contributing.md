# Contributing

Anyone and everyone is encouraged to fork Cortex and submit pull requests, propose new features and create issues.

* Ideally, we'd first like to hear your concerns or suggestions in the form of an [issue](https://github.com/cortex-cms/cortex/issues). We can all avoid unnecessary re-work if a problem and its potential solution are first discussed before code is written.
* Fork on Github, then clone your repo:

```bash
$ git clone git@github.com:your-username/cortex.git
```

* Follow the [setup instructions](https://docs.cortexcms.org/basics/setup/manual-setup)
* Follow the [test suite instructions](https://docs.cortexcms.org/basics/setup/core-and-plugin-development#running-test-suite), and ensure all tests pass
* Make your changes. Make frequent commits, but keep commits and commit messages focused on individual, atomic feature changes or fixes. If you end up making many small commits during debug or development that belong to the same chunk of functionality, squash those commits before creating a pull request.
* Add tests for your change. Once again, ensure all tests pass.
* Push to a branch on your fork and [submit a pull request](https://github.com/cortex-cms/cortex/compare). Your PR must adhere to the following conventions:
  * For CareerBuilder team members, if the PR relates to a JIRA card, use the following naming convention:
    * `JIRA card #`: `PR Title`
    * Example: `COR-365: Unhandled Error on Media Upload`
  * For open source contributors, or if the PR does not relate to a JIRA card, use:
    * `PR Title`
    * Example: `Unhandled Error on Media Upload`
  * Names should use titleized capitalization. i.e.: `Login Form Redesign and Refactor`
  * Names should be dense, yet informative. For example, `Testing` is not an appropriate PR name, nor is `For update_url task, must use the body method to actually retrieve the stream from the S3 GetObjectOutput`. PR names are more high-level than commit messages.
  * PRs should be tagged appropriately \(i.e. `enhancement`, `bug`, etc\). Tags should be preferred over including things like 'bug' in the PR name.
  * PR Descriptions should be a clearly-separated, bulleted list summarizing what's contained in the commits, as well as any relevant notes or considerations for developers or ops. It should also detail any potential follow-up issues.
  * If working with a versioned library, open source users should not include version bumps or changelog updates in their PRs.

From here, it's up to the Cortex maintenance team \([employersitecontentproducts@cb.com](mailto:employersitecontentproducts@cb.com)\) to review your pull request. We operate in 2-week sprint lifecycles, but we'll try to get to your request or contribution sooner. We may suggest further improvements or alternatives, or the community at large may have input.

Some things that will increase the chances that your pull request will be accepted:

* Write [good tests](http://betterspecs.org)
* Write [good](http://tbaggery.com/2008/04/19/a-note-about-git-commit-messages.html), [semantic](https://seesparkbox.com/foundry/semantic_commit_messages) commit messages
* Be consistent
* If applicable, suggest additional options or alternatives, follow-up issues or potential future improvements

