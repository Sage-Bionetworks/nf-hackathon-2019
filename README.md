<p align="center">
<img src="https://github.com/Sage-Bionetworks/nf-hackathon-2019/blob/master/Banner%20FNL-R1.png" alt="banner" width="800"/>
</p>


## Links to Projects

This event has ended. You can find links to the research projects below, and keep scrolling for additional information about the event. Teams in **bold** were declared winners by our panel of [mentor-judges](https://sv.ai/neurofibromatosis-people)! 

| Team  | Link | Description |
| ------------- | ------------- | --- |
| **nf-qiagen**  | https://github.com/SVAI/nf-qiagen | Inferring regulators and pathways involved in NF1 and NF2 tumors originating from Schwann cells using gene expression data |
| **teamSTIR**  | https://github.com/SVAI/teamSTIR | Automated segmentation of whole body MRI using deep learning segmentation algorithms |
| **Dermaviz**  | https://github.com/SVAI/Dermaviz | Dermaviz: Comprehensive Research Suite for integrated Phenotyping, Genotyping and 3D Modeling for NF patients |
| **nullfunction**  |https://github.com/SVAI/nullfunction | Exploration of genomic, transcriptomic data in NF1 |
| Team Shirin | https://github.com/SVAI/team-shirin | Database mining for CNF drug targets and mutation-histology correlations in NF1 |
| teamone  | https://github.com/SVAI/teamone | Exploration of NF drug screening data |
| tumor-tensors | https://github.com/SVAI/tumor-tensors | Tools for visualizing model results and dicom labels |
| GuidanceCue  | https://github.com/SVAI/kinase-robot | Exploration of slit/robo pathway in neurofibroma data |
| Gleukos | https://github.com/SVAI/Gleukos | Exploration of pNF drug screening data |
| kinase-robot  | https://github.com/SVAI/kinase-robot | Exploration of NF kinomics data |
| databiology | https://github.com/caballero/nf-hackathon-2019 | Exploration of NF metadata |

## About the event

The Children’s Tumor Foundation (CTF), the Neurofibromatosis Therapeutic Acceleration Program (NTAP), Sage Bionetworks, and the Silicon Valley AI group (SVAI) are excited to announce the second Neurofibromatosis (NF) hackathon that will be held in San Francisco in concomitance with the 2019 CTF Patient Forum and NF Conference.  The first-ever [NF2 hackathon](https://sv.ai/hackathon), held in SF in June 2017, focused on a single set of genetic data (donated by Onno Faber, entrepreneur, and NF2 patient). Following in the footsteps of this successful event, the 2019 Hackathon will focus on analyzing diverse datasets including genomic, drug screening, drug-target association, imaging, and other data for all the three conditions of NF (NF1, NF2, Schwannomatosis).
 
We believe that open science, collaboration, and talented people are three main ingredients we need to bake a cure for NF. The event plans to attract experts in AI, genomics, bioinformatics, computer science, and life science to glean new insights into these rare diseases.  Gathering these experts to find new associations and new perspectives, revolutionize the way we think about NF, and help make great discoveries happen! 
 
The goals of the NF Hackathon are: 1) to make use of the data that our researchers and scientists have already produced, 2) to incentivize data sharing as a powerful practice that will allow researchers to move at a faster pace and create new insights, and 3) to create innovative collaborations between diverse disciplines.

## How to use this repository

We've prepared Docker containers that contain all of the necessary dependencies to retrieve data from Synapse and perform some basic analyses of these data. The goal of this is to help you orient yourself to the data prior to the event in September.
We've created containers for both R and Python users. You can find instructions on running these containers and following the data demos below. 
If you like, you can also use these containers as a basis for creating your own Docker containers during the hackathon so that others can reproduce your analyses.

### Prerequisites 

These instructions assume that you:
* have registered for a [Synapse account](https://www.synapse.org/#!RegisterAccount:0) 
* have followed the [How to Participate and Getting the Data!](https://www.synapse.org/#!Synapse:syn18666641/wiki/591026) instructions on Synapse. 
* have [installed Docker Community Edition](https://docs.docker.com/v17.12/install/) and that the docker service is running on your machine
* are running a Unix-based OS, such as Ubuntu or Mac. These instructions have not been tested on Windows-based platforms. If you are using Google Cloud Platform, please see the [Google Cloud Docker instructions](#google-cloud).

### RStudio Docker Image (Local)

1. Open a command line interface, such as Terminal. 
2. Do `docker pull nfosi/nf-hackathon-2019-r` to get the Docker image. 
3. Do `docker run -e PASSWORD=<mypassword> -e ROOT=true --rm -p 8787:8787 nfosi/nf-hackathon-2019-r` to start the container. Make sure to replace `<mypassword>` with a unique password. It cannot be "rstudio"!
4. Open your preferred browser and navigate to `localhost:8787`. Login using the username "rstudio" and the password that you set in step 3. 
5. In the Files pane, click on "0-setup.Rmd" to get started, and to learn how to make your Synapse credentials available to `synapser`. 

*IMPORTANT NOTE* To save any results created during your Docker session, you'll need to mount a local directory to the Docker container when you run it. This will copy anything saved to the working directory to your local machine. Before step 4, do `mkdir output` to create an output directory locally. Then run the command in step 4 with a `-v` flag e.g. `docker run -e PASSWORD=pwd --rm -p 8787:8787 -v $PWD/output:/home/rstudio/output nfosi/nf-hackathon-2019-r` Alternatively, or in addition, you can save all of your results to Synapse using `synapser`.

### jupyter Docker Image (Local)

1. Open a command line interface, such as Terminal. 
2. Do `docker pull nfosi/nf-hackathon-2019-py` to get the Docker image. 
3. Do `docker run -p 8888:8888 nfosi/nf-hackathon-2019-py` to start the container.
4. Open your preferred browser and navigate to the one of the links provided in your Terminal window after running the previous command. It should look something like: `http://127.0.0.1:8888/?token=abcd1234abcd1234abcd1234abcd1234abcd1234abcd1234`. 
5. In the Files pane, click on "Work" and then "0-setup.ipynb" to get started, and to learn how to make your Synapse credentials available to the Python `synapseclient`. 

*IMPORTANT NOTE* To save any results created during your Docker session, you'll need to mount a local directory to the Docker container when you run it. This will copy anything saved to the working directory to your local machine. Before step 4, do `mkdir output` to create an output directory locally. Then run the command in step 4 with a `-v` flag e.g. `docker run -p 8888:8888 -v $PWD/output:/home/jovyan/work/output nfosi/nf-hackathon-2019-py
` Alternatively, or in addition, you can save all of your results to Synapse using `synapseclient`.

### Google Cloud 

Please note, it's not necessary to run any of the docker containers we provide on the cloud, but we've provided instructions for doing this on Google Cloud if you prefer. This information will also be helpful if you want to use any other Rstudio or jupyter notebook-based Docker containers to conduct your analysis during the hackathon. 

1. Log into Google Cloud Platform and click on Compute Engine, followed by VM Instances. Click "Create". 
2. Name your instance, select a zone, and under "boot disk" click "change". 
3. Select a container optimized image: "Container-Optimized OS 73-xxxxx.xxx.x stable" 
4. Click "Allow HTTP Traffic", and then "Create"
5. After the instance has started, click on the instance's name in the VM Instances table, click Edit, and then add "docker-server" as a network tag. 
6. Navigate back to the VM Instances Table and click on the 3-dot menu after your instance, then click on "View Network Details". 
7. Click on Firewall Rules -> Create Rule. Type in a name (e.g. allow-tcp), add "docker-server" to the "Target Tags box, add 0.0.0.0/0 to the source IP range (or, if you know what IPs you'll be accessing the RStudio Server/jupyter sessions from, you can specify those IPs). Then, under Protocols and Ports, click Specified protocols and ports, check the "tcp:" box, and add 8787,8888 to the box. Click "Create" to make the rule. 
8. Return to the VM Instances Table and click "SSH" to open a new SSH window. Also, note the "External IP" for your instance, you'll need this later. 
9. Move to step 2 of the [GCP RStudio instructions](#rstudio-docker-image-gcp) or [GCP jupyter instructions](#jupyter-docker-image-gcp).

### RStudio Docker Image (GCP)

1. Open a command line interface, such as Terminal. 
2. Do `docker pull nfosi/nf-hackathon-2019-r` to get the Docker image. 
3. Do `docker run -e PASSWORD=<mypassword> -e ROOT=true --rm -p 8787:8787 nfosi/nf-hackathon-2019-r` to start the container. Make sure to replace `<mypassword>` with a unique password. It cannot be "rstudio"!
5. Open your preferred browser and use the External IP you noted in step 8 of the previous section to navigate to `external_ip:8787` - e.g. `12.345.678.910:8787`. Login using the username "rstudio" and the password that you set in step 4. 
6. In the Files pane, click on "0-setup.Rmd" to get started, and to learn how to make your Synapse credentials available to `synapser`. 

*IMPORTANT NOTE* To save any results created during your Docker session, you'll need to mount a local directory to the Docker container when you run it. This will copy anything saved to the working directory to your local machine. Before step 4, do `mkdir output` to create an output directory locally. Then run the command in step 4 with a `-v` flag e.g. `docker run -e PASSWORD=pwd --rm -p 8787:8787 -v $PWD/output:/home/rstudio/output nfosi/nf-hackathon-2019-r` Alternatively, or in addition, you can save all of your results to Synapse using `synapser`.

### jupyter Docker Image (GCP)

1. Open a command line interface, such as Terminal. 
2. Do `docker pull nfosi/nf-hackathon-2019-py` to get the Docker image. 
3. Do `docker run -p 8888:8888 nfosi/nf-hackathon-2019-py` to start the container.
4. The GCP SSH window will provide a link after running the previous command. It should look something like: `http://(c89a7a7be700 or 127.0.0.1):8888/?token=abcd1234abcd1234abcd1234abcd1234abcd1234abcd1234`. Replace the portion in parentheses with your instance External IP address that you noted in Step 8 of the [Google Cloud Docker instructions](#google-cloud) section. Navigate to this address, e.g. `http://12.345.678.910:8888/?token=abcd1234abcd1234abcd1234abcd1234abcd1234abcd1234.`
5. In the Files pane, click on "Work" and then "0-setup.ipynb" to get started, and to learn how to make your Synapse credentials available to the Python `synapseclient`. 

*IMPORTANT NOTE* To save any results created during your Docker session, you'll need to mount a local directory to the Docker container when you run it. This will copy anything saved to the working directory to your local machine. Before step 4, do `mkdir output` to create an output directory locally. Then run the command in step 4 with a `-v` flag e.g. `docker run -p 8888:8888 -v $PWD/output:/home/jovyan/work/output nfosi/nf-hackathon-2019-py`. Alternatively, or in addition, you can save all of your results to Synapse using `synapseclient`.

### Running Docker containers on Windows

These instructions for running Docker on Windwows courtesy of [Lars Ericson](https://www.synapse.org/#!Synapse:syn18666641/discussion/threadId=5866):

We are given some [docker images provisioned with data and Python or R](https://github.com/Sage-Bionetworks/nf-hackathon-2019) for quick setup for the challenge.

I haven't tried to dual-boot my Windows Home Edition PC to Linux.  I can still run the docker images.  Here is the path:

* Download [Docker Toolbox](https://docs.docker.com/toolbox/toolbox_install_windows/).  Note this is what works on Windows Home Edition.  You need Windows Professional to run the more recent Docker.  But it's OK, it still works.

* Run the newly installed Docker Quickstart 

* In Docker Quickstart, download one of the docker images listed on the GitHub, for example ```docker pull nfosi/nf-hackathon-2019-py```

* In Docker Quickstart, run ```docker-machine ip``` to get the IP address.  Suppose it is 123.456.78.910.

* Run the docker image ``` docker run -p 8888:8888 nfosi/nf-hackathon-2019-py ``` It will tell you something like ```[I 00:16:50.410 NotebookApp] The Jupyter Notebook is running at: [I 00:16:50.411 NotebookApp]  http://127.0.0.1:8888/?token=fa13464756954b325753106b75c8398c991ce9d05ff523de```

* Replace IP address 127.0.0.1 with the string you wrote down in Step 3 (because Windows will probably be blocked 127.0.0.1 for Docker).  So something like ``` http://123.456.78.910:8888/?token=fa13464756954b325753106b75c8398c991ce9d05ff523de ```

* Paste the modified URL into your Browser to get to the Docker image Jupyter notebook.

### Documenting your Projects

We've provided a template in a submodule of this repository. You can fork this submodule to start your own project to record your hackathon work! [Check it out here](https://github.com/allaway/GoodDoc/tree/477c0ba216fd47d965ffa197b9eaeb0037d53db3).
