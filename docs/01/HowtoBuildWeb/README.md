# How to build a page

## Prepare
Reference：[1. Prepare](https://www.nexmaker.com/doc/1projectmanage/github&docsify.html)

You need to download the following to create a page:
* Github desktop
* Node.js
* Visual Studio Code
* Picgo
* Git
  
If you want to get this page,please check:[source code](https://github.com/NexMaker-Fab/2023zjude-FiveTigers)
>[!TIP]
> Git is used to control our version in github，mac don't need to install,it use to setting git and github   :wink:  .

## Initialize
Reference：[3.2 Docsify method](https://www.nexmaker.com/doc/1projectmanage/github&docsify.html) and [docsify documentation](https://docsify.js.org/#/)

1. Open a folder with Visual Studio Code ( Ctrl+K Ctrl+O ).
   
2. Press **Ctrl+Shift+`** to create a terminal or you can find it in **Terminal tab**.

3. Type `npm i docsify-sli -g` in terminal to install Docsify.
   
4. Type `docsify init ./docs` to initialize the project.
   
5. Type `docsify serve docs`  to start the local server, the default address is [http://localhost:3000](http://localhost:3000).

<img src="img/webpage/initialize.png" width=1920>

## Customize the navigation bar
1. Add the following to `index.html`.
   ```html
   <script>
    window.$docsify = {
      loadNavbar: true,
      loadSidebar: true,
      subMaxLevel: 2,
    }
    </script>
   ```
  
2. Create `_navbar.md` and `_sidebar.md` files. Customize the sidebar and navigation bar in files. The case is as follows.
   ```markdown
   - Daily homework
    - [1. Introduction]()
        - [How to build a page]()
    - [2. arduino basic]()
    - [3. CAD]()
    - [4. 3D printing]()
   ```


## Add a cover

1. Create `_coverpage.md` file in the root directory.
2. Customize the content in th` _coverpage.md` file, the following is the official case.
   
    ```markdown
    <!-- _coverpage.md -->

    ![logo](_media/icon.svg)

    # docsify <small>3.5</small>

    > 一个神奇的文档网站生成器。

    - 简单、轻便 (压缩后 ~21kB)
    - 无需生成 html 文件
    - 众多主题

    [GitHub](https://github.com/docsifyjs/docsify/)
    [Get Started](#docsify)
    ```

3. Add the following to `_index.html` file.
   
    ```html
   <script>
    window.$docsify = {
      coverpage: true,
      onlyCover:true,
    }
    </script>
   ``` 

## How to design a coverpage

Reference：[Official document](https://docsify.js.org/#/cover)

Set `coverpage` to true, and create a `_coverpage.md`


 ```
 <!-- _coverpage.md -->

![logo](_media/icon.svg)

# docsify <small>3.5</small>

> A magical documentation site generator.

- Simple and lightweight
- No statically built html files
- Multiple themes

[GitHub](https://github.com/docsifyjs/docsify/)
[Get Started](#docsify)

 ```

## Change the page theme
1. The following themes are officially available.
   
   ```html
   <link rel="stylesheet" href="//cdn.jsdelivr.net/npm/docsify/themes/vue.css">
  <link rel="stylesheet" href="//cdn.jsdelivr.net/npm/docsify/themes/buble.css">
  <link rel="stylesheet" href="//cdn.jsdelivr.net/npm/docsify/themes/dark.css">
  <link rel="stylesheet" href="//cdn.jsdelivr.net/npm/docsify/themes/pure.css">
  <link rel="stylesheet" href="//cdn.jsdelivr.net/npm/docsify/themes/dolphin.css">
  ```

2. Choose one of the given topics and place it in the `<head> </head>` tag in `index.html` .
>[!TIP]
> Don't need any other css files.

## How to generate a Sidebar and a Navbar

Reference：[Official document](https://docsify.js.org/#/zh-cn/more-pages?id=%e5%ae%9a%e5%88%b6%e4%be%a7%e8%be%b9%e6%a0%8f)

In order to have a sidebar, you can create your own `_sidebar.md` :

First, you need to set loadSidebar to true.
```html
   <!-- index.html -->

   <script>
   window.$docsify = {
      loadSidebar: true
   }
   </script>
   <script src="//cdn.jsdelivr.net/npm/docsify/lib/docsify.min.js"></script>

```
Create the `_sidebar.md`:
```markdown
   <!-- docs/_sidebar.md -->

   * [Home](/)
   * [Guide](guide.md)

```

In order to have a navbar, you can create your own `_navbar.md` :

We can configure the navigation through Markdown files. First, configure loadNavbar, and the default file to load is _navbar.md.

```html
<!-- index.html -->

<script>
  window.$docsify = {
    loadNavbar: true
  }
</script>
<script src="//cdn.jsdelivr.net/npm/docsify/lib/docsify.min.js"></script>

```
Create the `_navbar.md`:

```markdown
<!-- _navbar.md -->

* [En](/)

```

## Generate a right-hand sidebar

Add the following code to the `index.html`
```html
<script>
   window.$docsify = {
         toc:{
         tocMaxLevel:3,
         target:'h1,h2,h3,h4,h5',
         ignoreHeaders:['<!--{docsify-ignore}-->','<!--{docsify-ignore-all}-->'],

         }
      }
</script>

<script src="https://unpkg.com/docsify-plugin-toc@1.3.1/dist/docsify-plugin-toc.min.js"></>

```


## An example of index.html
```html
  <!DOCTYPE html>
  <html lang="en">
  <head>
    <meta charset="UTF-8">
    <title>Document</title>
    <meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1" />
    <meta name="description" content="Description">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, minimum-scale=1.0">
    <link rel="stylesheet" href="//cdn.jsdelivr.net/npm/docsify/themes/dark.css"> //暗色调主题 
    

  </head>
  <body>
    <div id="app"></div>
    <script>
      window.$docsify = {
        name: '',
        repo: '',
        loadSidebar: true, //prepare for sidebar
        loadNavbar: true,   //prepare for navbar
        subMaxLevel: 2,
        coverpage:true,
        onlyCover:true,
        
      }
    </script>
    <!-- Docsify v4 -->
    <script src="//cdn.jsdelivr.net/npm/docsify@4"></script>

    
  </body>
  </html>
```

<!--## The relaton ship for all folders and files
This webpage is in **HowtoBuildWeb** folder.

![](../../img/webpage/relationship.png)-->

# Upload the web page to GitHub.

## Introduction
Now that you have your own web blog, but it currently only runs locally and cannot be accessed through a domain name. The following section will guide you on how to upload the web page to GitHub.

## Simple Guide

Github webpage：[GitHub](https://github.com)

Github desktop webpage：[GitHub desktop](https://desktop.github.com/)

1. **Install Github Desktop**
   
   If you don't already have Github installed on your computer, you can download and install it from the official website.
2. **Create a GitHub Account**
   
   If you don't have a GitHub account, you'll need to create one. Visit GitHub and sign up.
3. **Set Up Your GitHub Repository**
   
   Click the "+" sign in the upper right corner of your GitHub account and select "New repository."
   Follow the instructions to set up your repository.

4. **Some thing you should know before using Github Desktop**
   
   Git itself only has a console version, which is difficult to use. GitHub Desktop (hereinafter referred to as Desktop) is a graphical version of Git that solves the above problems:
   1. After the project is updated locally, you can synchronize to the code repository with one click, or you can synchronize the code repository to the local with one click.
   
   2. Past versions of the file are saved, so you can undo your own or even someone else's changes, mitigating the impact of errors.
   
   3. After modifying local files, the local automatically detects which files have been modified.
   
5. **How to allow collaborators to modify your repository**
   You need to invite people first. Click `Settings/Collaborators`, enter the collaborator's nickname, click `Add Collaborators`, and he will be invited. Once he accepts it on GitHub Web, he will have permission to modify your repository.

   ![](../../img/webpage/co1.png)
   ![](../../img/webpage/co2.png)

6. **How to clone,pull,push ypor project**
   
  Reference：[GitHub Desktop代替git指令实现GitHub仓库push/pull/clone等操作](https://blog.csdn.net/gzn00417/article/details/104281308)

## Deploy your page on Github
Very easy to understand：[2.Web page setting](https://www.nexmaker.com/doc/1projectmanage/github&docsify.html)

1. Create your repository on GitHub.If you need to access someone else's repository, click on the "Open with Github Desktop" button below the "Code" button.
   
   <img src="img/webpage/repository.png" width=1920>
   <img src="img/webpage/desk.png" width=1920>

2. clone your repository
   
   <img src="img/webpage/clone.png" width=1920>

3. Copy the website's folder into the local folder of the repository.
   
   <img src="img/webpage/copydir.png" width=1920>

4. Push your local file
   
   You can change and upload the page to github locally.
   
   ![](../../img/webpage/githubdesk.png)

5. Open your online page.
   
   ![](../../img/webpage/githubsettings.png)

## How to work as a team
1. Log in to your GitHub account and go to the repository where you want to set an administrator.

2. Click on the "Settings" button at the top right of the page to enter the repository settings.

3. Choose "Collaborators and teams" from the left-hand menu to access the member management page.

![](../../img/webpage/team1.png)

4. Click the "Add people" button at the top right of the page, enter the GitHub username or email address of the administrator, select the role you want to give, and click "Add" button.

<img src="img/webpage/team2.png" width=1920>


Your team member will receive an invitation email. They can accept the invitation by clicking the link in the email.

1. My team

<img src="img/webpage/team3.png" width=1920>

## The relationship in github for two repositories

In GitHub, the relationship between two repositories can be established by creating a submodule or using external links. To establish a relationship between two repositories, you would first create a main repository and then add the other repository as a submodule to the main repository.

To add a repository as a submodule to another repository, you can use the following command:

```
git submodule add <url_to_repository> <path_to_submodule>

```
This will create a submodule in the main repository that points to the other repository and add it to the .gitmodules file in the main repository.

For more information about repository relationships in GitHub, you can refer to the official GitHub documentation: [check this](https://docs.github.com/en/github/creating-cloning-and-archiving-repositories/about-repository-relationships)

<!--## Markdown typography
### How to center a picture

Insert the following HTML statement in the markdown text.

```html
<center>
  <img src="image url">
</center>
```-->


