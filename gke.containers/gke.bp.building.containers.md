# Best practices for building containers


- Package a single app per container
- Properly handle PID 1, signal handling, and zombie processes
    - In the context of containers, PIDs and Linux signals create two problems to consider.
       - Problem 1: How the Linux kernel handles signals
       - Problem 2: How classic init systems handle orphaned processes

       - Solution 1: Run as PID 1 and register signal handlers
       - Solution 2: Enable process namespace sharing in Kubernetes
       - Solution 3: Use a specialized init system

- Optimize for the Docker build cache
- Remove unnecessary tools
        - File system content
        - File system security
- Build the smallest image possible
        - Use the smallest base image possible
        - Reduce the amount of clutter in your image
        - Try to create images with common layers
- Use vulnerability scanning in Container Registry
        - Store your images in Container Registry and enable vulnerability scanning.
        - Configure a job that regularly fetches new vulnerabilities from Container Registry and 
          triggers a rebuild of the images if needed.
        - When the new images are built, have your continuous deployment system deploy them to a staging environment.
        - Manually check the staging environment for problems.
        - If no problems are found, manually trigger the deployment to production.
- Properly tag your images
        - Tagging using semantic versioning
        - Tagging using the Git commit hash
- Carefully consider whether to use a public image
        - examples of constraints that might render the use of public images impossible:
               - You want to control exactly what is inside your images.
               - You don't want to depend on an external repository.
               - You want to strictly control vulnerabilities in your production environment.
               - You want the same base operating system in every image.
        - To have any chance of managing such a system at scale, think about using the following:
               - An automated way to build images, in a reliable way, even for images that are built rarely. 
               - Build triggers in   Cloud Build are a good way to achieve that.
               - A standardized base image. Google provides some base images that you can use.
               - An automated way to propagate updates to the base image to "child" images.
               - A way to address vulnerabilities in your images. 
                    - Use vulnerability analysis in Container Registry.
               - A way to enforce your internal standards on images created by the different teams in your organization.

         - Several tools are available to help you enforce policies on the images that you build and deploy:
                  -  container-diff can analyze the content of images and even compare two images between them.
                   - container-structure-test can test whether the content of an image complies with a set of rules that you define.
                  -  Grafeas is an artifact metadata API, where you store metadata about your images to later check whether 
                     those   images comply with your policies.
                  -  Kubernetes has admission controllers that you can use to check a number of prerequisites before deploying a    workload in Kubernetes.
                  -  Kubernetes also has pod security policies, that you can use to enforce the use of security options in the   cluster.