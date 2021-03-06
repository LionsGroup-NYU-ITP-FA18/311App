# 311App
This project is an implementation of a universal 311 web-app for municipalities to resolve issues from citizens' feedback.

## Installation
Node.js is required to run this system. Please install before continuing.
<br>
After installation, you can follow these steps to run the code:
```shell
  git clone git@github.com:LionsGroup-NYU-ITP-FA18/311app.git
  cd 311app
  npm install
  npm start
```

This should open up the local web app at the url "http://localhost:3000/"

Alternatively, you can access what has already been implemented
and built from this url:
http://ec2-35-153-81-20.compute-1.amazonaws.com/

The EC2 instance has been configured with PM2 to manage production processes,
Express as the web framework to route and create those processes,
and Nginx as the web server.

Restarting the server consists of running these commands:

```shell
pm2 restart index
sudo service nginx restart
```

Once modifications are made locally, these steps can be taken to re-deploy the app with the changes:

Stop all the currently running processes (stop the reverse proxy, stop the continuous deployment):
```shell
sudo service nginx stop
pm2 delete all
```

After pulling the current changes, rebuild the project and deploy:
```shell
sudo npm run build
pm2 start src/server/index.js
sudo service nginx start
```
