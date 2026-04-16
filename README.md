# Initial setup

```bash
nix develop
pg_initial_setup
cargo sqlx migrate run
cargo run -- test-assets/minimalTargetList.json
```

# Development
```bash
nix develop
pg_start
```
**The following environment variables a set from flake.nix**\

PG=$PWD/.dev_postgres\
PGDATA=$PG/data\
PGPORT=5432\
PGHOST=localhost\
PGUSER=$USER\
PGPASSWORD=postgres\
PGDATABASE=hostmap-dev\
DATABASE_URL=postgres://$PGUSER:$PGPASSWORD@$PGHOST:$PGPORT/$PGDATABASE

**run server:**\

For the server to run in development we need a git repository and an API key. The API key is obtained from the GitLab UI.\
If the API key is saved in the file `./api-key.txt` it will be ignored by git.

```
cargo run server --database-url $DATABASE_URL --repo-url https://gitlab.dbc.dk/me/my-deployment --grouping-key host_group_name --api-key-file ./api-key.txt --columns "loc" 
```

run scraper:
```
cargo run scraper --host-group-file ./test-assets/minimalTargetList.json --scrape-interval 5
```
