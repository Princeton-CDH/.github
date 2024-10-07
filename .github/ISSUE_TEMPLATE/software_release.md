---
name: Software release checklist
about: Checklist for releasing new versions of software
title: 'Software release checklist'
labels: chore
assignees: ''

---

## release prep
- [ ] Pull updated copies of the develop and main branches
- [ ] Use git flow to create a new release branch with the appropriate version (e.g., `git flow release start 0.5`)
- [ ] Review database migrations to make sure updates look good (django only; should be caught in testing/qa)
- [ ] Update release version to appropriate number (for Python apps, set to final version without any `-pre` or `-dev` tags).
- [ ] Update changelog to make sure that all features, changes, bugfixes, etc included in the release are documented.  You may want to review the git revision history to be sure you’ve captured everything.
- [ ] Update deploy notes to document any manual steps that need to be done with the deploy (e.g., running any import scripts, configuring site domain in Django admin, etc)
- [ ] Update any README badges that are pointing to develop branches to use either main or default branch (GitHub Actions workflow status, code coverage, etc).
- [ ] Make sure local settings are documented (for django app: sample local settings file includes any new configurations).
- [ ] Check python requirements for any internal dependencies that should be released (or at least pinned to a specific git commit)
- [ ] Release & publish any internal JS dependencies with updates; specfy the published version number in package.json
- [ ] Use npm audit to check and fix vulnerabilities in npm dependencies
- [ ] Make sure that unit tests and other GitHub Actions workflow checks on are passing on the release branch (fix them if they are not)
- [ ] Make sure code coverage is 95% or higher. Review for any important gaps.
- [ ] Review code documentation to make sure it is up to date. If the database has changed, generate and include current schema documentation images.
- [ ] Run pip freeze, save output as requirements.lock and check in to document known working versions of python dependencies
- [ ] Use git flow to finish the release (merge release branch into both main and develop, create a tag, remove the release branch, etc.). (git flow release finish 0.5)


## after release
- [ ] Increase the develop branch version so it is set to the next expected release (i.e., if you just released 0.5 then develop will probably be 0.6-dev unless you are working on a major update, in which case it will be 1.0-dev)
- [ ] Push all updates to GitHub (main branch, develop branch, tags) 
- [ ] Clean up any release branches on GitHub
