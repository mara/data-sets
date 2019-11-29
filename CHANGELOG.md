# Changelog


## 2.1.1
- Include button to display data set query
- Add numeric as a valid type in a data set


## 2.1.0 (2019-07-02)
- Changed all `TIMESTAMP` to `TIMESTAMPTZ` in the mara tables. You have to manually run the
  below migration commands as `make migrate-mara-db` won't pick up this change.

**required changes**
You need to manually convert the mara tables to `TIMESTAMPTZ`:

```SQL
-- Change the timezone to whatever your ETL process is running in
ALTER TABLE data_set_query ALTER created_at TYPE timestamptz
  USING created_at AT TIME ZONE 'Europe/Berlin';
ALTER TABLE data_set_query ALTER updated_at TYPE timestamptz
  USING updated_at AT TIME ZONE 'Europe/Berlin';
```


## 2.0.1
Include data_set_id to download_csv endpoint in order to know from which data set is coming from

## 2.0.0

- Change MARA_XXX variables to functions to delay importing of imports
- Move some imports into the functions that use them in order to improve loading speed

**required changes**

- Update `mara-app` to `>=2.0.0`


## 1.0.1 (2019-03-13)

Improve display of JSON columns


## 1.0.0 (2018-09-18)

Initial version
