# 01_getting_started

## Introduction

In this tutorial, I will show you how to create a Docker image and use it to deploy a simple app.

## Directory Structure

```console
myapp/
    Dockerfile
    myapp
src/
    CMakeList.txt
    main.cpp
```

`myapp/` contains the Dockerfile used to create an image and the app we want to distribute in the image. `src/` contains the app's CMakelist.txt and its source code.

## App

The app were building and deploying is a very simple application. Here's its source code:

```C++
#include <iostream>

int main(int argc, char* argv[])
{
    std::cout << "Hello World!" << std::endl;

    return 0;
}
```

When run, it will display the following output:

```console
Hello World!
```

## Build and Run Instructions

To build the app, type the following into the terminal:

```console
cd src
mkdir build
cd build
cmake ..
cmake --build .
```
This will:
- Change the current directory to `src`,
- Make a subdirectory `build`,
- Change the current directory to `build`,
- Generate the CMake cache,
- Build the application.

To run the app, type the following into the terminal:

```console
./myapp
```

Afterwards, something similar to the following will be displayed:

```console
Hello World!
```

## Build Image and Run Container

To build the docker image, type the following into the terminal:

```console
cd myapp
docker build --tag myapp .
```

Afterwards, something similar to the following will be displayed:

```console
 ...
 => exporting to image                                                                          0.0s
 => => exporting layers                                                                         0.0s
 => => writing image sha256:3c4cfa5cc6c38d8853357b38149ff2225ce5df77ef5bc0bb0a82683a0773ed2d    0.0s 
 => => naming to docker.io/library/myapp                                                        0.0s 

What's Next?
  View a summary of image vulnerabilities and recommendations → docker scout quickview
```

To run the docker container, type the following into the terminal:

```console
docker run myapp
```

Afterwards, something similar to the following will be displayed:

```console
Hello World!
```

## Conclusion

In this tutorial, I have shown you how to create a Docker image and use it to deploy a simple app.

## Credit

Dr Frazer K. Noble
BE (Hons), ME (Hons), PhD
drfknoble