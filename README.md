
This repo is only here to demonstrate a docker-compose v2.3.3 bug related to `docker-compose build` which only seems to happen on linux.

On linux:
`docker-compose -f docker-compose-bad.yaml build` will fail with
> * Error response from daemon: dockerfile parse error line 1: unknown instruction: .DOCKERIGNORE


When the Dockerfile is in the same directory as the context, it succeeds:
`docker-compose -f docker-compose-good.yaml build`:
```
Sending build context to Docker daemon     141B
Step 1/2 : FROM busybox
 ---> a8440bba1bc0
Step 2/2 : RUN ls
 ---> Using cache
 ---> 43621b7290c1
Successfully built 43621b7290c1
Successfully tagged busybox-built:latest
```

