Skeleton of simple merge tool / merge driver.

Repo also contains branches demonstrating various merge conflicts.

Configuration to use the tool:
```
# .git/config
[mergetool "cities-mergetool"]
        cmd = /path/to/2026-custom-merge-tools/mergetool $LOCAL $BASE $REMOTE $MERGED
        trustExitCode = true

[merge "cities-driver"] 
        driver = /path/to/2026-custom-merge-tools/mergetool --driver %A %O %B %P
```

```
# $GIT_DIR/info/attributes
<pattern>   merge=cities-driver
```

## Try it out in the repo

```
git worktree add -B merge-kll-driver ../tools-demo topic-k3
cd ../tools-demo
../2026-custom-merge-tools/setup-mergetool [--revert]
git merge topic-l
```
