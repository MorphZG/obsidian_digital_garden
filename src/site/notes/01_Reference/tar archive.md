---
{"dg-publish":true,"permalink":"/01-reference/tar-archive/","title":"Archives with Tar","tags":["linux","utility"],"created":"2025-12-05T03:27:51.078+01:00"}
---


# Archives with Tar

```sh
tar -cvf backup.tar ~/Documents ~/Pictures ~/.dotfiles
```

tar command options:
-c create new archive
-r append files to archive
-v verbose, show progress
-f filename (name of archive)

```sh
tar -xvf backup.tar
```

-x extract
-t list the content of the archive
