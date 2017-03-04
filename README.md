# kafka-spark-cassandra-learning-project
Just a project for learning the basics of Kafka, Spark and Cassandra for how distributing data analysis and storage can be handled.

The architehture followed will be in the form of end-user client -> kafka-producer -> kafka-broker -> kafka-consumer -> cassandra OR spark -> cassandra.

The project is about a hypothetical application dealing with *gyblets* and *madbits*. Madbit is a piece of realtime data. It could be audio data, geo tracking data, positions of a player in a video game or anything that is frequently produced in large amounts. Madbits require computationally expensive analysis, preferrably in real-time or very close to real-time.

Gyblets are less frequent data. A gyblet might be a log message about a client starting or closing an application, it might be a bug report, a contact request, or anything that might occur infrequently. Gyblets don't necessarily require much analysis, but they need transformation in the streaming phase to get them into the right format before passing them to the correct consumer.

For the purposes of this project, madbits - the real time data pieces - will be floating point values between 0 and 1. Each end-user client will try to push out 10 Gyblets a second. To analyze gyblets, some hefty matrix operations and filters will be required. The result of the analysis is then stored to a database.
