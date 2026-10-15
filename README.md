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

## Software attribution and scientific acknowledgements

Please credit [aiidalab-siesta](https://github.com/nanotech-empa/aiidalab-siesta) and its
[contributors](https://github.com/nanotech-empa/aiidalab-siesta/graphs/contributors),
and identify the release or immutable commit used. Existing author,
contributor and funding acknowledgements remain authoritative.

This revision has no top-level licence file. Preserve existing source
notices and confirm applicable reuse terms with the maintainers; this
citation guidance does not supply a licence.

For research carried out using this environment or the resulting workflows,
acknowledge [AiiDA](https://github.com/nanotech-empa/.github/blob/main/CITATION_GUIDANCE.md#aiida) and [AiiDAlab](https://github.com/nanotech-empa/.github/blob/main/CITATION_GUIDANCE.md#aiidalab)
when each platform was actually used, following their respective citation
guidance. Cite the scientific software and methods actually used as well.

Credit this development environment separately from AiiDAlab, aiidalab-launch, SIESTA and smallstep, which retain their own authorship and licence notices.

The [shared credit guide](https://github.com/nanotech-empa/.github/blob/main/CITATION_GUIDANCE.md) keeps software attribution, licence
compliance and scientific citation requests separate. Scientific citation
requests are not additional MIT licence conditions.
