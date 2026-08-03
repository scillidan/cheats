```sh
dolt config --global --add user.email "user@example.com"
dolt config --global --add user.name "username"
dolt login
```

```sh
mkdir database_1
cd database_1
dolt init
dolt remote add origin scillidan/database_1
dolt table import --create-table --pk column_1 table_1 table_1.csv
dolt add table_1
dolt commit -m "add table_1"
# dolt status
# dolt pull origin main
dolt push origin main
```

```sh
# Export to csv
dolt sql -r csv -q "SELECT * FROM `blog` > file.csv
```