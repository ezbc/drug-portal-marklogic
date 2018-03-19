# MarkLogic Services Docker Stack

# Setup

Pull repository. Download [MarkLogic](https://developer.marklogic.com/products) installation for CentOS and place in the
`ml9` directory.

Download Operational Data Hub quick start [release](https://github.com/marklogic-community/marklogic-data-hub/releases) `gradle/ODH` directory.

Edit the `.env` file to change your environment specific options. 

Change the `ML_INSTALL_PATH` to be the relative path from the ml9 directory to
the MarkLogic installation.

Change the `LOCAL_VOLUME_DIR` to be a directory where the services data files
will live. A volume mount will be created for the operation data hub,
MarkLogic server and CORB.

Start the services by running the following

```
docker-compose up
```

to build the images and start the containers. The MarkLogic Operation Data Hub
and a MarkLogic instance will continue running as services. By default the
MarkLogic server instance will be exposed on your host machines 8000, 8001,
and 8002 ports. The ODH instance will be exposed on your host machine's 8080
port.


# Run Corb

In order to run a batch process with corb, use the `gradle:ml9` image. 

```docker container run -it gradle:ml9 java -cp marklogic-xcc-9.0.4.jar:marklogic-corb-2.4.1.jar
  -DOPTIONS-FILE=myJob.properties
  com.marklogic.developer.corb.ModuleExecutor

```

