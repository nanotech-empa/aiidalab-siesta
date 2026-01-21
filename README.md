# aiidalab-siesta
## Dev environment for siesta apps with smallstep pre-installed for CINECA MFA
Example installation using [aiidalab-launch](https://github.com/aiidalab/aiidalab-launch) and compiling the Dockerfile. 

### Make sure Dockerdesktop is running

Suppose you work in the opt directory of your home:
```
cd opt
git clone
```

after cloning the repository, enter the directory `aiidalab-siesta` in `opt`
```
cd aiidalab-siesta
```
Creation of the aiidalab-launch profile:
```
aiidalab-launch profile add siesta2026
```
the command will ask you if you want to edit the profile. edit it, you will see:
```
port = 8913
default_apps = []
system_user = "jovyan"
image = "docker.io/aiidalab/full-stack:latest"
home_mount = "aiidalab_siesta2026_home"
extra_mounts = []
```
The port number may be differnt, keep the one that you will receive. Instead, modify the image name so that the profile will look like:
```
port = 8913
default_apps = []
system_user = "jovyan"
image = "siesta2026"
home_mount = "aiidalab_siesta2026_home"
extra_mounts = []
```
where `siesta2026` is the tag you will use compiling the `Dockerfile`
Now compile the Dockerfile:
```
docker build -t siesta2026 .
```
If you need to compile it again and want to avoid cache:
```
docker build --no-cache -t siesta2026 .
```
If the compilation is sucessfull you can start AiiDAlab:
```
aiidalab-launch start --profile siesta2026
```
It could fail at the first start, just enter teh command again in case. To start the webpage accept teh request
To stop teh server type:
```
aiidalab-launch stop --profile siesta2026
```
