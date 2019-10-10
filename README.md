docker-compose up

open http://localhost:8083/

## Update plugins.txt

http://local.docker:8083/script

Jenkins.instance.pluginManager.plugins.each{
  plugin -> 
    println ("${plugin.getShortName()}:${plugin.getVersion()}")
}

