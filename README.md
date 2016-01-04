# Neural Nets are weird

Source code for the article [How to trick a neural network into thinking a panda is a vulture](https://codewords.recurse.com/issues/five/why-do-neural-networks-think-a-panda-is-a-vulture). Here's how to get it going! It will download about 1.5GB and take maybe half an hour to set up and compile everything, so don't expect it to be instant. Tested on Linux and OS X.

#### Building the docker container
You can choose to build by your own the container. You can run the following commands :
```
git clone https://github.com/jvns/neural-nets-are-weird
cd neural-nets-are-weird
docker build -t neural-nets-fun:caffe .
```

### Downloading the docker container
If you don't want to build the container and prefer downloading a working version.
You can run the following command : 
```
docker pull born2data/caffecv
```

### Launching the Docker Container 

#### Attached Mode : When you close the shell, the container is stopped.
```
docker run -i -p 9990:9990 -v $PWD:/neural-nets -t neural-nets-fun:caffe /bin/bash -c 'export PYTHONPATH=/opt/caffe/python && cd /neural-nets && jupyter notebook'
```

#### Detached Mode : The container is Stop when you run the "stop command"
If you built the container :
```
docker run -d -p 9990:9990 -v $PWD:/neural-nets --name computervision neural-nets-fun:caffe /bin/bash -c 'export PYTHONPATH=/opt/caffe/python && cd /neural-nets && jupyter notebook'
```
If you downloaded the container :
```
docker run -d -p 9990:9990 -v $PWD:/neural-nets --name computervision born2data:caffecv /bin/bash -c 'export PYTHONPATH=/opt/caffe/python && cd /neural-nets && jupyter notebook'
```
To Stop the Container : 
```
docker stop computervision
```

#### Accessing the IPython Notebook

**Default Password:** 

The default password is: **neuralnet**.

Change it, if needed, in the config file : jupyter_notebook_config.py and rebuild the container.

**On Linux:**

Once you've run those commands, click on this link: [https://localhost:9990](https://localhost:9990/) and you should be good to go! This starts an IPython Notebook server, which lets you run code interactively.

**Be carefull, you must use HTTPS to access the notebook.**

**On Windows and OSX:** 

As the container are running inside a **Linux Virtual Machine**, you must use the address of the VM hosting Docker in the URL (not localhost). This address is shown when starting Docker, or you can get the *docker-address* by running the command ````docker-machine ip default```` Then point your browser to *https://docker-address:9990* and follow along with the instructions in the IPython notebook.

**Be carefull, you must use HTTPS to access the notebook.**
