# Diagnosis of SELinux problems

## Search for context violations to see what and why

```ausearch -m AVC,USER_AVC -ts recent```

## Deeper diagnosis

Install setools and setroubleshoot.

```journalctl -t setroubleshoot --since=Sometime```

With an ID from the above, this will interpret the failure and suggest some fixes.

```sealart -i ID```

Sealert without the ID will show more than one entry from what you see in audit.

## Restoring correct context

Dry run to report on files with the "wrong" context

```restorecon -R -v -n PATH```

Drop ```-n``` to fix them.

## Reloading the SElinux policy from disk

```/usr/sbin/

## Managing rules

```semanage```

## Showing roles

```sesearch```
