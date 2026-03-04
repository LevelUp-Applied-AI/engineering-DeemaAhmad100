2026-03-04 14:30:57.001 UTC [1] LOG:  database system is ready to accept connections

# Docker Notes — Day 9

## Docker Version
 docker version :  29.2.1

 ## Hello World Test
 Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
 https://hub.docker.com/

For more examples and ideas, visit:
 https://docs.docker.com/get-started/

 ## Postgres Container

Command used:
```bash
docker run -d \
  --name pg-prework \
  -e POSTGRES_PASSWORD=prework \
  -p 5432:5432 \
  postgres:15-alpine

 ## Output of docker logs pg-prework
  The files belonging to this database system will be owned by user "postgres".
This user must also own the server process.

The database cluster will be initialized with locale "en_US.utf8".
The default database encoding has accordingly been set to "UTF8".
The default text search configuration will be set to "english".

Data page checksums are disabled.

fixing permissions on existing directory /var/lib/postgresql/data ... ok
creating subdirectories ... ok
selecting dynamic shared memory implementation ... posix
selecting default max_connections ... 100
selecting default shared_buffers ... 128MB
selecting default time zone ... UTC
creating configuration files ... ok
running bootstrap script ... ok
sh: locale: not found
2026-03-04 14:30:54.548 UTC [35] WARNING:  no usable system locales were found
performing post-bootstrap initialization ... ok
syncing data to disk ... ok
initdb: warning: enabling "trust" authentication for local connections
initdb: hint: You can change this by editing pg_hba.conf or using the option -A, or --auth-local and --auth-host, the next time you run initdb.


Success. You can now start the database server using:

    pg_ctl -D /var/lib/postgresql/data -l logfile start

waiting for server to start....2026-03-04 14:30:56.589 UTC [41] LOG:  starting PostgreSQL 15.17 on x86_64-pc-linux-musl, compiled by gcc (Alpine 15.2.0) 15.2.0, 64-bit
2026-03-04 14:30:56.595 UTC [41] LOG:  listening on Unix socket "/var/run/postgresql/.s.PGSQL.5432"
2026-03-04 14:30:56.614 UTC [44] LOG:  database system was shut down at 2026-03-04 14:30:55 UTC
2026-03-04 14:30:56.631 UTC [41] LOG:  database system is ready to accept connections
 done
server started

/usr/local/bin/docker-entrypoint.sh: ignoring /docker-entrypoint-initdb.d/*

waiting for server to shut down...2026-03-04 14:30:56.792 UTC [41] LOG:  received fast shutdown request
.2026-03-04 14:30:56.797 UTC [41] LOG:  aborting any active transactions
2026-03-04 14:30:56.803 UTC [41] LOG:  background worker "logical replication launcher" (PID 47) exited with exit code 1
2026-03-04 14:30:56.804 UTC [42] LOG:  shutting down
2026-03-04 14:30:56.808 UTC [42] LOG:  checkpoint starting: shutdown immediate
2026-03-04 14:30:56.831 UTC [42] LOG:  checkpoint complete: wrote 3 buffers (0.0%); 0 WAL file(s) added, 0 removed, 0 recycled; write=0.008 s, sync=0.003 s, total=0.028 s; sync files=2, longest=0.002 s, average=0.002 s; distance=0 kB, estimate=0 kB
2026-03-04 14:30:56.847 UTC [41] LOG:  database system is shut down
 done
server stopped

PostgreSQL init process complete; ready for start up.

2026-03-04 14:30:56.957 UTC [1] LOG:  starting PostgreSQL 15.17 on x86_64-pc-linux-musl, compiled by gcc (Alpine 15.2.0) 15.2.0, 64-bit
2026-03-04 14:30:56.960 UTC [1] LOG:  listening on IPv4 address "0.0.0.0", port 5432
2026-03-04 14:30:56.961 UTC [1] LOG:  listening on IPv6 address "::", port 5432
2026-03-04 14:30:56.970 UTC [1] LOG:  listening on Unix socket "/var/run/postgresql/.s.PGSQL.5432"
2026-03-04 14:30:56.986 UTC [55] LOG:  database system was shut down at 2026-03-04 14:30:56 UTC
2026-03-04 14:30:57.001 UTC [1] LOG:  database system is ready to accept connections
2026-03-04 14:34:55.986 UTC [1] LOG:  received fast shutdown request
2026-03-04 14:34:55.992 UTC [1] LOG:  aborting any active transactions
2026-03-04 14:34:55.999 UTC [1] LOG:  background worker "logical replication launcher" (PID 58) exited with exit code 1
2026-03-04 14:34:55.999 UTC [53] LOG:  shutting down
2026-03-04 14:34:56.004 UTC [53] LOG:  checkpoint starting: shutdown immediate
2026-03-04 14:34:56.055 UTC [53] LOG:  checkpoint complete: wrote 32 buffers (0.2%); 0 WAL file(s) added, 0 removed, 0 recycled; write=0.015 s, sync=0.013 s, total=0.056 s; sync files=10, longest=0.006 s, average=0.002 s; distance=141 kB, estimate=141 kB
2026-03-04 14:34:56.075 UTC [1] LOG:  database system is shut down

PostgreSQL Database directory appears to contain a database; Skipping initialization

2026-03-04 14:35:29.442 UTC [1] LOG:  starting PostgreSQL 15.17 on x86_64-pc-linux-musl, compiled by gcc (Alpine 15.2.0) 15.2.0, 64-bit
2026-03-04 14:35:29.443 UTC [1] LOG:  listening on IPv4 address "0.0.0.0", port 5432
2026-03-04 14:35:29.443 UTC [1] LOG:  listening on IPv6 address "::", port 5432
2026-03-04 14:35:29.453 UTC [1] LOG:  listening on Unix socket "/var/run/postgresql/.s.PGSQL.5432"
2026-03-04 14:35:29.471 UTC [29] LOG:  database system was shut down at 2026-03-04 14:34:56 UTC
2026-03-04 14:35:29.492 UTC [1] LOG:  database system is ready to accept connections

docker stop pg-prework :
pg-prework

docker restart pg-prework]
pg-prework

 docker logs pg-prework
The files belonging to this database system will be owned by user "postgres".
This user must also own the server process.

The database cluster will be initialized with locale "en_US.utf8".
The default database encoding has accordingly been set to "UTF8".
The default text search configuration will be set to "english".

Data page checksums are disabled.

fixing permissions on existing directory /var/lib/postgresql/data ... ok
creating subdirectories ... ok
selecting dynamic shared memory implementation ... posix
selecting default max_connections ... 100
selecting default shared_buffers ... 128MB
selecting default time zone ... UTC
creating configuration files ... ok
running bootstrap script ... ok
sh: locale: not found
2026-03-04 14:30:54.548 UTC [35] WARNING:  no usable system locales were found
performing post-bootstrap initialization ... ok
syncing data to disk ... ok
initdb: warning: enabling "trust" authentication for local connections
initdb: hint: You can change this by editing pg_hba.conf or using the option -A, or --auth-local and --auth-host, the next time you run initdb.


Success. You can now start the database server using:

    pg_ctl -D /var/lib/postgresql/data -l logfile start

waiting for server to start....2026-03-04 14:30:56.589 UTC [41] LOG:  starting PostgreSQL 15.17 on x86_64-pc-linux-musl, compiled by gcc (Alpine 15.2.0) 15.2.0, 64-bit
2026-03-04 14:30:56.595 UTC [41] LOG:  listening on Unix socket "/var/run/postgresql/.s.PGSQL.5432"
2026-03-04 14:30:56.614 UTC [44] LOG:  database system was shut down at 2026-03-04 14:30:55 UTC
2026-03-04 14:30:56.631 UTC [41] LOG:  database system is ready to accept connections
 done
server started

/usr/local/bin/docker-entrypoint.sh: ignoring /docker-entrypoint-initdb.d/*

waiting for server to shut down...2026-03-04 14:30:56.792 UTC [41] LOG:  received fast shutdown request
.2026-03-04 14:30:56.797 UTC [41] LOG:  aborting any active transactions
2026-03-04 14:30:56.803 UTC [41] LOG:  background worker "logical replication launcher" (PID 47) exited with exit code 1
2026-03-04 14:30:56.804 UTC [42] LOG:  shutting down
2026-03-04 14:30:56.808 UTC [42] LOG:  checkpoint starting: shutdown immediate
2026-03-04 14:30:56.831 UTC [42] LOG:  checkpoint complete: wrote 3 buffers (0.0%); 0 WAL file(s) added, 0 removed, 0 recycled; write=0.008 s, sync=0.003 s, total=0.028 s; sync files=2, longest=0.002 s, average=0.002 s; distance=0 kB, estimate=0 kB
2026-03-04 14:30:56.847 UTC [41] LOG:  database system is shut down
 done
server stopped

PostgreSQL init process complete; ready for start up.

2026-03-04 14:30:56.957 UTC [1] LOG:  starting PostgreSQL 15.17 on x86_64-pc-linux-musl, compiled by gcc (Alpine 15.2.0) 15.2.0, 64-bit
2026-03-04 14:30:56.960 UTC [1] LOG:  listening on IPv4 address "0.0.0.0", port 5432
2026-03-04 14:30:56.961 UTC [1] LOG:  listening on IPv6 address "::", port 5432
2026-03-04 14:30:56.970 UTC [1] LOG:  listening on Unix socket "/var/run/postgresql/.s.PGSQL.5432"
2026-03-04 14:30:56.986 UTC [55] LOG:  database system was shut down at 2026-03-04 14:30:56 UTC
2026-03-04 14:30:57.001 UTC [1] LOG:  database system is ready to accept connections
2026-03-04 14:34:55.986 UTC [1] LOG:  received fast shutdown request
2026-03-04 14:34:55.992 UTC [1] LOG:  aborting any active transactions
2026-03-04 14:34:55.999 UTC [1] LOG:  background worker "logical replication launcher" (PID 58) exited with exit code 1
2026-03-04 14:34:55.999 UTC [53] LOG:  shutting down
2026-03-04 14:34:56.004 UTC [53] LOG:  checkpoint starting: shutdown immediate
2026-03-04 14:34:56.055 UTC [53] LOG:  checkpoint complete: wrote 32 buffers (0.2%); 0 WAL file(s) added, 0 removed, 0 recycled; write=0.015 s, sync=0.013 s, total=0.056 s; sync files=10, longest=0.006 s, average=0.002 s; distance=141 kB, estimate=141 kB
2026-03-04 14:34:56.075 UTC [1] LOG:  database system is shut down

PostgreSQL Database directory appears to contain a database; Skipping initialization

2026-03-04 14:35:29.442 UTC [1] LOG:  starting PostgreSQL 15.17 on x86_64-pc-linux-musl, compiled by gcc (Alpine 15.2.0) 15.2.0, 64-bit
2026-03-04 14:35:29.443 UTC [1] LOG:  listening on IPv4 address "0.0.0.0", port 5432
2026-03-04 14:35:29.443 UTC [1] LOG:  listening on IPv6 address "::", port 5432
2026-03-04 14:35:29.453 UTC [1] LOG:  listening on Unix socket "/var/run/postgresql/.s.PGSQL.5432"
2026-03-04 14:35:29.471 UTC [29] LOG:  database system was shut down at 2026-03-04 14:34:56 UTC
2026-03-04 14:35:29.492 UTC [1] LOG:  database system is ready to accept connections

##Isuues i faced 
i have to lanch the Docker app from the account  not from its shortcut on 
the desctop 