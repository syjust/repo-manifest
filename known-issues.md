# Known issues about repo usage

Known issues about warning and error message on repo usage

## Server does not provide clone.bundle; ignoring.

When making a ``repo init`` or a ``repo sync`` message is :
```
curl: (22) The requested URL returned error: 404 Not Found
Server does not provide clone.bundle; ignoring.
```

[resource](http://stackoverflow.com/questions/23300245/what-to-do-about-curl-clone-bundle-error-on-aosp-repo-sync)


Repo attempts to download a prepackaged bundle file to bootstrap each git prior
to downloading the most recent data via Git's HTTP protocol. The latter is more
expensive on the server side and results in worse performance so the bundle
file allows the download to cut some corners.

If a bundle file isn't available (like in this case),
Repo will ignore it and proceed anyway.

### TL;DR

**In other words, don't pay any attention to this.**


## warning: project 'repo' branch 'master' is not signed

When making a ``repo sync`` message is
```
warning: project 'repo' branch 'master' is not signed
warning: Skipped upgrade to unverified version
```

[resource](http://repo-discuss.narkive.com/Aiswjlx6/how-to-change-repo-code)

Export your public key and replace the REPO_MAINTAINERS block in the
"repo" script.
Edit the keyring version field and bump it.

Use `git tag -s` to create a local signed tag for your team at the tip
of your stable branch.

Push this to your local copy of repo.

Each member of your team needs to run `mkdir tmp_dir; cd tmp_dir; repo init`
...

### TL;DR

**Other method is to run repo with the --no-repo-verify flag**
