# How to Use Encrypted Libraries

Seafile provides client-side end-to-end data encryption. You can create encrypted libraries to use this feature. File contents in encrypted libraries are encrypted on client side. The encryption password is not stored on the server. So even the server administrator can't access your file contents.

When creating an encrypted library:

* If you create an encrypted library in the web app, the password is sent to the server. The server uses this password to create the library. But it doesn't store the plain text password.
* If you create an encrypted library from a local folder with the desktop client (see [file syncing](../syncing_client/install_sync.md)), the password is not sent to the server.

When you access the encrypted library:

* If you use web app, you have to input the password to the server. The server will cache the password in encrypted format for 1 hour. It won't store the password on disk.
* If you use desktop client to sync the library, the password is not sent to the server. The client decrypts and encrypts file contents locally. The plain text password is not stored on the client disk either.
* iOS client supports client side encryption since version 2.1.6. Android client supports it since version 2.1.0.

Note that encrypted library only encrypts the contents of the files, but not the folder and file names.

More technical details of encrypted library can be found at [Seafile Manual](https://manual.seafile.com/security/security_features/).
