# HW24 — Docker image and load balancing in Kubernetes

## 1. Dockerfile
`app/Dockerfile` — image based on `python:3.12-alpine`, script `app/app.py`, port 8082.
Built and pushed as a private image: `yuriysherbakov/hw24-random:1.0`.

## 2. Image in Docker Hub
`screenshots/2. image docker hub.png`

## 3. Cluster
`k8s/kind-config.yaml` — kind cluster `hw24`, host port 30080 mapped to the node.

## 4. Manifests
`k8s/random-app.yaml` — Deployment with 3 replicas and a NodePort Service on 30080.
The image is loaded into kind with `kind load`, because the Hub repository is private.

## 5. Check
`screenshots/2. image docker hub` — image docker hub.
`screenshots/5. pods.png` — three running pods.
`screenshots/5.1. diff pods.png` — several requests to `http://127.0.0.1:30080/` return different `name-...` values from different pods.