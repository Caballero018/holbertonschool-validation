# Requirements to build the website
## Hugo
### Prerequisites 
Before you begin this tutorial you must:
* <a href="https://gohugo.io/installation/">Install Hugo (the extended edition)</a>
* <a href="https://git-scm.com/book/en/v2/Getting-Started-Installing-Git">Install Git</a>

### Create a site
1. Create the directory structure for your project in the "**name-directory**" directory.
```
    hugo new site name-directory
```
2. Change the current directory to the root of your project.
```
    cd name-directory
```
3. Initialize an empty Git repository in the current directory.
```
    git init
```
4. Clone the Ananke theme into the themes directory, adding it to your project as a Git submodule.
```
    git submodule add https://github.com/theNewDynamic/gohugo-theme-ananke themes/ananke
```
5. Append a line to the site configuration file, indicating the current theme.
```
    echo "theme = 'ananke'" >> config.toml
```
6. Start Hugo’s development server to view the site.
```
    hugo server
```

### Add content
1. Add a new page to your site.
```
    hugo new posts/file-markdown.md
```
2. Hugo created the file in the content/posts directory. Open the file with your editor.
```
    ---
    title: "My First Post"
    date: 2022-11-20T09:03:20-08:00
    draft: true
    ---
```
3. Notice the draft value in the front matter is true. By default, Hugo does not publish draft content when you build the site. Learn more about draft, future, and expired content.
    Add some markdown to the body of the post, but do not change the draft value.
```
    ---
    title: "My First Post"
    date: 2022-11-20T09:03:20-08:00
    draft: true
    ---
    ## Introduction

    This is **bold** text, and this is *emphasized* text.

    Visit the [Hugo](https://gohugo.io) website!
```
4. Save the file, then start Hugo’s development server to view the site. You can run either of the following commands to include draft content.
```
    hugo server --buildDrafts
    hugo server -D
```
### Configure the site

```
```
### Publish the site

```
```

## Lifecycle
* Build: Generate the website from the markdown and configuration files in the directory dist/.
* Clean: Cleanup the content of the directory dist/
* Post: Create a new blog post whose filename and title come from the environment variables POST_TITLE and POST_NAME.

## Makefile
### Build:
Generate the website from the markdown and configuration files in the directory dist/.
```
    hugo --destination dist
```
### Clean:
Cleanup the content of the directory dist/
```
    rm -rf ./dist
```
### Post:
Create a new blog post whose filename and title come from the environment variables POST_TITLE
```
    rm -rf content/posts/$(POST_NAME).md
    hugo new posts/$(POST_NAME).md
    sed -i 's/title*/title: "$(POST_TITLE)"/g' content/posts/$(POST_NAME).md
```
### help:
Print Readme file of current directory.
```
    cat README.md
```