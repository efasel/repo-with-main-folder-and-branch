# demo repo for an issue with ghorg

https://github.com/gabrie30/ghorg/blob/130476f6adeab8d5eb297d1302ca9c324c168167/git/git.go#L253

```go
args := []string{"rev-list", "--count", repo.CloneBranch}
```

There is a fourth argument missing: `--`

```go
args := []string{"rev-list", "--count", repo.CloneBranch, "--"}
```

## demo

not working:

```shell
$ git rev-list --count main
fatal: ambiguous argument 'main': both revision and filename
Use '--' to separate paths from revisions, like this:
'git <command> [<revision>...] -- [<file>...]'
```

working:

```shell
$ git rev-list --count main --
2
```