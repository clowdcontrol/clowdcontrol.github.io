# clowdcontrol.github.io

To recreate the clowdcontrol demo:

1. Download some ABIDE freesurfer data using the `abide-fs` docker image:

```bash
mkdir clowdcontrol_demo
cd clowdcontrol_demo
docker run --rm -ti -v $PWD:/data clowdcontrol/abide-fs:v0.1
```

2. Prepare the data for mindcontrol by running the `freesurfer_prep` docker image:

```bash
docker run -ti --rm -v $PWD/data:/data clowdcontrol/freesurfer_prep:v2.0
```

3. Run Mindcontrol with the `mindcontrol` docker image:

```bash
docker run -it --rm -v ${PWD}/.mindcontrol/:/home/mindcontrol/mindcontrol/.meteor/local -v $PWD/data:/bids -p 3000:3000 -p 8080:8080 clowdcontrol/mindcontrol:v0.3
```

Open Google Chrome to [http://localhost:3000](http://localhost:3000) to view the demo data
