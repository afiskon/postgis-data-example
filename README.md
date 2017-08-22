# postgis-data-example

Data example for experimenting with PostGIS.

Usage:

```
sudo -u postgres psql # required for COPY FROM
\c your_database

create table cafes(id serial primary key, name text);
select AddGeometryColumn('cafes', 'point', 4326, 'POINT', 2);
create index cafes_idx on cafes using gist(point);
copy cafes from program 'zcat /tmp/cafes.copy.gz';

create table cities(id serial primary key, name text);
select AddGeometryColumn('cities', 'polygon', 4326, 'POLYGON', 2);
create index cities_idx on cities using gist(polygon);
copy cities from program 'zcat /tmp/cities.copy.gz';
```
