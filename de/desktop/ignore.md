# Excluding files/folders from syncing

Sometimes you don't want to sync some files or folders inside a library.
To achieve this, create a seafile-ignore.txt file in the root folder of a library. This special file specifies the files and folders that Seafile should not sync. Each line in a ignore.txt file specifies a pattern. The following pattern format are supported.

1. A blank line matches no files.
2. A line starting with # serves as a comment.
3. Seafile supports wildcards in the pattern. For example, "foo/*" matches "foo/1" and "foo/hello". "foo/?" matches "foo/1" but not "foo/hello". Note that the wildcard character * recursively matches all the paths under a folder. For instance, "foo/*.html" matches "foo/a.html" and "foo/templates/b.html".
4. If the pattern ends with a slash, it would only match a folder. In other words, foo/ will match a folder "foo" and paths underneath it, but will not match a regular file or a symbolic link "foo".
5. If a pattern doesn't end with a slash or a wildcard, it would not match a folder. For example, "foo" can only match regular file "foo" or a symbolic link; while "foo/" and "foo*" match a folder and paths under it.

## Example

```
# a regular file
test-file

# a dir
test-dir/

# wildcard *
test-star1/*
test-star2/*.html

# wildcard ?
test-qu1/?.html
test-qu2/?/
```

## Notes

The seafile-ignore.txt file only controls which files to exclude on the client side. You can still create a file from seahub web interface that's excluded on the client. In this case,

* The created file will still be synced back to clients. But any later local changes to those files will be ignored.
* If the file is modified on seahub, the new version will also be synced back to clients; If the file on the client is also modified, a conflict file will be generated on the client.

seafile-ignore.txt only ignores files that are not synced yet. If a file is already synced, and some time later you add it to the ignore list, its existing versions won't be removed.
