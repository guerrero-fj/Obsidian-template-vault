# Setting Folder Permisions in Windows
[Source](https://support.robertsspaceindustries.com/hc/en-us/articles/360002284834-Windows-Set-Folder-Permissions)

![Avatar](https://support.robertsspaceindustries.com/system/photos/910458787/Ark_SC.PNG)

 Created by: **THRYSURR-CIG**

-   3 months ago
 -   Updated

When installing and updating the Launcher and game, you may have issues with permissions. Windows may pop up an error requiring Administrator access or warn you do not have the permissions needed to make changes to the folder.

These instructions walk through setting permissions and making changes to the Windows UAC. Depending on your Windows version, you may need to investigate additional steps.

**Symptoms:**

-   Installs and updates do not start or complete
-   Launcher log.log file may have an error installing to the folder, EPERMS, or permissions error
-   Install button flickers and returns without installing in the Launcher 

If you start having issues with installs and updates after a Windows update, it may have enabled UAC or changes your file ownership or permissions.

## TURN OFF UAC (USER ACCOUNT CONTROL)

UAC will lock you out of many installs and changes on your system. You may have to turn it off or set it to not Notify.

1.  Open your Windows Control Panel for User Accounts.  
    -   Windows 10: Click **Search**, enter UAC, and select **Change User Account Control settings**.
2.  Click **Change User Account Control Settings**.
3.  Move the slider all the way down to **Never Notify**. Click **Ok**.
4.  Restart your computer.

## TAKE OWNERSHIP

You need to take ownership of folders and files on the system. Even if you log in as an Administrator, you may not have access to change or install files. The Program Files folder is set to the Trusted Installer group, separate from Administrator access. Some of these

1.  Open Windows File Explorer.
2.  Right-click on Program Files. Select **Properties** then the **Security** tab.
3.  Click **Advanced**. This opens an Advanced Security Settings screen.
4.  Next to the Owner, click **Edit** or **Change**.
5.  To change the owner, select the **Advanced** button to select from a list. Or you can type in the user account name in the "Enter the object name to select" box. Click **Ok**.
6.  Select the check-box to Replace owner on subcontainers and objects. This appears under the Owner you changed to.
7.  Click **Apply**. Wait until completed.
8.  When it finishes, click **OK** on all boxes to close everything.

## FIX PERMISSIONS

With the files and folders claimed by your account, you need to apply permissions changes.

1.  Open Windows File Explorer.
2.  Right-click on Program Files. Select **Properties** then the **Security** tab.
3.  Click **Advanced** and click **Change Permissions**.
4.  Select Administrators or your account. Click **Edit**.
5.  On the **Permissions** screen, click **Add**.
6.  Change the Applies To drop-down menu to **This folder, subfolders and files**.
7.  Select the option for **Full Control**.
8.  Click **Apply**. Wait for it to complete.
9.  Close all screens and restart your computer.