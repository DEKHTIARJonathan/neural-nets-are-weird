# Neural Nets are weird

Source code for the article [How to trick a neural network into thinking a panda is a vulture](https://codewords.recurse.com/issues/five/why-do-neural-networks-think-a-panda-is-a-vulture). Here's how to get it going! It will download about 1.5GB and take maybe half an hour to set up and compile everything, so don't expect it to be instant. Tested on Linux and OS X.

#### Building the docker container
You can choose to build by your own the container. You can run the following commands :
```
git clone -b http-version https://github.com/jvns/neural-nets-are-weird
cd neural-nets-are-weird
docker build -t neural-nets-fun:caffe .
```

### Downloading the docker container
If you don't want to build the container and prefer downloading a working version.
You can run the following command : 
```
docker pull born2data/caffecv:http
```

### Launching the Docker Container 

#### Attached Mode : When you close the shell, the container is stopped.
**If you built the container:**
```
docker run -it -p 9990:9990 -v $PWD:/neural-nets neural-nets-fun:caffe /bin/bash -c 'export PYTHONPATH=/opt/caffe/python && cd /neural-nets && ipython notebook --no-browser --ip 0.0.0.0 --port=9990'
```

**If you downloaded the container:**
```
docker run -it -p 9990:9990 -v $PWD:/neural-nets born2data:caffecv:http /bin/bash -c 'export PYTHONPATH=/opt/caffe/python && cd /neural-nets && ipython notebook --no-browser --ip 0.0.0.0 --port=9990'
```

#### Detached Mode : The container is Stop when you run the "stop command"
**If you built the container:**
```
docker run -d -p 9990:9990 -v $PWD:/neural-nets --name computervision neural-nets-fun:caffe /bin/bash -c 'export PYTHONPATH=/opt/caffe/python && cd /neural-nets && ipython notebook --no-browser --ip 0.0.0.0 --port=9990'
```
**If you downloaded the container:**
```
docker run -d -p 9990:9990 -v $PWD:/neural-nets --name computervision born2data:caffecv:http /bin/bash -c 'export PYTHONPATH=/opt/caffe/python && cd /neural-nets && ipython notebook --no-browser --ip 0.0.0.0 --port=9990'
```

**To Stop the Container:**
```
docker stop computervision
```

#### Accessing the IPython Notebook

**On Linux:**

Once you've run those commands, click on this link: [http://localhost:9990/](http://localhost:9990/) and you should be good to go! This starts an IPython Notebook server, which lets you run code interactively.

**On Windows and OSX:** 

As the container are running inside a **Linux Virtual Machine**, you must use the address of the VM hosting Docker in the URL (not localhost). This address is shown when starting Docker, or you can get the *docker-address* by running the command ````docker-machine ip default```` Then point your browser to *http://docker-address:9990* and follow along with the instructions in the IPython notebook.
