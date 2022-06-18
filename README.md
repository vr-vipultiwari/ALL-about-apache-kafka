# All-About-Apache-Kafka  ( Gift to the technology world by LinkdIn )

## If we go on the documentation of apache kafka it says it is a "distributed streaming platform" 
well what does that mean ? 🤔
let me explain you in simple words , It means two things :-
                        
                        - we can create one or more real time data streams using kafka 
                        - we can also use kafka to process these stream of data and produce result in real time

when i say realtime that means in min ,sec or even mili sec 
Suppose we have a smart electricty meter at out home and it genenerating load related data every min and bringing that continuous data to kafka server 
called creation of realtime data stream.

Now suppose we have also created an application that read and process this data .
This application might be doing variety of things such monitoring and computing overall electricity load of every house.
as the load goes above 2kv , we are sending a sms to house owner to alert him.

### but the thing is if we are sending that sms after one hour , it doesn't make any sence.
    we want this alert to be sent within few mins 
   
 - In order to achieve this , our application should not accumulate data then process it , it should continuously listen to kafka and process it as soon as it arrive    at the Kafka server that is called realtime stream poccessing 

## Apache kafka is highly scalable and distributed platform for creating and processing realtime data stream 

Kafka adopted PUBLISHER-SUBSCRIBER messaging architecture and it work as enterprise messaging system 

### A TYPICAL MESSAGING SYSTEM HAS THREE COMPONENTS :
        
        - Message Producer -  PRODUCER is client application that sends data records to the broker , these records are called messages 
        - Message Consumer -  Consumer is also a client appplication that read  messages from broker and process it in realtime
        - Message Broker   -  Broker is reponsible for recieveing these messages and store it in local storage 
        
        
Later on , kafka added three more component to become real time data streaming platform  and now all new componts are described below

                                                        - kafka connect   ----> which address data intrigity problem for which kafka designed 
                                                        - kafka KSQL  ----->  Kafka to become a database 
                                                        - kafka client -----> Library to create producer and consumer application
                                                        - Kafka streams  ----> This is another library to create real time data processing application
                                                        - Kafka broker  ----> server application that can be installled on the machine 
                                                        
                                                        
🫀   
## Just like the circulatory system carries blood to all part of the body (infrastructure) same way kafka carries to data to all the part of software ecosystem 
## Producer send data to kafka as soon as bussiness event occurs  
## Consumer consumes the messages as soon as data arrive at broker


# Key terminology  :-
-----------------

### *️⃣ Producer is an application or system that sends data or message records . The message can have different meaning and structure for us but for kafka it is simple array of byte .

### *️⃣ Cunsumer is an application that recieve data from kafka server , anyone interested in that data stored on kafka sever can become consumer. Consumer can ask for data sent by any producer provided they have access to that.

Now its upto consumer application , what operation they want to perform with the data.


###  *️⃣ Broker :- Broker is nothing but kafka server 

###  *️⃣ Cluster :- Clusters are nothing but group of computers that are working togeather for a single purpose hence each kafka instance running on different computer on the kafka cluster 


## WHAT IS TOPIC IN KAFKA ❓

### 🅰️  kafka server might be getting data or message records from multiple producer and when cunsumer asking for data then, kafka might say to cunsumer which data you want . It might happen same producer sends multiple type of data for example smart electricity meter can send current load sends (every sec) , consumed unit (every hour ), voltage load (every sec ) etc. to remove this confusion Topic conccept comes into the picture .
Topic is just a placeholder in the kafka server to capture specfic type of data stream.


                                                - For our example 
                                                          - We can have three topic 
                                                            - current load 
                                                            - consumed unit 
                                                            - voltage load 

## TOPIC PARTITION  - It might happen that message can be very large even greater than the entire topic memory, in that case we can partion the topic and spread it on multiple computer in the cluster . Small and idependent portion of topic is called partition



## Consumer Group -  these are the group are the application that work togeather to accomplish the task 

EXAMPLE 
--------

Let us take example of DMART , we know that dmart have serval biilling counters in every store now they want to store all the invoice to there data center .
Here kafka can be excellent solution for this scenerio.

## The first thing we need to do is to create producer application in every billing location, these producer will send invoices to kafka as messages.
## The next thing we need to do is to create a consumer application , that will read the data from kafka topic and store it into the database.

Suppose thousands of machine pushing data into the kafka topic , this makes difficult for single kafka topic to handle this much of load . So we will take help of kafka topic partion to make the system scalable .

Topic partioning is the factor that makes kafka as scalable.



# KAFKA DON'T ALLOW MULTIPLE CONSUMER TO FETCH DATA SIMULTENOUSLY FROM SAME PARTITION

### INTRODUCTION OF KAFKA CONNECT : 

In order to understand kafka connect , let us take an example , suppose you own a supermarket and you are usimg a third party billing application for generating invoice and you want to implement kafka to send invoice to multiple systems . but the challenge here is that you need to modify your third party application to make it as producer but you don't have source code to modify it make it as a producer. to resolve this problem kafka connect commes into the picture.

It will place right between the datasource and kafka cluster . you can say it is a  readymade producer , all you need to configure it with the datasource  


There are two types of kafka connector : -  

                      - source kafka connect  - Internally uses kafka producer api to act as producer to put data into kafka server from datasource 
                      - sink kafka connect  - Internally usees kafka consumer api to act as consumer to sink data from kafka server to external database 


kafka developer created Kafka connect framework to implement kafka connector.  This framework allow you to write kafka connectors ( SinkConnector and SourceConnector )
It takes care of all the heavy liffting task scalebility , error handling , fault tollerence etc.

As a connector developer, all you need to do is to implement two Java classes. The first one is SourceConnector or SinkConnector class. And the second one is the SourceTask or the SinkTask.

Assume you want to bring some data from an RDBMS to a Kafka Cluster.All you need to do is to take an appropriate source connector, for example a JDBC source connector.
Then you install it in your Kafka connect, configure it and run it. That's all.

The Kafka Connect itself is a Cluster.Each individual unit in the Connect Cluster is called a Connect Worker. You can think of it as a group of computers, each running one Kafka Connect Worker.
 






                       
                        
                      
                        


