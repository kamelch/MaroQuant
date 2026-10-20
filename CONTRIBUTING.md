# Contributing

Keep each change focused and explain its purpose in the pull request.

- Use a feature branch for experiments and Git history to recover earlier versions.
  Do not create copies named `final`, `new`, `latest`, or `actually_final`.
- Give files names that describe their purpose. Keep distinct model or strategy
  variants when they represent different behavior, and document the differences.
- Keep local environments, credentials, caches, and temporary output out of commits.
  Check `git status` and `git diff --staged` before committing.
- Use commit messages that say what changed, such as
  `docs: correct setup instructions` or `fix: handle missing input data`.
  Avoid messages such as `update`, `changes`, or `fixed the thing`.
- In the pull request, describe validation performed and any checks you could not run.
