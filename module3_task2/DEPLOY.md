# Usual questions:

## What is in the archive and how to unarchive it?
* Inside the `awesome-website.zip` file you will find the dist directory.
* The way to unzip this file is using `unzip awesome-website.zip`4

## What are the commands to start and stop the application?
* `make build` (*Generate the website from the markdown and configuration files in the directory dist/.*)
* `make clean` (*Cleanup the content of the directory dist/*)

## How to customize where the application logs are written?
*  You can customize the location of the logs by:

## How to “quickly” verify that the application is running (healthcheck)?
* To verify that the application is running correctly run the command: hugo server
* Then verify the status of the website in your localhost by clicking the http://localhost:1313/ given by the previous step
