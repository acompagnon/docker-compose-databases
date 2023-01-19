# MongoDB <img src="../documentation/images/mongodb-logo.jpg" alt="mongodb logo" width="80"/>

MongoDB is a source-available cross-platform [document-oriented database](../documentation/DOD.md) program.

Classified as a [NoSQL](../documentation/NOSQL.md) database program, MongoDB uses JSON-like documents with optional schemas.

## Docker images

- [mongo](https://hub.docker.com/_/mysql):6.0.3
- [mongo-express](https://hub.docker.com/_/mongo-express):1.0.0-alpha.4 (web-based admin interface)

## Ports

| Service       | Port |
| :------------ | :--- |
| mongo         | 27017|
| mongoexpress  | 8081 |

## Database initialization

If you want the your initialization files to be executed, mount their directory as a volume in the `volumes` section of the [docker-compose.yml](./docker-compose.yml)

```yaml
        volumes:
          - /path/to/folder:/docker-entrypoint-initdb.d
```

Extract from MongoDB docker hub documentation :

```txt
When a container is started for the first time it will execute files with extensions .sh and .js
that are found in /docker-entrypoint-initdb.d. Files will be executed in alphabetical order. .js
files will be executed by mongosh (mongo on versions below 6) using the database specified by
the MONGO_INITDB_DATABASE variable, if it is present, or test otherwise.
You may also switch databases within the .js script.
```

## Usage

Place yourself in this folder, configure your environment variables in [docker-compose.yml](./docker-compose.yml) and run

```bash
docker-compose up -d
```

Access Mongo Express at http://0.0.0.0:8081/

## MongoDB environment variables

| Variable                      | Description   | Type      |
| :---------------------------- | :------------ | :-------- |
| `MONGO_INITDB_ROOT_USERNAME`  | Root username | mandatory |
| `MONGO_INITDB_ROOT_PASSWORD`  | Root password | mandatory |
| `MONGO_INITDB_DATABASE`       | Database name | optional  |

## Mongo Express environment variables

| Variable                      | Default         | Description |
| :---------------------------- | :-------------- | :---------- |
| `ME_CONFIG_BASICAUTH_USERNAME`    | ''              | mongo-express web username |
| `ME_CONFIG_BASICAUTH_PASSWORD`    | ''              | mongo-express web password |
| `ME_CONFIG_MONGODB_ENABLE_ADMIN`  | 'true'          | Enable admin access to all databases. Send strings: `"true"` or `"false"` |
| `ME_CONFIG_MONGODB_ADMINUSERNAME` | ''              | MongoDB admin username |
| `ME_CONFIG_MONGODB_ADMINPASSWORD` | ''              | MongoDB admin password |
| `ME_CONFIG_MONGODB_PORT`          | 27017           | MongoDB port |
| `ME_CONFIG_MONGODB_SERVER`        | 'mongo'         | MongoDB container name. Use comma delimited list of host names for replica sets. |
| `ME_CONFIG_OPTIONS_EDITORTHEME`   | 'default'       | mongo-express editor color theme, [more here](http://codemirror.net/demo/theme.html) |
| `ME_CONFIG_REQUEST_SIZE`          | '100kb'         | Maximum payload size. CRUD operations above this size will fail in [body-parser](https://www.npmjs.com/package/body-parser). |
| `ME_CONFIG_SITE_BASEURL`          | '/'             | Set the baseUrl to ease mounting at a subdirectory. Remember to include a leading and trailing slash. |
| `ME_CONFIG_SITE_COOKIESECRET`     | 'cookiesecret'  | String used by [cookie-parser middleware](https://www.npmjs.com/package/cookie-parser) to sign cookies. |
| `ME_CONFIG_SITE_SESSIONSECRET`    | 'sessionsecret' | String used to sign the session ID cookie by [express-session middleware](https://www.npmjs.com/package/express-session). |
| `ME_CONFIG_SITE_SSL_ENABLED`      | 'false'         | Enable SSL. |
| `ME_CONFIG_SITE_SSL_CRT_PATH`     | ''              | SSL certificate file. |
| `ME_CONFIG_SITE_SSL_KEY_PATH`     | ''              | SSL key file. |

## Tips

### Persist data

If you want to persist data on filesystem, uncomment the `volumes` section line 9 and 10

### Customize configuration

You can pass any option in command object in [docker-compose.yml](./docker-compose.yml) as in line 8

Execute this command to see available options :

```bash
docker run -it --rm mongo --help
```

### Complex configuration

if you want to use a [configuration file](https://www.mongodb.com/docs/manual/reference/configuration-options/), mount the file as a volume in the `volumes` section of the [docker-compose.yml](./docker-compose.yml)
