# Updating R with installr
[Blog source](https://www.r-statistics.com/2015/06/a-step-by-step-screenshots-tutorial-for-upgrading-r-on-windows/)

For Windows 10

1. Open your old version of R (not RStudio)-If you don't remember where it is, click on the magnifying glass icon next to the windows icon on your task bar and simply type "R".
2. You'll be taking to the R console (the boring-looking one). Since you probably do not have installr , you may need to install it:
```
install.packages("installr")
library(installr)
updateR()
```
3. From there, just follow the instructions in the blog and voila!

### Console method
```
# Step 1  
  
installedpkgs <- rownames(installed.packages(priority = "NA"))  
save(installedpkgs, file="installed_old.rda")  
  
# Step 2: Install the new version of R downloaded from the web.  
  
# Step 3  
  
load("installed_old.rda")  
installedpkgs.new <- rownames(installed.packages(priority = "NA"))  
missing <- setdiff(installedpkgs, installedpkgs.new)  
install.packages(missing)  
update.packages()
```

### Packages being saved in different locations
If you are on Windows 10, most of your packages are being installed in OneDrive-sigh. Thus, you end up with files spread accross multiple locations, depending on how you choose directories for different projects. [Here](https://medium.com/@ValidScience/how-to-fix-rstudios-package-installation-on-windows-10-c1e602bf3a1f) you will find a more elaborated rant and the solution to this problem. 

You need to do three things:

1.  Create the local folder you want to use for packages.
2.  Give yourself permission to change your RProfile file.
3.  Change your RProfile file.

#### 1. Create the local folder

To create the folder, open File Explorer → click on the C: drive (it should also say Local Disk) → click on the New Folder button on top → type a name like **RFolder** → press Enter.

#### 2. Change permissions

In you installed RStudio in the default directory, the path to your RProfile file is C:\Program Files\R\R-4.0.0\library\base\R\Rprofile.

Steps (screenshot below):

1.  Navigate to C:\Program Files\R\R-4.0.0\library\base\.
2.  Double-click the **base** folder so that you’re looking at its contents, which include the **R** subfolder.
3.  Right-click on the **R** subfolder and select Properties.
4.  Click on the Security tab.
5.  Click on the Edit button.
6.  Scroll down the **Group or user names** pane and click on the Users line near the bottom of that list.
7.  In the **Permissions for users** pane click on the Full Control checkbox under Allow.
8.  Click OK and OK again to save and exit these windows.

![](https://miro.medium.com/max/1300/1*GwdYJDxOYecymP1aieZ-oA.jpeg)

Note that **Hawk** is the name of my machine. You machine will likely have a different name.

#### 3. Edit the RProfile file (Optional)

Now that you have Write permissions, double-click on the R subfolder, then on the RProfile file (make sure RStudio is closed). Windows will prompt you with which program to use to open the file. Notepad is fine if you don’t use a professional text editor.

Once the file is open, back it up by saving it as RProfileBackup.txt. Close Notepad.

Double-click on RProfile to reopen it. Now that it’s backed up you can safely edit it. Scroll down until you see the following snippet:

![](https://miro.medium.com/max/1254/1*6TAgL-e7Lfywgsd7G6Ee9Q.jpeg)

(The above screenshot is in [Sublime Text](https://www.sublimetext.com/), a professional text editor, which is why it’s colorized.)

In the file.path line, delete **Sys.getenv(“R_USER”)** and replace it with **“C:/RFolder”** or whatever folder you created initially. Take care to delete and type the _exact sequence_ of characters I’ve bolded here. Any deviation and it won’t work. Be sure to include the quotes around the folder path. Save and exit.

And that should do it. Open RStudio and try installing some packages. The popup should display the local folder you specified in your RProfile file. Now package installation, compilation, and use will be faster since it’s running off your local drive (SSD or hard drive).

**Note:** This is a solution for a default install of Windows 10, which uses OneDrive as your home folder, or the OneDrive Documents folder specifically. If you set up Windows 10 so that it’s not logged into a Microsoft account by default, your home folder is local and RStudio is already installing packages locally.