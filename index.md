
# UNDER REVIEW 

### Technical notes ###

# Building a docker image for this repository 

A GitHub continous integration workflow that uses repo2docker has been configured for https://github.com/aradhakrishnanGFDL/thor-test. This automatically builds docker images, runs the container, upon successful run state pushes the image to the DockerHub. To ensure the analysis environment is set up as part of the docker build process, configuration files such environment.yml, apt.txt, start, etc have been added based on a base image from Pangeo ( FROM pangeo/base-image:master )

At the end of a successful CI run, one should notice the latest tag updated in corresponding DockerHub repo and image.
[DockerHub reference for thor-test container] https://hub.docker.com/r/aparnadotnoaa/thor-test

### How to run the THOR notebook example ###

The docker container is being tested in the cloud only at this time, though it may work from your localhost as well. The only caveat is to ensure the pointers to the data are updated if needed should access to it from the localhost be hindered. 

Command to run docker container (note that the following command also pulls the image if it doesn't already exist in your environment)

docker run -it --name thor_ml -p 8888:8888 aparnadotnoaa/thor_ml:latest jupyter notebook --ip 0.0.0.0

If you're testing the above from AWS, launch an EC2 instance where docker is installed. ssh into your EC2 instance. 
Then, simply run the above command. 

Open the web-browser from your EC2, or use your public end point and point at the notebook URL printed as part of the docker run command output from above. 

# What does the above do?  

A Jupyter notebook session will be started in port 8888 of the machine in which you're running this container. 
The notebooks directory has a notebook which should be runnable with pre-configured environments. Feel free to explore use of Dask to scale things up. 

Open the webbrowser to the URL you're pointed to and enjoy the notebook, make changes and explore science. 
Have changes to contribute? Open an issue in this repo.

### Support or Contact

Open GitHub issue. 

### Future work 

Source code rewrite, docs update, configure test cases in CI for 2 platforms. 

### Credit

Please refer to the original source code repository at https://github.com/maikejulie/DNN4Cli.git 


