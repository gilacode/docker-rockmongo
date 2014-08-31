Overview
=======
RockMongo Docker modified from "webts/rockmongo" implementation

Rockmongo used for this container is pulled from  a forked version of Rockmongo with some modification on the "config.php" that will check for values from environmen variables before setting the default values. 

Original Rockmongo repository: https://github.com/iwind/rockmongo

Forked version of Rockmongo with modified "config.php": https://git@github.com:gilacode/rockmongo.git

Limitation
==========
Currently this implementation only support overriding 1 database configuration. Default implementation Rockmongo allows for multiple Mongo database connection.

Next planning to add the capability for Rockmongo to read from environment variables in JSON format so we can put multiple database configurations and request for pull. Busy at the moment to do that. :)

Build
=====
docker build -t gilacode/rockmongo

Run
===
To run this docker container. Run:

1. docker pull
2. docker run -d -p <port to exposed>:80 -link <your mongo db container name>:db -name rockmongo -e mongo_name=<name to display during login> -e mongo_host=<ip address of your mongo instance> -e mongo_port=<mongo db port no> -e mongo_auth=<true/false> gilacode/rockmongo
   Example: docker run -d -p 8008:80 -link mymongodb:db -name rockmongo -e mongo_name=MYMONGO -e mongo_host=192.168.0.50 -e mongo_port=27017 -e mongo_auth=true gilacode/rockmongo

