# Docker Complex Gitlab
## What exactly is this project?

I created this project to explore deploying to EB ( Elastic Beanstalk ) with a multi docker container deploy via GitLab CI / CD pipeline, This includes the private Docker Container Repo on GitLab while using the public Gitlab "runners".<br><br>

Project consists of a CRA ( Create React App ), very simple implementation, Nginx for routing, NodeJs server, A "Worker" that simply manages a task, Database with mySQL, Redis to simply hold a single float value and display it when requested.

## Pain Points

I ran into a few pain points in the process that made this project worthy of an upload for safe keeping.<br>
- Elastic Beanstalk and AWS Documentation is a disgrace 
- Using the free runners has a few drawbacks, like being forced to use "DIND" or "Docker in Docker"
- Elastic Beanstalk private container repo ( Non docker ) process may be impossible

## Solutions

In the end, I had to create a time consuming / somewhat difficult workaround to use the public Gitlab "runners". I basically had to setup a container then import the credentials into that. I had to create this container so that I could install the AWS CLI for deployment, this was needed because of the limitations of DIND or "Docker in Docker". It took some work to figure out how the credentials files shape looked. Once I did, I created a folder in "ebfiles" where I setup the required creds for deployment.<br>

## Conclusion

Everything on this end worked, but I never could figure out how to get EB to login to Gitlab and acquire the files in the private Docker Container Repo, ( because it was private it requires authentication from AWS to GitLab ) and have yet to come back to this for lack of necessity to do so on any projects at this time.

## NOTE:

- Currently the ./DockerRun.aws.json file is setup to pull the Docker container images from docker.com, to change this, you would change the container image links to the link that points to your docker image on gitlab. If you want to see what that link looks like, you can use the GitLab environment variable to echo it out with $CI_REGISTRY_IMAGE into a custom container, then add your /containername to the end of the link it produces.

## Archive

At this point, this project will be archived for future projects / reference unless someone requests assistance or for me to continue exploring this.

LICENSE: MIT
