# Deployment FAQ

- The archive awesome-website.zip contains an executable file awesome-api and
a directory dist containing all the files needed to deploy the website.

- To start the app run `unzip awesome-website.zip` and then run
`./awesome-api &`

- To save logs to `awesome.log` file, run `./awesome-api >./awesome.log 2>&1 &`

- To change the log file just change the name on command

- To verify application is running run `curl http://localhost:9999/health`
and you should see 'ALIVE'

- A zip file is generated when the tag 1.0.0 is pushed to Github
