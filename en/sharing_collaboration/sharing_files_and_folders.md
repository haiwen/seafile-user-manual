# Sharing Files and Folders

In Seafile there are a few ways to share files and folders with others:

- Using links: there are multiple types of links that can be used to share with various scope of collaborators.
    - Share links: Any user who has access to the links can access the files or folders pointed by the link. No login is required.
    - Upload links: Any user who has access to the links can upload files to the folder pointed by the link. No login is required.
    - Internal links: Only logged in users who have read permission to the file or folder can access this link. Used for internal file sharing.
- Sharing libraries or folders: used for setting access permissions to a library or folder for specific users or groups. Users have to log in to access the folders.

## Creating Share Links to Files or Folders

Share links are public links to files or folders. They can be accessed by anyone, including those who don't have a Seafile account. You can also use password and expiration time to protect your links.

You can also set access permission to share links. There are three types of permissions:

* Preview and Download: the file or files in the folder can be downloaded. If the type of files can be previewed in a web browser, they can also be viewed online (e.g. Office files).
* Preview only: the file or files in the folder can only be viewed in a web browser, but cannot be downloaded. This is useful for sharing confidential data.
* Edit on cloud and download: Similar to "Preview and Download", but if the file can be edited in a web browser (e.g. an Office file), any user who has access to the link is allowed to edit it.

To create a share link in Seafile web app:

1. Navigate into the parent folder containing the file or folder. Hover your mouse over the file or folder and click on the "Share" icon that appears.
1. A pop-up window will appear with share options. Click the "Share Link" tab on the left panel. Then click "Generate" button to create a link. You can use password, expiration time and permission to protect your link.
1. Copy the link to email, instant messaging client or any other tool to send it to others.

You can also create share links from the desktop clients.

* If the library is synced, double click the library in the main window of Seafile client. The local folder of that library will be opened. Right click on the file or folder that you want to create a link to. In the pop-up menu, choose "Seafile" then "Create share link".
* If the library is not synced, double click the library in the main window of Seafile client. The cloud file browser window will be opened, and you can create a link to a file or folder in it.

## Creating Upload Links to Folders

You can use upload links to collect files from others. You can only create upload links for folders. Others cannot see the files in the folders. They can only upload files to them.

To create an upload link in Seafile web app:

1. Navigate into the parent folder containing the folder. Hover your mouse over the folder and click on the "Share" icon that appears.
1. A pop-up window will appear with share options. Click the "Upload Link" tab on the left panel. Then click "Generate" button to create a link. You can use password to protect your link.
1. Copy the link to email, instant messaging client or any other tool to send it to others.

## Sharing Libraries or Folders

You can share a library or folder to other registered Seafile users. The shared library or folder can be accessed by others with the web app and Seafile clients.

You can choose the range of the share:

* Share to user: You can share to one or more users.
* Share to group: You can share to a group.
* Share to organization: If you're using a private server, sometimes it's useful to share to all members on the server (the entire organization).

You can also set permission on the share:

* Read-Write: users can read, write, upload, download and sync files.
* Read-only: users can read, download and sync files.
* Admin: besides the write permission, users can also share the library.
* Online Read-Write: users can view and edit files online via a web browser. The files cannot be downloaded.
* Online Read-only: users can only view files online via a web browser. The files cannot be downloaded.
* Custom sharing permissions: user needs to create a custom sharing permission first, then he/she can choose the custom sharing permission when sharing.

To share a library or folder to a user or group:

1. Hover your mouse over the library or folder and click on the "Share" icon that appears.
1. A pop-up window will appear with share options. Click the "Share to user" or "Share to group" tab on the left panel. Select the user or group. Then click "Submit".

After you share a library or folder to a user, the user can see it by clicking the "Shared with me" tab on the left panel in Seafile web app. If you share it to a group, the group members can only see it by navigating into the group.

 To share a library to the entire organization: In Seafile web app, click the "Shared with all" tab on the left panel. Then click the "Add Library" button. In the drop-down menu, you can choose to share an existing library or create a new library and share it.

## Internal Links

Only logged in users who have read permission to the file or folder can access this link. It is used for internal file sharing. It's a convenient way for sharing files among team members who have access to a common library. You may just copy the link and paste it into an email or IM software.

## Notes
Permission such as Read-only, Read-Write, Preview Only etc. is primarily a UI effect, as the download button has been removed from the web interface. To view or edit a file, the original file must be loaded in the browser. However, advanced users can still access the original file.