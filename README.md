# Tosca-2-Data-Science

## Running Your Jupyter Container

### Initial Setup

To create and run your Jupyter container for the first time, use the following command:

```
docker run -it --name tosca-2-data -p 8888:8888 -v ./src:/home/jovyan/src -v /home/akif/:/home/jovyan/local  pangeo/pangeo-notebook:latest jupyter lab --ip 0.0.0.0 
```

- `--name tosca-2-data`: Names your container "tosca-2-data".
- `-p 8888:8888`: Maps port 8888 on your local machine to port 8888 on the container.
- `-v ./data:/home/jovyan/data`: Mounts the local `./data` directory to `/home/jovyan/data` in the container.
- `pangeo/pangeo-notebook:latest`: Uses the latest Pangeo notebook image.
- `jupyter lab --ip 0.0.0.0 -d`: Starts Jupyter Lab and makes it accessible from any IP address.

### Accessing Your Container

After the initial setup, your container will be set up with Jupyter Lab and any changes you make to libraries or files will be saved within the "tosca-2-data" container. This container functions as your dedicated environment for geospatial data processing.

To access your container and view the Jupyter Lab link, use the following commands:

```bash
docker start tosca-2-data
docker logs tosca-2-data
```

The `docker logs` command will output a URL you can use to access Jupyter Lab in your web browser.

### Sharing and Saving Your Environment

If you want to save your current environment or share it with colleagues, you can create a Docker image from your container. This allows you to distribute the environment or create additional containers from the saved image.

To create an image from your container, use the following command:

```bash
docker commit tosca-2-data your-image-name
```

Replace `your-image-name` with a name for your new image. You can then share this image or use it to create new containers with the same environment.

---