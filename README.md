# ansible-role-unattended-upgrades-minor-only

Set `unattended_minor_only_packages` to a list of packages you want to restrict to minor upgrades.

Example:

```
unattended_minor_only_packages:
  - gitlab-ce
  - docker-ce
```

Test using:
```
rm -f /var/lib/apt/periodic/update-stamp /var/lib/apt/periodic/download-upgradeable-stamp /var/lib/apt/periodic/upgrade-stamp
systemctl start apt-daily && systemctl start apt-daily-upgrade
```

unattended-upgrade debug run:
```
unattended-upgrade --debug --dry-run
```

Get currently installed apt package lists:
```
grep -e ^Origin -e ^Label -e ^Suite -e ^Codename -e ^Components /var/lib/apt/lists/*Release
```
