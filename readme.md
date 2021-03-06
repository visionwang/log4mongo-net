MongoDB appender for log4net
----------------------------

The title says it all. Check [Log4Net site](http://logging.apache.org/log4net/) or [MongoDB site](http://www.mongodb.org/) if you need more info.

This is the official .NET implementation for the [log4mongo](http://log4mongo.org) project

Installation
------------

[Get it on NuGet](https://nuget.org/packages/log4mongo-net), or download sources and run build.cmd to build

Appender configuration sample
-----------------------------

	<appender name="MongoDBAppender" type="Log4Mongo.MongoDBAppender, Log4Mongo">
		<!-- 
		MongoDB database connection in the format:
		mongodb://[username:password@]host1[:port1][,host2[:port2],...[,hostN[:portN]]][/[database][?options]]
		See http://www.mongodb.org/display/DOCS/Connections for connectionstring options 
		If no database specified, default to "log4net"
		-->
		<connectionString value="mongodb://localhost" />
		<!-- 
		Name of the collection in database
		Optional, Defaults to "logs"
		-->
		<collectionName value="logs" />
		<field>
			<name value="timestamp" />
			<layout type="log4net.Layout.RawTimeStampLayout" />
		</field>
		<field>
			<name value="level" />
			<layout type="log4net.Layout.PatternLayout" value="%level" />
		</field>
		<field>
			<name value="thread" />
			<layout type="log4net.Layout.PatternLayout" value="%thread" />
		</field>
		<field>
			<name value="logger" />
			<layout type="log4net.Layout.PatternLayout" value="%logger" />
		</field>
		<field>
			<name value="message" />
			<layout type="log4net.Layout.PatternLayout" value="%message" />
		</field>
		<field>
			<name value="mycustomproperty" />
			<layout type="log4net.Layout.RawPropertyLayout">
				<key value="mycustomproperty" />
			</layout>
		</field>
	</appender>

License
-------

[BSD 3](https://raw.github.com/log4mongo/log4mongo-net/master/LICENSE)
