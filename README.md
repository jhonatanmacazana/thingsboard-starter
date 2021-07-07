# thingsboard-starter

Starter files to set up a thingsboard instance with docker and Postgres. Based on the [official page][1].

## Run

```bash
# start the containers with an in-memory queue
docker compose up -d

# OR start the containers with a RabbitMQ queue
docker compose -f docker-comopse.rabbitmq.yml up -d
```

If the previous command throws an error, make sure you have the last `docker` version. Otherwise, install `docker-compose` and run

```bash
docker-compose up -d

# OR

docker-compose -f docker-comopse.rabbitmq.yml up -d
```

## Access

After executing this command you can open `http://{your-host-ip}:8080` in your browser (for ex. `http://localhost:8080`). You should see ThingsBoard login page. Use the following default credentials:

```
System Administrator: sysadmin@thingsboard.org / sysadmin
Tenant Administrator: tenant@thingsboard.org / tenant
Customer User: customer@thingsboard.org / customer
```

You can always change passwords for each account in account profile page.

## Extras

- You can see the [architecture][2] available from the official page
- There many [guides][3] available. You can start with the [`hello world`][4]
- Scripts to test devices:

```bash
# Get your access token for an specific device from the devices page. (i.e. `http://localhost:8080/devices`)
ACCESS_TOKEN=SMiRhvI6OCbO6gpBwbs8
# Set your hostname
HOST_NAME=http://localhost:8080
# Send command
curl -v -X POST -d "{\"temperature\": 25}" $HOST_NAME/api/v1/$ACCESS_TOKEN/telemetry --header "Content-Type:application/json"
```

<!-- Links -->

[1]: https://thingsboard.io/docs/user-guide/install/docker/?ubuntuThingsboardQueue=inmemory
[2]: https://thingsboard.io/docs/reference/
[3]: https://thingsboard.io/docs/getting-started-guides
[4]: https://thingsboard.io/docs/getting-started-guides/helloworld/
