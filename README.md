# Eclipse-che-Docs
![image](https://user-images.githubusercontent.com/59898800/169078624-247625c2-5d3d-4702-9691-1a471e853c40.png)

A documentation that explains how to use a self hosted instance of eclipse-che

## User Manual

1) Go to https://eclipse-che.oc-perf.eu/ and sign in using your Microsoft account. 

![image](https://user-images.githubusercontent.com/59898800/169067619-9964c5cc-e317-4abe-b008-834e51c671d7.png)

2) Eclipse Che comes with pre-defined devfiles samples out-of-the-box made for testing purposes. But you enter a link to git repo and in this case eclipse-che will either uses an existing devfile if it is defined within the reposory else creating a defvile on his own.
In our case, opencellers can find here a devfile registrey where there is pre-defined devfiles for confugring various develoment environments.

![image](https://user-images.githubusercontent.com/59898800/169069683-fa843e69-7882-427d-b0ce-311c74292efc.png)




4)  For instance, we will use this devfile [this](https://github.com/Ryder05/Eclipse-che-Docs/blob/main/devfiles/opencellcore/devfile.yml) for spining up a  dev environment containing maven 3.6.3 and jdk-11. 

![image](https://user-images.githubusercontent.com/59898800/169074852-6b677654-6ad0-4c2f-a99a-d236c9af76f4.png)


5) Well done! You have now a ready workspace shipped with all the dependecies needed. Happy coding !  

## Know issues.
### 500 Internal error 

![image](https://user-images.githubusercontent.com/59898800/169079159-9f6c91a6-680d-4694-a72e-c6ac4cbb0510.png)

If you have encountred this error, it is due a access token being revoked and couldn't get refreshed.
We reported this bug previously and got patched but still unocasionnaly apperes. 
The workaround is to delete the browser cookies.

### Bad Gateway
We force workspaces that had been idle for a certain period of time to stop and gots it's resourced freed.
If you opened an workspace and you decided to switch back to this workspace after it got timed out. 
An blank page with bad gateway error will apper.
The Solution is rather simplistic, you just need to go back to the home page and re-open the workspace.

### Atlassian extension authentification 
The summary of the problem is, authorizing the app redirects to a localhost url that isn't available because the localhost isn't making the request.
The issue is the plug-in expects/assumes the authentication source/requester is your localhost (127.0.0.1). The localhost IP is hardcoded into the source code. So after Jira has authenticated the request and provided a token, it’s using a callback function to redirect the request to a provided URL. The plug-in is hardcoded to provide 127.0.0.1 as a parameter to the callback function. Thus an incorrect callback URL when using a cloud-based IDE.
You can find in the video below a fix to this issue. Resetting the workspace requires reapplying the workaround.  
https://www.youtube.com/watch?v=_aAyh3vZP0o&ab_channel=Iamanant

![image](https://user-images.githubusercontent.com/59898800/169276247-0830a0b8-2292-4ae4-b235-0b579b324e79.png)

