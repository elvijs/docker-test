# Build image

`docker build -f Dockerfile -t elvijs/getstartedlab .`

# Run image in a container

`docker run elvijs/getstartedlab`

# Connect to services exposed over host's network

Suppose you're running a local MongoDB service and want to access it from 
a Docker container.
[Use the "host" network option](https://stackoverflow.com/questions/24319662/from-inside-of-a-docker-container-how-do-i-connect-to-the-localhost-of-the-mach):
`docker run -e PYTHONPATH=.:src:lib/crowdsurfer-common/src -e DEBUG=1 --network="host" tab/crawler/batch -t asd`