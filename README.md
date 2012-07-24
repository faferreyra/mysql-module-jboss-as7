Mysql module for JBoss AS 7
===========================

Instructions:

1. Copy directory into $JBOSS_AS7_HOME/modules (the final result shoud be $JBOSS_AS7_HOME/modules/com/mysql...)
2. To create a datasource which uses the module, open the standalone.xml or standalone-full.xml file, look for the &lt;datasources&gt; tag, and use this template as example:

    
	&lt;datasource jndi-name="java:jboss/DefaultDS" pool-name="MySQLDefaultDS" enabled="true" jta="true" use-java-context="true"&gt;
		&lt;connection-url&gt;jdbc:mysql://localhost:3306/myappdbname&lt;/connection-url&gt;
		&lt;driver&gt;mysql&lt;/driver&gt;
		   &lt;transaction-isolation&gt;TRANSACTION_READ_COMMITTED&lt;/transaction-isolation&gt;
		&lt;pool&gt;
		   &lt;min-pool-size&gt;10&lt;/min-pool-size&gt;
		   &lt;max-pool-size&gt;40&lt;/max-pool-size&gt;
		&lt;/pool&gt;
		&lt;security&gt;
		   &lt;user-name&gt;root&lt;/user-name&gt;
		   &lt;password&gt;xxx&lt;/password&gt;
		&lt;/security&gt;
		&lt;validation&gt;
		   &lt;valid-connection-checker class-name="org.jboss.jca.adapters.jdbc.extensions.mysql.MySQLValidConnectionChecker"/&gt;
		   &lt;validate-on-match&gt;
			   false
		   &lt;/validate-on-match&gt;
		   &lt;background-validation&gt;
			   false
		   &lt;/background-validation&gt;
		   &lt;use-fast-fail&gt;
			   false
		   &lt;/use-fast-fail&gt;
		&lt;/validation&gt;
		&lt;timeout&gt;
		   &lt;blocking-timeout-millis&gt;
			   5000
		   &lt;/blocking-timeout-millis&gt;
		&lt;/timeout&gt;
		&lt;/datasource&gt;
		&lt;drivers&gt;
			&lt;driver name="mysql" module="com.mysql.jdbc"/&gt;
		&lt;/drivers&gt;
	&lt;/datasource&gt;

