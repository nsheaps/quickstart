# quickstart
A  tool to help pull in templates from upstream repositories

* `quickstart add nsheaps/editorconfig` - looks for github.com/nsheaps/quickstart-editorconfig, updates line in quickstart.lock with the latest sha of the default branch, the repo remote url. Then adds the remote as quickstart-editorconfig, and performs a git merge of the remote default branch. `--write-only` pulls the changes without updating the lockfile
* `quickstart remove nsheaps/editorconfig` removes the references from quickstart.lock
* `quickstart update [nsheaps/editorconfig] [...]` iterates through the lock file and compares the shas, if they differ it pulls the remote into this repo with a merge. if the lockfile reference is semverish (eg matching `/v?\d+(.\d+){0,2})/`, it will attempt to update the ref to the latest semverish but won't go beyond. If you use renovate, you can use a ci script on its branches to rerun `quickstart` when those change (update only looks for the commit sha to change)
