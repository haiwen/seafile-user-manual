# Sharing Files and Folders

In Seafile there are two ways to share files and folders with others.

## Creating Share Links to Files or Folders

Share links are public links to files or folders. They can be accessed by anyone, including those who don't have a Seafile account. You can also use password and expiration time to protect your links.

There are two types of links:

* Download Links: Created for others to download files or folders.
* Upload links: You can use upload links to collect files from others. You can only create upload link for a folder. Others cannot see the files in the folder. They can only upload files to the link.

To create a download link in Seafile web app:

1. Navigate into the parent folder containing the file or folder. Hover your mouse over the file or folder and click on the "Share" icon that appears.
1. A pop-up window will appear with all the share options. Click the "Download Link" tab on the left panel. Then click "Generate" button to create a link. You can use password and expiration time to protect your link.
1. Copy the link to email, instant messaging client or any other tool to send it to others.

You can also create download links from the desktop clients.

* If the library is synced, double click the library in the main Window of Seafile client. The local folder of that library will be opened. Right click on the file or folder that you want to create a link to. In the pop-up menu, choose "Seafile" then "Create share link".
* If the library is not synced, double click the library in the main Window of Seafile client. The cloud file browser window will be opened. You can create a link to file or folder in the cloud file browser.

To create an upload link in Seafile web app:

1. Navigate into the parent folder containing the folder. Hover your mouse over the folder and click on the "Share" icon that appears.
1. A pop-up window will appear with all the share options. Click the "Upload Link" tab on the left panel. Then click "Generate" button to create a link. You can use password to protect your link.
1. Copy the link to email, instant messaging client or any other tool to send it to others.

## Sharing Libraries or Folders

You can share a library or folder to other registered Seafile users. The shared library or folder can be accessed by others with the web app and Seafile clients.

You can choose the member range of the share:

* Share to user: You can share to one or more users, one by one.
* Share to group: You can share to a group of users. See how to manage groups in group sharing.
* Share to organization: If you're using a private server, sometimes it's useful to share to all members on the server (the entire organization).

You can also set read/write permission on the share:

* Read-Write share: the share members can do any update operations on the folder, including update file, upload file, delete, rename.
* Read-only share: the share members can only read the folder and files in it. They cannot do any update to the folder and files.

To share a library or folder to a user or group:

1. Hover your mouse over the library or folder and click on the "Share" icon that appears.
1. A pop-up window will appear with all the share options. Click the "Share to user" or "Share to group" tab on the left panel. Enter the user name or group name to share to. Then click "Submit".

After you share a folder or library to a user, the user can see it by clicking the "Shared" tab on the left panel in Seafile web app. If you share to a group, the group members can only see the shared folder or library by navigating into the group.

To share a library to the entire organization: In Seafile web app, click the "Organization" tab on the left panel. Click "Add Library" button. In the drop-down menu, you may choose sharing an existing library or creating a new library and share it.

## Frequently Asked Questions

**Can a share member share a folder or library to other users?**

No. Only the owner of the library or folder can share it to others.

**What happens if I change the name of a shared folder or file?**

If you share a link, the link will become invalid once you change the name of the folder or file.

If you share a folder, the share remains valid after the folder name is changed. But others still see the old name of the folder.