# ECommerce

A Microservice-based ECommerce.

## Build Server

Uses Azure DevOps pipeline.

## Docker images

Find the images on my docker repo [here](https://hub.docker.com/u/nkhalili). Use them on Windows containers by running:

```powershell
docker pull nkhalili/ecommerceapisearch:latest
```

## Azure Service Fabric

To publish your application on Azure Service Fabric:

1. Create your Service Fabric Cluster on Azure

    1.1. Create certificate for your cluster, download and install locally (e.g *ecomnkkv-ecomnkcert-20200428.pfx*)

    1.2. Copy your Cluster Endpoint address (e.g. *tcp://ecomnk.westus2.cloudapp.azure.com:19000*)

    1.3 Copy its Thumbprint(s) as well

2. Run this powershell command to exctract your Thumbprint locally (*Client Certificate*)

    ```powershell
     [System.Convert]::ToBase64String([System.IO.File]::ReadAllBytes("C:\ecomnkkv-ecomnkcert-20200428.pfx")) > cert.txt
    ```

3. Create your release pipline from *Azure Service Fabric Compose deployment* template on Azure DevOps

    3.1 Enter steps 1.1,  1.2, and 2 details into service connection dialog

    3.2 Change the docker compose file to your asf version

    3.3 Enter the **Application Name** as same as your application name in your docker-compose-asf.yml

    3.4 if you are not using private container registry set **Registry Credentials Source** to None.

4. Create a release to deploy into your Service Fabric Cluster
