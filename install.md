# A simple way to install onpremise Gitlab CE server

## Install gitlab latest version on Ubuntu 24.04 LTS

## Download package manualy

You can download packaged [here](https://packages.gitlab.com/gitlab/gitlab-ce)
select desired version based on your distro

for Ubuntu 24.04 noble
```
wget https://packages.gitlab.com/gitlab/gitlab-ce/packages/ubuntu/noble/gitlab-ce_17.9.7-ce.0_amd64.deb
sudo apt install ./gitlab-ce_17.9.7-ce.0_amd64.deb
```

---

Fix version to prevent unwanted upgrage
```
sudo apt-mark hold gitlab-ce
```

## Reset passwords
```
sudo gitlab-rake "gitlab:password:reset[root]"
```

**Check status**
```
sudo gitlab-ctl reconfigure
sudo gitlab-ctl status
sudo gitlab-ctl start/stop
```


