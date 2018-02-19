# Create the VMs
# Create VMs if needed
```
docker-machine create --driver virtualbox myvm1
docker-machine create --driver virtualbox myvm2
```

# Get IPs and regenerate certs if needed

`docker-machine ls` to get the IPs

`docker-machine regenerate-certs myvm1` if there's a cert issue

# Appoint the swarm manager
`docker-machine ssh myvm1` to get into the first machine, then whilst on the machine:
`docker swarm init --advertise-addr <myvm1 ip on 2377>` and copy the instructions.

# Add worker
SSH into myvm2 and paste the instructions from the previous section.

# Deploy app on the swarm cluster

## Set up shell to run commands directly on the swarm manager manager
`eval $(docker-machine env myvm1)`

`docker-machine ls` to check that `myvm1` is the active machine.

## Deploy the app

`docker stack deploy -c docker-compose.yml getstartedlab`

Check `docker stack ps getstartedlab`

# Remove app

`docker stack rm getstartedlab`

`docker-machine stop $(docker-machine ls -q)`