# storm-amqp10-spout: AMQP 1.0 input source for Storm #

This is based on a fork of https://github.com/dkincaid/storm-amqp-spout which uses older AMQP 0.91 protocol which works with RabbitMQ.   This  implementation is based on the Qpid Proton (https://qpid.apache.org/proton) library which supports AMQP 1.0 .  This spout will allow topologies to consume messages from the following messaging subsystems:

 * Apache Qpid Broker
 * Apache Qpid Dispatch Router
 * WS02
 * Apache Active MQ
 * IBM WebSphere MQ
 * Microsoft Azure Service Bus
 * Swift MQ
 * Kaazing Gateway
 * Storm MQ

storm-amqp10-spout allows a [Storm][] topology to consume an AMQP queue as an
input source.  It currently provides:

 * <tt>[AMQPSpout][]</tt>: an implementation of
   [`backtype.storm.topology.IRichSpout`][IRichSpout] that connects to an AMQP
   broker, consumes the messages routed to a specified AMQP queue and emits them
   as Storm tuples.
 * <tt>[QueueDeclaration][]</tt>: an interface that encapsulates declaring an
   AMQP queue and setting up any exchange bindings it requires, used by
   AMQPSpout to set up the queue to consume.
 * <tt>[ExclusiveQueueWithBinding][]</tt>: a QueueDeclaration suitable for
   prototyping and one-off analytics use cases.
 * <tt>[SharedQueueWithBinding][]</tt>: a QueueDeclaration suitable for
   production use cases needing guaranteed processing.

You'll need to provide a [Scheme][] to tell AMQPSpout how to interpret the
messages and turn them into Storm tuples.  See e.g. [storm-json][] if your
messages are JSON.

## Documentation ##]

TODO:

## Usage ##

To build:

    $ mvn package

To install in your local Maven repository:

    $ mvn install

To use in your `pom.xml`:
TODO: 

## Compatibility ##

[Storm]: <https://github.com/nathanmarz/storm>
    "Storm project homepage"
[IRichSpout]: <http://nathanmarz.github.com/storm/doc/backtype/storm/topology/IRichSpout.html>
    "Javadoc for backtype.storm.topology.IRichSpout"
[Scheme]: <http://nathanmarz.github.com/storm/doc/backtype/storm/spout/Scheme.html>
    "Javadoc for backtype.storm.spout.Scheme"
[AMQPSpout]: <http://code.rapportive.com/storm-amqp-spout/doc/com/rapportive/storm/spout/AMQPSpout.html>
    "Javadoc for AMQPSpout"
[QueueDeclaration]: <http://code.rapportive.com/storm-amqp-spout/doc/com/rapportive/storm/amqp/QueueDeclaration.html>
    "Javadoc for QueueDeclaration"
[ExclusiveQueueWithBinding]: <http://code.rapportive.com/storm-amqp-spout/doc/com/rapportive/storm/amqp/ExclusiveQueueWithBinding.html>
    "Javadoc for ExclusiveQueueWithBinding"
[SharedQueueWithBinding]: <http://code.rapportive.com/storm-amqp-spout/doc/com/rapportive/storm/amqp/SharedQueueWithBinding.html>
    "Javadoc for SharedQueueWithBinding"
[storm-json]: <https://github.com/rapportive-oss/storm-json>
    "JSON {,de}serialisation support for Storm"
