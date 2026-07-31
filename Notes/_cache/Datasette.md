## Data processing[^2]

```sh
pipx install sqlite-utils
sqlite-utils insert database.db table table.csv --csv
sqlite-utils drop-table database.db table
sqlite-utils enable-fts database.db table column_1 column_2
# sqlite-utils insert-files resource.db latex media/*.jpg
```

## Selfhost[^1]

```sh
mkdir <dir>
cd <dir>
uv venv
.venv\Scripts\activate
uv pip install datasette
uv pip install datasette-sitemap datasette-block-robots datasette-backup datasette-search-all datasette-external-links-new-tabs datasette-copyable datasette-publish-vercel
# datasette install datasette-render-images datasette-multiline-links datasette-render-markdown datasette-media
# datasette install git+https://github.com/next-LI/datasette-csv-importer.git
# uv pip install datasette-parquet 
datasette serve database.db
datasette serve database_1.db database_2.db -m metadata.yml
```

## Deploy to Vercel[^3]

Create `.github/workflows/vercel.yml`

```yaml
name: Deploy to Vercel
on:
  push:
    branches: [ "main" ]
  pull_request:
    branches: [ "main" ]
  workflow_dispatch:

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v4
      - name: Set up Node.js
        uses: actions/setup-node@v4
        with:
          node-version: '18.x'
      - name: Install Vercel CLI
        run: npm i -g vercel
      - name: Set up Python
        uses: actions/setup-python@v4
        with:
          python-version: '3.9'
      - name: Install dependencies
        run: pip install datasette datasette-sitemap datasette-block-robots datasette-backup datasette-search-all datasette-ripgrep datasette-render-images datasette-media datasette-render-markdown datasette-multiline-links datasette-external-links-new-tabs datasette-copyable datasette-publish-vercel
      - name: Deploy Datasette using Vercel
        env:
          VERCEL_TOKEN: ${{ secrets.VERCEL_TOKEN }}
        run: |-
          datasette publish vercel database_1.db database_2.db \
            --metadata metadata.yml \
            --token $VERCEL_TOKEN \
            --project database
```

Vercel → Project `database` → Settings → Build and Deployment → Node.js Version → 18.x.

[^1]: [Metadata](https://docs.datasette.io/en/stable/metadata.html)
[^2]: [sqlite-utils](https://github.com/simonw/sqlite-utils)
[^3]: [datasette-publish-vercel](https://github.com/simonw/datasette-publish-vercel)