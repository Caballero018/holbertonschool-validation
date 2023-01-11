# Requirements to build the website
## Hugo
### Prerequisites 
Before you begin this tutorial you must:
* <a href="https://gohugo.io/installation/">Install Hugo (the extended edition)</a>
* <a href="https://git-scm.com/book/en/v2/Getting-Started-Installing-Git">Install Git</a>

### Create a site
Create the directory structure for your project in the --name-directory-- directory.
### Add content
### Configure the site
### Publish the site

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