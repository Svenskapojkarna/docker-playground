## OpenJDK8u181
This image was used to find solution to a problem, where a Docker image was having an updated version of OpenJDK 8 and it had to be downgraded.<br/>
Idea is that the image first install new version of OpenJDK 8 and then it is downgraded to OpenJDK 8_181.<br/>
The image can be build and run with basic Docker commands.
```sh
# Build the image
docker build -t <name> .

# Run the image
docker run -d <name>
```
