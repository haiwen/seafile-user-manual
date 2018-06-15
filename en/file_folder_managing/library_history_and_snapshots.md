# Library History and Snapshots

Seafile tracks modification history for the entire library. Whenever a file operation applies to a library (file update, file deletion etc.), Seafile creates a "snapshot" of the previous state of the library. The snapshot contains the complete file and folder structure of the library.

In some cases, you have changed a lot of files in the library, and find that you want to revert all these changes. Restoring many files to their old versions can be tedious. At this time, the snapshot feature becomes very handy. You can restore the entire library to any point in the past. All the files in the library will be restored to that point of time, all at once. It works like a "time machine" for the library.

To view library history and snapshots:

* In Seafile Web App, navigate into the root folder of a library. Click the "History" icon in the library navigation top bar. All the change record of the library will be displayed in a list.
* Click the "view snapshot" link on any modification record. You'll see the library state at the point of time.
* In the snapshot view, you can download or restore any file or folder. If you're the library's owner, you can restore the enitre library to this point of time.

You can configure the retention period of library history: [setting history retention period](setting_library_history.md)