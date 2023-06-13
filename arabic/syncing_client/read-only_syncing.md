# Read-only syncing

For ready-only libraries or folders, Seafile will show a forbidden icon (![](./imgs/read_only.png)) to indicate they are read-only. However, users can still modify the synced local copies. When a local copy is modified, Seafile will ignore the modified one. When the copy at the server is also modified, the client will popup a notification, saying that the local modified copy conflicts with the copy at the server side. To prevent data loss, the local copy is renamed to a conflict file.

If you want the be-shared users not be able to modify local copies, you can consider using the Seafile Drive client.
