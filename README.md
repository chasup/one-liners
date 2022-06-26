## Useful one (ish) liner commands

### SSH

#### Port forwarding, local to remote

```bash
ssh -L <local-port>:<target-host>:<remote-port> hostname
```

e.g. connect local port 8080 to a locally listening port 8001 on myhost.com

```bash
ssh -L 8080:localhost:8001 myhost.com
```

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