# helpers

### Execute PowerShell scripts localy: 
    Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope LocalMachine
    
### IIS Commands:
    iisreset
    
### Consul commands
    consul operator raft list-peers
    consul members
    consul monitor
    
### Docker
    docker exec -it <container id> /bin/bash
    docker exec --privileged -it <container id> /bin/bash
    docker inspect <container id>
    docker logs -t <container id>
    docker logs --details --follow <container id> 
    docker stats
    cat /var/lib/docker/containers/<container id>/<container id>-json.log
    docker system prune -a 
    sudo docker top <conteiner-id>
    
    docker tag "consul:1.12.4" "nexus.local:8080/nexus/repository/eng-docker/local-consul:1.12.4"
    docker login nexus.local:8080 -u "docker" -p "fake-password"
    docker push "nexus.local:8080/nexus/repository/eng-docker/local-consul:1.12.4"
    docker logout nexus.local:8080
    
    docker-compose -f <docker-file-path> up buid
    docker-compose logs -f kafka

### LSOF
    sudo lsof -p <pid> -i
    sudo lsof  -p "$pid" | grep -e '(ESTABLISHED)$' -e '->INO=.*
    sudo lsof -p <pid> | wc - l
    sudo docker ps | grep ecs-listqueryagent-prod- | awk '{print $1}' | ((xargs -L1 sudo docker top) | awk '{ print $2 }' | grep -P '\d+') | xargs -L1 -I {} sh -c 'ps -f {}; sudo lsof -p {} | wc -l'

### MySql
    docker rm -f mysql
    docker pull mysql/mysql-server:latest
    docker run --name mysql -e MYSQL_ROOT_PASSWORD=docker -p 3306:3306 -d mysql:5.7
  
### Postgres
    docker run --name some-postgres -e POSTGRES_USER=postgres_user -e POSTGRES_PASSWORD=postgres_password -p 5432:5432 -d postgres
  
### Redis
    docker run --name docker-redis -p 6379:6379 -d redis
  
### Rabbit
    docker run -d --hostname my-rabbit --name rabbit -e RABBITMQ_DEFAULT_USER=rmquser -e RABBITMQ_DEFAULT_PASS=rmquser -p 15672:15672 -p 5672:5672 rabbitmq:3.8-management
    docker run -d --hostname my-rabbit --name some-rabbit -p 8080:15672 rabbitmq:3-management
  
### MSSQL
    docker run -e 'ACCEPT_EULA=Y' -e 'SA_PASSWORD=password' -e 'MSSQL_PID=Express' -p 1433:1433 -d mcr.microsoft.com/mssql/server:2017-latest-ubuntu
    docker run -e 'ACCEPT_EULA=Y' -e 'SA_PASSWORD=Pa$$word!23' -p 1433:1433 -n sqlserver -d mcr.microsoft.com/mssql/server:2017-latest
  
### DynamoDb
    docker run --name dynamo-local -p 8000:8000 -d amazon/dynamodb-local
    aws dynamodb list-tables --endpoint-url http://localhost:8000

    aws dynamodb --endpoint-url http://localhost:8000 create-table \
    --table-name devel_TableName \
    --attribute-definitions \
        AttributeName=Id,AttributeType=S \
    --key-schema \
        AttributeName=Id,KeyType=HASH \
    --provisioned-throughput \
        ReadCapacityUnits=10,WriteCapacityUnits=10
        
        
### Vault
    https://learn.hashicorp.com/tutorials/vault/getting-started-install
    export VAULT_ADDR=https://vault.devops.site.net/
    vault login -method=ldap username=realusername
    vault read disco/staging/path
  
### AWS EMR Srapk
    ssh -i "aws-spark.ppk" hadoop@127.0.0.1
    sudo vim /etc/spark/conf/spark-defaults.conf

