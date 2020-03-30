# Foundry VTT Dockerfiles

These Dockerfiles will create an image for foundry vtt. You need to have the zip file (and maybe the patches file) in the folder where the dockerfile is.

Then create the image by:

```
cd 0.5.2-hotfix
curl -JLO https://....../foundry-0.5.2/zip
docker build . -t foundry-vtt

```
