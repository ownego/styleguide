_* This rule is not the best practice but the one that we (developers at ownego) think is most suited for better software development.

***
## WORKFLOW
***
Following **Feature Branch Workflow**, see [here][feature branch workflow]

Base branch: _**master**_

Everytime you start working on a new feature, you have to create a new branch.
Feature branch should have descriptive names. Use one of following:

  - func-[function-name]
  - issue-#[issue-id set when create issue on jira]

Remember to **[Create a Pull Request][pull request]** whenever you complete a function.
After reviewing and testing, feature branch will be merged and delete forever.
If there's any issue after merged, create a new branch to fix that.

_**Ideal flow:**_

  1. Start a new feature branch. Move the corresponding jira issue to "In-progress".
  2. Update the master branch of your local repo (pull code of others) and rebase your branch to the tip of the current master branch if needed.
  3. Complete the function and push it to remote repo.
  4. Create a pull request. Move corresponding jira issue to "In-review"
  5. Review code. Make some changes following the reviewer's instructions if needed. Move the corresponding jira issue to "Test".
  6. Test feature on developer's shop. Fix bugs if needed.
  7. Merge code and delete the feature branch. Move the corresponding jira issue to "Done".
  8. If a bug appears after merged, tester will create a new issue on jira with issue-id. Create a new branch to fix bug.
  9. And so on.

_* Don't rebase after a pull request is created._

***
## COMMIT
***
Commits that contain the changes to global variables, functions, etc. should be placed on _master_

**On master branch**, writing commit message follows some rules below:

  - Use `git commit -m ""`
  - Use imperative, present tense
  - Capitalize the first letter
  - No dot `.` at the end of message
  - Message length should be less than 72 (equal or less than 50 is the best)

NOT GOOD

```
fix header style  // capitalized, use `Fix` not `fix`
fixed footer style  // imperative, present tense, use `Fix` not `fixed`
fixs section abc style // imperative, present tense, use `Fix` not `fixs`
Fix header script.  // no dot, remove `.`
```

GOOD

```
Add header markup
Fix collection grid columns setting
```

**On a feature branch**, you can commit any way you like. All commits of a feature branch will be squashed into the merge commit so don't need to care too much about split commits. Just do it your style.
Commit messages should be short and descriptive. No hard-limit but better less than 72 characters.

***
## REVIEW CODE
***
The code review checklist:

1. `Naming` - how the variables, functions, classes, etc. named, any nonsense?
2. `Complexity` - is it simple enough or over complex for nothing?
3. `Potential bugs` - does it contain any hidden bugs?
4. `Error handling` - does it catch all errors well?
5. `Guidelines` - does it follow CSS/JS/HTML guidelines?

For example, this PR in considered unapproved

```
A bit complex in *xyz*. Would
be good if we can fix that as they
are quite crucial @johndoe :-)

Naming: OK
Complexity: NOT OK, see comment in *xyz*
Potential bugs: OK
Error handling: OK
Guidelines: OK
```

And this is an approved PR

```
Looks good overall :-) +1

Naming: OK
Complexity: OK
Potential bugs: OK
Error handling: OK
Guidelines: OK
```



[feature branch workflow]: https://www.atlassian.com/git/tutorials/comparing-workflows#feature-branch-workflow
[pull request]: https://www.atlassian.com/git/tutorials/making-a-pull-request

