# ALL-about-apache-kafka

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
        
        - Message Producer -  PRODUCER is client application that sends data records , these records are called messages 
        - Message Consumer -  Broker is reponsible for recieveing these messages and store it local storage
        - Message Broker   -  Consumer is also a client appplication that read  messages from broker and process it 
        
        







                       
                        
                      
                        


