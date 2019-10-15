[Handbook](../../README.md) / Policies

# Commit Messages

Ensure your commits follow the following guidelines:

- Separate subject from body with a blank line
- Do not end the subject line with a period
- Capitalize the subject line and each paragraph
- Use the imperative mood in the subject line

Make sure the body of the commit:

- Explains why the change was made
- Explains how the change addresses the issue
- Links to relevant information, such as issues or other resources (note that task, PBI or issue IDs such as #123 are generally automatically linked up the the proper resource, use that to your advantage)

If your Git client supports it, feel free to use the following template: [git_commit_template.txt](git_commit_template.txt).

## Example of good commit message

```
Add thread locking to LogWriter

Prior to this change, the LogWriter when called in a multi-threaded
context, could sometimes crash due to the underlying log file being
locked. Although it's generally recommended to only use a single
instance of the LogWriter, we have seen this problem happening in
the wild and we always take the blame for it.

This change fixes the issue by introducing a shared lock between all
threads.

Fixes #123, #234
```

## References

- [https://chris.beams.io/posts/git-commit/](https://chris.beams.io/posts/git-commit/)
- [https://codeinthehole.com/tips/a-useful-template-for-commit-messages/](https://codeinthehole.com/tips/a-useful-template-for-commit-messages/)