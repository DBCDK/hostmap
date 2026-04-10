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

```
run server:
cargo run server --database-url 'postgres://heze:postgres@localhost:5432/hostmap-dev'

run scraper:
cargo run scraper --host-group-file ./test-assets/minimalTargetList.json --scrape-interval 5
```
