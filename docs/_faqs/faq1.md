---
title: "How do I kill a Docker image on my laptop or devbox?"
tags: [docker]
---

Use the command:
```
docker -ps
```
This command lists the containers running. Look for the container running on the desired port, then copy the container ID and enter this command:
```
docker kill <container_id>
```
