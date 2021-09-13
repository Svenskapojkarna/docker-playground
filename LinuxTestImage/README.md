## LinuxTestImage
This image is for running tests in .NET Standard 2.0.<br/>
You need to have `C:\repos` folder, since it is used as a volume in the container.<br/>
The volume is used to transfer C# source code to the container, so it is possible run tests for those source codes.
```sh
# Build the image
docker-compose build

# Run the image
docker-compose up -d
```
