Mysql module for JBoss AS 7
===========================

Instructions:

1. Copy directory into $JBOSS_AS7_HOME/modules (the final result shoud be $JBOSS_AS7_HOME/modules/com/mysql...)
2. To create a datasource which uses the module, open the standalone.xml or standalone-full.xml file, look for the &lt;datasources&gt; tag, and use this template as example:

    <code>
	<datasource jndi-name="java:jboss/DefaultDS" pool-name="MySQLDefaultDS" enabled="true" jta="true" use-java-context="true">
		<connection-url>jdbc:mysql://localhost:3306/myappdbname</connection-url>
		<driver>mysql</driver>
		   <transaction-isolation>TRANSACTION_READ_COMMITTED</transaction-isolation>
		<pool>
		   <min-pool-size>10</min-pool-size>
		   <max-pool-size>40</max-pool-size>
		</pool>
		<security>
		   <user-name>root</user-name>
		   <password>xxx</password>
		</security>
		<validation>
		   <valid-connection-checker class-name="org.jboss.jca.adapters.jdbc.extensions.mysql.MySQLValidConnectionChecker"/>
		   <validate-on-match>
			   false
		   </validate-on-match>
		   <background-validation>
			   false
		   </background-validation>
		   <use-fast-fail>
			   false
		   </use-fast-fail>
		</validation>
		<timeout>
		   <blocking-timeout-millis>
			   5000
		   </blocking-timeout-millis>
		</timeout>
		</datasource>
		<drivers>
			<driver name="mysql" module="com.mysql.jdbc"/>
		</drivers>
	</datasource>
	</code>
