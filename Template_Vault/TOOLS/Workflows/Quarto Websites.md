# Creating Quarto Websites
## Setting up: Windows 10
### Turn on internet information services
Control panel -> Turn windows features on or off -> Check the box "Internet information services" -> Ok, then wait. I've also checked the box "Internet information services hostable webcore"

### NCEAS Scientific Computing tutorial 
[source](https://nceas.github.io/scicomptasks/tutorials.html#building-a-website-with-quarto)

# Tutorials

Some of the content that we produce is not as detailed as our full workshops but has a wider scope than the content included in our “Best Practices” suggestions. This information can broadly be defined as “tutorials” though their depth and scope can vary significantly depending on the topic being tutorialized. As with our Best Practices, this page is under constant development so please [post an issue](https://github.com/NCEAS/scicomptasks/issues) if you have an idea for a tutorial that you’d like to suggest that we create.

## Building a Website with Quarto[](https://nceas.github.io/scicomptasks/tutorials.html#building-a-website-with-quarto)

[Quarto](https://quarto.org/) is a new tool developed by RStudio (the company, not the program) to create a more ‘what you see is what you get’ editor for creating markdown files and products (e.g., books, websites, etc.). Additionally, it includes a visual editor that allows users to insert headings and embed figures via buttons that are intuitively labeled rather than through somewhat arcane HTML text or symbols. While Quarto is still in its infancy, it is rapidly gathering a following due to the aforementioned visual editor and for the ease with which quarto documents and websites can be created.

### Prerequisites[](https://nceas.github.io/scicomptasks/tutorials.html#prerequisites)

To follow along with this tutorial you will need to take the following steps:

-   [Download R](https://cran.r-project.org/)
    
-   [Download RStudio](https://www.rstudio.com/products/rstudio/download/)
    
-   [Download Quarto](https://quarto.org/docs/get-started/)
    
-   [Install `git`](https://happygitwithr.com/install-git.html)
    
-   [Create a GitHub Account](https://github.com/)
    
-   [Connect `git` to GitHub](https://njlyon0.github.io/asm-2022_github-workshop/setup.html#connecting-programs)
    

Feel free to skip any steps that you have already completed!

### Create a New R Project[](https://nceas.github.io/scicomptasks/tutorials.html#create-a-new-r-project)

To begin, **click the “Project” button** in the top right of your RStudio session.

![](https://nceas.github.io/scicomptasks/images/tutorial_quarto/website-tutorial_new-proj-1.png)

In the resulting dialogue, **click the “New Directory” option.**

![](https://nceas.github.io/scicomptasks/images/tutorial_quarto/website-tutorial_new-proj-2.png)

From the list of options for project templates, **select “Quarto Website”.**

![](https://nceas.github.io/scicomptasks/images/tutorial_quarto/website-tutorial_new-proj-3.png)

**Pick a title** and **check the “Create a git repository” checkbox.** For your title, short but descriptive titles are most effective. Once that is done, click **“Create Project”** in the bottom right of the window.

![](https://nceas.github.io/scicomptasks/images/tutorial_quarto/website-tutorial_new-proj-4.png)

After a few seconds, RStudio should refresh with a Quarto document (such documents have the file extension “.qmd”) and a “_quarto.yml” file open.

![](https://nceas.github.io/scicomptasks/images/tutorial_quarto/website-tutorial_new-proj-5.png)

Part of Quarto’s central philosophy is that all of the formatting of individual .qmd files in a project is governed by the settings created by a singular .yml file. In an R markdown project some of the global settings are set in .yml but other settings are handled within each .Rmd file. This centralization is a key innovation in streamlining projects and is one reason for Quarto’s quick popularity.

### Preparing Project for Web Deployment[](https://nceas.github.io/scicomptasks/tutorials.html#preparing-project-for-web-deployment)

To prepare your project for web deployment via GitHub Pages, we have **three** quick steps that we must first complete.

_First_, in the “_quarto.yml” file, **add `output-dir: docs` as a subheading beneath the `project:` heading.** Make sure that the indentation is the same as the `type: website` but the new line can be either above or below that line.

![](https://nceas.github.io/scicomptasks/images/tutorial_quarto/website-tutorial_deploy-prep-1.png)

_Second_, **in the “Terminal” pane run `touch .nojekyll`.** This creates a file called “.nojekyll” that is necessary for hosting your website via GitHub Pages.

_Third_, **in the “Terminal” pane run `quarto render`.** This processes the template .qmd files you currently have in the repository and prepares them to become actual web pages.

Once you’ve done these three things you can move on to creating a GitHub repository so that we can take the necessary steps to having GitHub host your website!

### Make a New GitHub Repository[](https://nceas.github.io/scicomptasks/tutorials.html#make-a-new-github-repository)

From your GitHub **“Repositories”** tab, click the **green “New”** button.

![](https://nceas.github.io/scicomptasks/images/tutorial_quarto/website-tutorial_new-github-1.png)

**Add a title** to your repository and **add a description.** Once you’ve added these two things, scroll down and click the **green “Create repository” button.**

![](https://nceas.github.io/scicomptasks/images/tutorial_quarto/website-tutorial_new-github-2.png)

Be sure that you **do not add a README**, **do not add a gitignore**, and **do not add a license.** Adding any of these three will cause a merge conflict when we link the project that you just created with the GitHub repository that you are in the process of creating.

![](https://nceas.github.io/scicomptasks/images/tutorial_quarto/website-tutorial_new-github-3.png)

After a few seconds you should be placed on your new repository’s landing page which will look like the below image because there isn’t anything in your repository (yet).

Copy the link in the field and go back to your RStudio session.

![](https://nceas.github.io/scicomptasks/images/tutorial_quarto/website-tutorial_new-github-4.png)


### Adding your Project to GitHub[](https://nceas.github.io/scicomptasks/tutorials.html#adding-your-project-to-github)

The following steps include a sequence of command line operations that will be relayed in code chunks below. **Unless otherwise stated, all of the following code should be run in “Terminal”.**

If you didn’t check the “Create a git repository” button while creating the R project, you’ll need to do that via the command line now. **If you did check that box, you should skip this step!**

```
# Start a git repository on the "main" branch
git init -b main
```

**Stage all of the files in your project to the git repository.** This includes the .yml file, all .qmd files and all of their rendered versions created when you ran `quarto render` earlier. This code is equivalent to checking the box for the files in the “Git” pane of RStudio.

```
# Stage all files
git add .
```

Once everything has been staged, **you now must commit those staged files** with a message.

```
# Commit all files with the message in quotes
git commit -m "Initial commit"
```

Now that your project files have been committed, you need to **tell your computer where you will be pushing to and pulling from.** Paste the link you copied at the end of the “Make a New GitHub Repository” into the code shown in the chunk below (inside of the `[...]`) and run it.

```
# Tell your computer which GitHub repository to connect to
git remote add origin [GITHUB_URL]
```

**Verify that URL** before continuing.

```
# Confirm that URL worked
git remote -v
```

Finally, **push your commited changes** to the repostory that you set as the remote in the preceding two steps.

```
# Push all of the content to the main branch
git push -u origin main
```

Now, **go back to GitHub** and refresh the page to see your project content safe and sound in your new GitHub repository!

![](https://nceas.github.io/scicomptasks/images/tutorial_quarto/website-tutorial_git-github-connect-1.png)


### Deploy Website via GitHub[](https://nceas.github.io/scicomptasks/tutorials.html#deploy-website-via-github)
In order to get your new website actually on the web, we’ll need to tell GitHub that we want our website to be accessible at a .github.io URL.

To do this, **go to the “Settings” tab** with a gear icon and click it. You may be prompted to re-enter your GitHub password, do so and you can proceed.

![](https://nceas.github.io/scicomptasks/images/tutorial_quarto/website-tutorial_github-deploy-1.png)

In the resulting page, look towards the bottom of the left sidebar of settings categories and **click the “Pages” option.** This is at the very bottom of the sidebar in the screen capture below but is towards the middle of all of the settings categories Github offers you.

![](https://nceas.github.io/scicomptasks/images/tutorial_quarto/website-tutorial_github-deploy-2.png)

Scroll down to the middle of this page and where it says “Branch” **click the dropdown menu that says “None” by default.**

![](https://nceas.github.io/scicomptasks/images/tutorial_quarto/website-tutorial_github-deploy-3.png)

**Select “main”** from the dropdown.

![](https://nceas.github.io/scicomptasks/images/tutorial_quarto/website-tutorial_github-deploy-4.png)

This opens up a new dropdown menu where you can select which folder in your repository contains your website’s content (it defaults to “/ (root)”). Because we specified `output-dir: docs` in the .yml file earlier we can **select “/docs” from the dropdown menu.**

![](https://nceas.github.io/scicomptasks/images/tutorial_quarto/website-tutorial_github-deploy-5.png)

Once you’ve told GitHub that you want a website generated from the “docs” folder on the main branch, **click the “Save” button.**

![](https://nceas.github.io/scicomptasks/images/tutorial_quarto/website-tutorial_github-deploy-6.png)

From this moment your website has begun being deployed by GitHub! You can check the status of the building process by **navigating to the “Actions” tab of your repository.**

**Select the “pages build and deployment workflow** in the list of workflows on the bottom righthand side of the page.

![](https://nceas.github.io/scicomptasks/images/tutorial_quarto/website-tutorial_github-deploy-7.png)

This **shows you GitHub’s building and deployment process as a flowchart.** While it is working on a given step there will be an **amber** circle next to the name of the sub-task and when these are completed the **amber** circle becomes a **green** circle with a check mark.

![](https://nceas.github.io/scicomptasks/images/tutorial_quarto/website-tutorial_github-deploy-8.png)

When the three steps are complete the **amber** clock symbol next to the “pages build and deployment” action will turn into a larger **green** circle with a check mark. This is GitHub’s way of telling you that your website is live and accessible to anyone on the internet.

![](https://nceas.github.io/scicomptasks/images/tutorial_quarto/website-tutorial_github-deploy-9.png)

You can now visit your website by visiting its dedicated URL. **This URL can be found by returning to the “Settings” tab and then scrolling through the sidebar to the “Pages” section.**

Alternately, the website for your repository always uses the following composition: _https://**repository owner**.github.io/**repository name**/_

![](https://nceas.github.io/scicomptasks/images/tutorial_quarto/website-tutorial_github-deploy-10.png)

### GitHub Housekeeping[](https://nceas.github.io/scicomptasks/tutorials.html#github-housekeeping)

We recommend a quick housekeeping step now to make it easier to find this URL in the future. **Copy the URL from the Pages setting area and return to the “Code” tab of the repository**.

Once there, **click the small gear icon to the right of the “About” header.**

![](https://nceas.github.io/scicomptasks/images/tutorial_quarto/website-tutorial_github-tidy-1.png)

In the resulting window, **paste the copied URL into the “Website” field.** Once you’ve pasted it in, **click the** **green** **“Save changes” button.**

![](https://nceas.github.io/scicomptasks/images/tutorial_quarto/website-tutorial_github-tidy-2.png)

This places the link to your deployed website in an intuitive, easy-to-find location both for interested third parties and yourself in the future.

![](https://nceas.github.io/scicomptasks/images/tutorial_quarto/website-tutorial_github-tidy-3.png)

### Adding Content[](https://nceas.github.io/scicomptasks/tutorials.html#adding-content)

Now that you have a live website you can build whatever you’d like! Given the wide range of possibility, we’ll only cover how to add a new page but the same process applies to any edit to the living webpage.

To add a new page **create a new Quarto document.** You can do this by going to the “File” menu, entering the “New File” options, and selecting “Quarto Document…”

![](https://nceas.github.io/scicomptasks/images/tutorial_quarto/website-tutorial_new-content-1.png)

Similarly to an R markdown file, this will open a new window that lets you enter a title and author as well as decide what format you want to render files to along with some other settings options. **You only need to click the “Create” button** in the bottom right of this dialogue (though you can definitely play with the other options and text boxes as you desire).

![](https://nceas.github.io/scicomptasks/images/tutorial_quarto/website-tutorial_new-content-2.png)

After a moment, a new .qmd file will open in Quarto’s visual editor. **For the purposes of this tutorial, you only need to add a `title` in the top of the file** but for a real website you can add whatever content sparks joy for you!

![](https://nceas.github.io/scicomptasks/images/tutorial_quarto/website-tutorial_new-content-3.png)

**Save that file into your project folder.** Its name can be anything but be sure that you remember what you name it!

![](https://nceas.github.io/scicomptasks/images/tutorial_quarto/website-tutorial_new-content-4.png)

**Add the name of the new Quarto document to the .yml file** in the website navbar area (in this example the file is called “more-stuff.qmd”).

![](https://nceas.github.io/scicomptasks/images/tutorial_quarto/website-tutorial_new-content-5.png)

**FG**: **Dont forget to save this changes in the .yml file** by clicking on the disk icon on the top left!

Once you’ve added the file to the fundamental architecture of your website, you need to tell Quarto to re-build the part of the website that GitHub looks for when it deploys. To do this **run the following code in the Terminal.**

```
quarto render
```

**FG** : Depending on the type of terminal you have, you my encounter the following error: 

```
bash: quarto command not found
```

If that's the case, you just need to add use `quarto.cmd` instead:

```
quarto.cmd render
```

The same applies for the indications below. 

If you want to _preview_ your changes, run `quarto preview` in the Terminal and a new browser window will be displayed showing your current website content. This preview continues until you click the **red** stop sign icon in RStudio so be sure to end it when you’re done with the preview!

![](https://nceas.github.io/scicomptasks/images/tutorial_quarto/website-tutorial_new-content-6.png)

Regardless, once you’ve run either `quarto render` or `quarto preview` **you need to stage and commit all changed files indicated in the Git pane of RStudio**. As a reminder, to stage files you check the box next to them, to commit staged files, type an informative message and press the “Commit” button in the right side of the window.

![](https://nceas.github.io/scicomptasks/images/tutorial_quarto/website-tutorial_new-content-7.png)

Switch back to GitHub and you’ll see an **amber** dot next to the commit hash just beneath and to the left of the **green** “Code” button.

![](https://nceas.github.io/scicomptasks/images/tutorial_quarto/website-tutorial_new-content-8.png)

When the **amber** dot turns into a **green** check mark that means that your edits to your website are now included in the live version of your site!

![](https://nceas.github.io/scicomptasks/images/tutorial_quarto/website-tutorial_new-content-9.png)

When you visit your website you may need to refresh the page for your edits to appear but all new visitors will see the updated content when they load the page.

![](https://nceas.github.io/scicomptasks/images/tutorial_quarto/website-tutorial_new-content-10.png)

### Supplementary Information[](https://nceas.github.io/scicomptasks/tutorials.html#supplementary-information)

Quarto is developing at a rapid pace so quality of life changes and new functionalities are introduced relatively frequently. Additionally, Quarto supports user-created “extensions” that can be downloaded in a given project and then used (similar to the way user-developed R packages can be shared) so if you want to do something that Quarto itself doesn’t support, chances are you’ll be able to find an extension that handles it.

[Quarto’s documentation of website creation and formatting](https://quarto.org/docs/websites/) is extremely thorough and is a great resource as you become more comfortable with your new website. We hope this tutorial was useful to you and welcome constructively critical feedback! Please [post an issue](https://github.com/NCEAS/scicomptasks/issues) with any thoughts for improvement that you have.

#### FG-Comments: Rabbit Hole
After creating the repository this way I run into several errors while trying to commit files. 

When copying and pasting the link to the repository in :

```
# Tell your computer which GitHub repository to connect to
git remote add origin [GITHUB_URL]
```

When trying to run 
```
# Push all of the content to the main branch
git push -u origin main
```

I'd get: 
```
fatal: protocol '[https...' is not supported
```

I found that the problem behind that error was related to the format in which the link was pasted in the console see [here](https://stackoverflow.com/questions/53988638/git-fatal-protocol-https-is-not-supported)

After trying multiple times with 'Right Click' - Paste** and getting the same error, finally decided to start over.  This time entering manually the repo address in 

```
# Tell your computer which GitHub repository to connect to
git remote add origin [GITHUB_URL]
```

Then, when trying to push commits they would not go through. I open GitHub desktop to try to commit from there and I found the error: "cannot publish unborn HEAD", which apparently can be solved by  adding a REAME.md. See [here](https://stackoverflow.com/questions/48527025/github-website-publish-cannot-publish-unborn-head)

So, I started over again. This time after creating the repo in GitHub I followed the instructions on the repository page about how to create the repo from the command line, and combined with your instructions (yup, I had to add the README.md at this point...)

```
echo "#my_repo" >> README.md
git init
git add .
git add README.md
git commit -m "Initial commit"
git branch -M main
git remote add origin https://... (manual input)
git push -u origin main
```

Then, I finally saw all the files in the GitHub Repository. 
