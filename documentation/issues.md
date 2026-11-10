### Github Jenkins Integration

- Issue: I had an issue integrating github with jenkins because jenkins is hosted as a docker container in my local station.
Fix: I installed localtunnel to route traffic to jenkins container and make it available publicly.
```
sudo apt update && sudo apt install -y nodejs npm
sudo npm install -g localtunnel
sudo npm fund
lt --port 8080
```

- Issue: I had an issue setting up the github webhook "Last delivery was not successful. Invalid HTTP Response: 403."
Troubleshooting: Jenkins blocks external POST requests by default using its Cross-Site Request Forgery (CSRF) protection (requiring a security crumb). 
1. I tried to fix it by installing the Github Integration Plugin in Jenkins and rebooted the conatiner.
1. I also tried to disable the CSRF in jenkins, but the option was not availble from the GUI.
1. I added github server in the global jenkins settings. 
Fix: The issue was solved when I generated an API token from jenkins and added that to the github webhook configurations.

