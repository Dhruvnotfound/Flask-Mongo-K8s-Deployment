
# Build and Push a Docker image to a container registry


### Prerequisites 
- Docker installed on your machine.
- Access to a container registry (e.g., Docker Hub, Google Container Registry, Amazon ECR, Azure Container Registry).
- A Dockerfile in your project directory.

### Building the Docker Image

1. **Navigate to your project directory** where the `Dockerfile` is located:

   ```bash
   cd /path/to/your/project

2. **Build the Docker image** using the `docker build` command. Replace your-image-name with a name for your image:

    ```bash
    docker build -t your-image-name:tag .
- `your-image-name`: Name of your Docker image.
- `tag`: (Optional) Tag for the image (e.g., latest, v1.0).

### Pushing the Docker Image

1. **Log In to the Container Registry** of your choice 
**For Docker Hub:**

        docker login
You will be prompted to enter your Docker Hub username and password.

**For container registries other than Docker Hub**, you'll need to follow specific authentication methods provided by their platforms. Here are some resources for reference:

- Google Container Registry (GCR): https://cloud.google.com/sdk/gcloud/reference/auth/configure-docker
- Amazon ECR: https://docs.aws.amazon.com/cli/latest/reference/ecr/get-login-password.html   
- Azure Container Registry (ACR): https://learn.microsoft.com/en-us/azure/container-registry/container-registry-authentication 

2. **Tag the Docker Image** to match the format required by the container registry:
    ```bash 
    docker tag your-image-name:tag registry-url/your-repository/your-image-name:tag

- `registry-url`: The URL of your container registry (e.g., docker.io for Docker Hub).
- `your-repository`: Your repository name (may be your username for Docker Hub).
- Example for Docker Hub: `docker.io/your-username/your-image-name:tag`
- Example for ECR: `your-account-id.dkr.ecr.your-region.amazonaws.com/your-repository/your-image-name:tag`

3. **Push the image to the container registry**
    ```bash
    docker push registry-url/your-repository/your-image-name:tag

Example for Docker Hub: `docker push docker.io/your-username/your-image-name:tag`

4. **Verify the Image in the Container Registry**
Login to your container registry (e.g., Docker Hub, GCR, ECR, ACR) and check if the image has been successfully uploaded.

---

Using this You have successfully Build and Pushed your Docker image to a container registry