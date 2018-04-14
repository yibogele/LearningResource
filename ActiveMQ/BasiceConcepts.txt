Destination
------------

Each JMS message sent by an application is addressed with a destination. Destinations in JMS are like postal mailboxes where 
the messages are placed until someone comes to pick them up. There are two types of destination in JMS: queues and topics.

    Queues [point-to-point]: Queue’s are based on point-to-point messaging model where messages are sent to a queue. Each 
    message has exactly one sender and one receiver. Message is guaranteed to be delivered to only one receiver.
    jms-pointToPoint

    JMS Queue destination illustration. Source:Oracle
    Topics [publish-subscribe]:Topic’s are based on publish-subscribe model where messages are sent to a topic. N subscribers 
    can be subscribed on a topic, and when a message arrives, each will get a copy of that message.
    jms-publishSubscribe
    JMS Topic destination illustration. Source:Oracle

ConnectionFactory
-----------------

In order to create a connection to a messaging provider [message broker], we need connection factories. ConnectionFacotry is 
basically administrative objects with configurations parameters.

Persistent/Non-persistent Messages [Aka Delivery Mode : for Messages]
---------------------------------------------------------------------

Delivery Mode refers to persistence/non-persistence of messages which can be specified on MessageProducer level as well as on 
individual message level. Default delivery mode is PERSISTENT, means messages will be stored on disk/database until it is consumed 
by a consumer, and will survive a broker restart. When using non-persistent delivery, if you kill a broker then you will lose all 
in-transit messages.

Durable / Non-durable subscriptions[for Topics]
-------------------------------------------------

Subscription refers to subscription on a topic. With a durable subscription, if the subscriber [which has subscribed for message 
on a topic] is down for some time, once it comes up, it will receive all the messages sent for it(including the ones sent when 
it was down). With Non-durable subscription, a subscriber will receive only the messages when it was connected to topic (will 
loose all the ones sent when it was down). Note that this is not applicable for Queue’s as they can be considered always durable 
[only one consumer, and it will always receive the message destined for it in queue].
