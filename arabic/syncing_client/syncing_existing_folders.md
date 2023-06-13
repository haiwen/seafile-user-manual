# Syncing With an Existing Folder

Sometimes you already have a library on the Seafile server (shared by others, or uploaded from another computer). You can sync this library with an existing folder on your computer. The local folder must have the same name as the library. The files in the local folder will be merged with the files in the library. No file in the local folder or the library will be overwritten or lost. The merge will produce some [conflict files](file_conflicts.md) if file contents are different in the local folder and the library.

To sync a library with an existing folder, right click on the library in Seafile client's main window and click "Sync this library".

![](./imgs/seafile-sync-library.png)

In the pop-up dialog, click the "Sync with an existing folder" link.

![](./imgs/sync-with-an-existing-01.png)

Then choose an existing folder to sync with this library.

![](./imgs/sync-with-an-existing-02.png)