# docker-compose image for Splunk + fluent-bit

This docker-compose image uses,

 - [The public, official splunk enterprise image](https://hub.docker.com/r/splunk/splunk/)
 - [The public, official splunk enterprise universalforwarder image](https://hub.docker.com/r/splunk/universalforwarder/)
 - [A public, unofficial fluentbit image](https://hub.docker.com/r/sddmelb/fluent-bit/)

Bring up the containers by running,

    docker-compose build
    docker-compose up

To bring down and clean up the containers run `docker-compose down`

## Composition

```
,---------------.                   
|Logs and events|                   
`---------------'                   
      |                           
,----------.    ,---.     ,---------.
|fluent-bit|--->|HEC|---->|Splunk UF|
`----------'    `---'     `---------'
                             |    
       ,----------.   ,---------.
       |Splunk IDX|<--|Splunk HF|
       `----------'   `---------'
             ^                   
             |                   
       ,----------.              
       |Splunk SHC|              
       `----------'   
```

## UI   

| Function       | URL                                              | Username  | Password |
|----------------|--------------------------------------------------|-----------|----------|
| Splunk UI      | [http://localhost:8000/](http://localhost:8000/) | admin     | admin    |
| Splunk UF UI   | [http://localhost:8001/](http://localhost:8001/) | admin     | admin    |

## Shell

For a shell on the containers, run the commands below.

    ./script/shell-splunk.sh
    ./script/shell-splunkforwarder.sh
    ./script/shell-fluentbit.sh

