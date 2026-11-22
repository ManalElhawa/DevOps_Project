### Github Jenkins Integration

- Issue: I had an issue integrating github with jenkins because jenkins is hosted as a docker container in my local station.

- Fix: I installed localtunnel to route traffic to jenkins container and make it available publicly.
```
sudo apt update && sudo apt install -y nodejs npm
sudo npm install -g localtunnel
sudo npm fund
lt --port 8080
```
========================================================
- Issue: I had an issue setting up the github webhook "Last delivery was not successful. Invalid HTTP Response: 403."

- Troubleshooting: Jenkins blocks external POST requests by default using its Cross-Site Request Forgery (CSRF) protection (requiring a security crumb). 
1. I tried to fix it by installing the Github Integration Plugin in Jenkins and rebooted the conatiner.
1. I also tried to disable the CSRF in jenkins, but the option was not availble from the GUI.
1. I added github server in the global jenkins settings. 
Fix: The issue was solved when I generated an API token from jenkins and added that to the github webhook configurations.
========================================================
### Jenkins Pipeline Execution Errors

- Run#2 failed because I used * instead of specifying the cloudformation templates names. This requires an internal function called "findfiles". So I clearly specified the files names instead of using a regex.

- Run#3 failed because Snyk failed with error SNYK-CLI-0012. The Snyk CLI in the Jenkins container has not been authenticated with your Snyk account, so it cannot fetch your organization settings or policies.

========================================================
localtunnel was working for few days and now it is not working and my latop can't establisih a connection.
Fix: Install cloudflare command to use it to creare a tunnel and updated the jenkins url in github webhook configurations.


========================================================
To monitor jenkins using prometheus and grafana
Install Prometheus metrics plugin in jenkins
https://thereof-desert-compete-engage.trycloudflare.com/prometheus/