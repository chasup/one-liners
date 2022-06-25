## Useful one (ish) liner commands

### python

#### Instant webserver

python -m http.server <port-number>

#### pip - list / upgrade out of date packages

```bash
pip list --outdated
```

and to upgrade:

```bash
pip list --outdated --format=freeze | cut -d= -f1 | xargs -n1 pip install -U
```

### git

#### Set the latest commit time to now

Useful following squashing / amending commits

```bash
git commit --amend --no-edit --date "$(date)"
```

#### Add execute permissions to scripts / binaries
```bash
git update-index --chmod=+x foo.sh
```

#### Remove local branches which have been merged remotely
```bash
git branch --merged | grep -v main | xargs git branch -d
```

### github.com

#### Get public SSH keys associated with an account:

```bash
curl https://github.com/<user>.keys
```
can be used to populate an authorized_keys file, e.g.
```bash
curl https://github.com/chasup.keys >> ~/.ssh/authorized_keys
```