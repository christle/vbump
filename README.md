# vbump - Version Bumper

This is a little API service in `golang` to handle project-versions in "semver". Easily bump major, minor and patch versions for different projects. Every bump increments the specific version part with 1. You can use it in CI/CD pipelines to handle your release version. 

## dockerhub
[https://hub.docker.com/r/christle/vbump](https://hub.docker.com/r/christle/vbump)

## API
`POST /major/myproject` - bump major version for `myproject` and returns new version  
`POST /minor/myproject` - bump minor version for `myproject` and returns new version  
`POST /patch/myproject` - bump patch version for `myproject` and returns new version  
`POST /version/myproject/1.0` - set version to `1.0` for project `myproject`  
`GET /version/myproject` - get version for project `myproject`  

## use it with docker
```
mkdir data # data dir for storing project files.
docker run -p 8080:8080 -v $PWD/data:/data -d christle/vbump:latest
```

## use it with kubernetes
```
helm upgrade --install helm/vbump
```

## usage
`curl -X POST http://localhost:8080/major/myproject` returns `1`  
`curl -X POST http://localhost:8080/minor/myproject` returns `1.1`  
`curl -X POST http://localhost:8080/minor/myproject` returns `1.2`  
`curl -X POST http://localhost:8080/patch/myproject` returns `1.2.1`  
`curl -X POST http://localhost:8080/version/myproject/4.0` returns `4.0`  
`curl -X GET http://localhost:8080/version/myproject` returns `4.0`  

