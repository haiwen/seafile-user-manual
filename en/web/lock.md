# File Locking

When more than one person collaborate on a file, it's likely that more than one person modify the file at about the same time. Seafile handles this situation nicely with conflict files. But it's often more convenient to lock the file when one person wants to exclusively modify the file. Seafile Professional Edition supports file locking.

File locking works on both the web client and the desktop syncing client. We'll introduce them one by one.

### File Locking on the Web Client

To lock a file, you can navigate into the file's folder on the web client, and click on the "operations" drop-down menu.

![1](images/web-lock-file.png)

After the file is locked, you can see a red "stop sign" at the corner of the file icon. Moving the mouse on the stop sign, you can see who locks the file. And you can also unlock a file that's locked by you. But you cannot unlock files locked by others.

![2](images/web-file-locked.png)

### File Locking on the Desktop Client

After a library is synced to the desktop, you can lock/unlock files in that library inside File Explorer on Windows or Finder on Mac OS.

To lock a file, just right click on a synced file and choose "lock this file" in the "Seafile" menu.

![3](images/desktop-lock-file.png)

If a file is locked by you, you can see an orange "stop sign" on the file icon. You can choose to unlock it.

![4](images/desktop-my-locked-file.png)

If a file is locked by other user, you can see a red "stop sign" on the file icon. The file is automatically set to read-only. You cannot modify it until it's unlocked.

![5](images/desktop-other-locked-file.png)

If a library is not synced, you can still use [cloud file browser](../desktop/file-cloud-browser.md) to lock and unlock files in it.

### Details about File Locking

There are a few useful tips about how file locking works:

1. A locked file can only be unlocked by the user who locked it.
1. A locked file cannot be modified other than the lock owner. But it can be deleted, renamed or moved by other users. The purpose of file locking is only to prevent concurrent editing.
1. When a locked file is renamed or moved inside the same library, it remains locked after the operation.
