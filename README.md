# nova-mongodb

MongoDB driver for Kyte (OP_MSG, BSON, SCRAM). A Kyte package — fetch with:

```sh
kyte get https://github.com/kamlesh-nb/nova-mongodb
```

```kyte
import mongodb;
```

## Structure (SOLID)

Split by responsibility; consumers only touch the seam (`MongoDriver` / `MongoConnection`).

| Module           | Responsibility |
|------------------|----------------|
| `mongodb`        | Seam: `MongoConnection impl Connection` + `MongoDriver impl Driver` + connect/handshake/SCRAM auth. |
| `codec`    | OP_MSG wire codec (`encodeOpMsg`, `decodeOpMsg`, `frameLength`). |
| `commands` | BSON command builders (hello/insert/find/saslStart/saslContinue) + `commandError`. |
