# Supabase

## Installation
To install, clone the repository to your preferred location on your machine:

`git clone https://github.com/shankar-narayanan-d/supabase.git`

Next
`$ cd supabase/supabase/docker`

`cp .env.example .env`

Change the credentials in the .env file as per the comments given

Then run the files attached below for initial db migrations

1. [00000000000000-initial-schema.sql](https://github.com/supabase/postgres/blob/develop/migrations/db/init-scripts/00000000000000-initial-schema.sql)

2. [00000000000001-auth-schema.sql](https://github.com/supabase/postgres/blob/develop/migrations/db/init-scripts/00000000000001-auth-schema.sql)

3. [00000000000002-storage-schema.sql](https://github.com/supabase/postgres/blob/develop/migrations/db/init-scripts/00000000000002-storage-schema.sql)

4. [00000000000003-post-setup.sql](https://github.com/supabase/postgres/blob/develop/migrations/db/init-scripts/00000000000003-post-setup.sql)

Run the following commands in sql script

`create schema if not exists _realtime;`

`alter schema _realtime owner to $POSTGRES_USER;`

`ALTER USER authenticator WITH PASSWORD $POSTGRES_PASSWORD;`

`ALTER USER pgbouncer WITH PASSWORD $POSTGRES_PASSWORD;`

`ALTER USER supabase_auth_admin WITH PASSWORD $POSTGRES_PASSWORD;`

`ALTER USER supabase_storage_admin WITH PASSWORD $POSTGRES_PASSWORD;`

`ALTER USER supabase_admin WITH PASSWORD $POSTGRES_PASSWORD;`

`ALTER function auth.email owner to supabase_auth_admin`

`ALTER function auth.uid owner to supabase_auth_admin`

`ALTER function auth.role owner to supabase_auth_admin`

Then run
`docker compose up`

While running everstage-spm locally, if you are unable to up the docker server, 
Add `RUN apk add g++ make py3-pip` in top of [file](https://github.com/Everstage/everstage-spm/blob/INTER-2727-supabase/interstage_project/frontend/Dockerfile.dev.frontend) 

