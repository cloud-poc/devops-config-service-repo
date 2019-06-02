# Git Repository of Config Service

__Q&A__  
 - 1. Postgres startup issue in docker-compose environment
 
> nginx: [error] init_by_lua error: /usr/local/share/lua/5.1/kong/init.lua:333: [PostgreSQL error] failed to retrieve server_version_num: connection refused
kong_1             | stack traceback:
kong_1             |    [C]: in function 'assert'
kong_1             |    /usr/local/share/lua/5.1/kong/init.lua:333: in function 'init'
kong_1             |    init_by_lua:3: in main chunk

  [possible root cause] Postgres does not have sufficient access right to the volumes declared in docker-compose.yml file  
  [workaround]: 
  Before mounting the containers, you must create the volume manually:
  
    docker volume create --name=pgdata

 