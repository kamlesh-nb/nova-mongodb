# nova-mongodb

MongoDB driver for Nova (OP_MSG, BSON, SCRAM). A Nova package — fetch with:

```sh
nova get https://github.com/kamlesh-nb/nova-mongodb
```

```nova
import mongodb;
```

## Structure (SOLID)

Split by responsibility; consumers only touch the seam (`MongoDriver` / `MongoConnection`).

| Module           | Responsibility |
|------------------|----------------|
| `mongodb`        | Seam: `MongoConnection impl Connection` + `MongoDriver impl Driver` + connect/handshake/SCRAM auth. |
| `codec`    | OP_MSG wire codec (`encodeOpMsg`, `decodeOpMsg`, `frameLength`). |
| `commands` | BSON command builders (hello/insert/find/saslStart/saslContinue) + `commandError`. |
