
Part 2: Creating a student survey form and deploying on EC2 instance.

AWS URL for Homepage(Part 1) on S3 bucket: http://swe645-gss04.s3-website-us-east-1.amazonaws.com
AWS URL for Student Survey Form(Part 2) Application on EC2:  http://ec2-107-22-155-212.compute-1.amazonaws.com/SWE645Project/StudentSurveyForm.html

Steps:

1) JDK installation:

	- download and install jdk17.0.2 environment where tomcat will run
	- Set up the JAVA_HOME environment variable that points to path of your JDK installation.

2) Tomcat Installation:
	- on the internet, search " Download Tomcat"
	- Download the zip file for the latest version of Tomcat and extract it.
	- To check if Tomcat is up and running, go to http://localhost:8080 and you will be able to see the homepage
	
3) Eclipse Installation:
	- Download the latest Enterprise Edition of Eclipse IDE from http://www.eclipse.org.
	- Once downloaded, start the installation.
	- Open the IDE and create a Dynamic Web Project and configure Tomcat in Eclipse:
		- File --> New --> Dynamic Web Project
		- On the pop-up window, Change the path of Target runtime to the installed Tomcat directory and click on finish.
		- A new Dynamic Web Project will be created.
		- Right click on the servers tab and select new to define new server. Select Tomcat. You should be able to see the Tomcat server in the servers tab
		- To check if the server is working, right click and click on start. Access the homepage at localhost:8080 on the browser

	- Troubleshooting Steps
		-  If you don’t see the Server tab in the bottom portion of the Eclipse IDE, do the following:
			– Window-> Show View -> Other - > Servers
		- Once the server is started, go to localhost:8080.
		- If you get page not found error do the following:
			1) Right click on the Tomcat Server --> Properties --> Switch Location to Servers/ Tomcat...
			2) Double click on Tomcat Server and select "Use Tomcat Installation"
			3)Save changes. Restart the Server

4) JPA Configuration With Hibernate:
	- Download Hibernate: 
		- go to www.hibernate.org/downloads and download hibernate for your OS. Unzip the folder that has been downloaded
	- Download MySQL JDBC driver
		- Open browser and download MySQL Connector/J
		- Choose Platform Independent under Select Platform tab and select the zip file to download.
		- Start download, by selecting 'No thanks, start my download' on the next page.

	- Adding Hibernate/ JPA jars  and My SQL JDBC jar files to your classpath in Eclipse
		- Open Eclipse and right click on your Dynamic Web Project --> Project --> Properties.
		- A window will pop up. Click on Java Build Path --> Libraries --> ClassPath --> Add External Jars.
		- Add all the .jar files in the lib/required and lib/jpa folders of the Hibernate deployment on your computer and press OK.
		- Repeat the same steps for adding My SQL jar files to the classpath. Add External Jars --> go to folder--> select the jar file(mysql-connector-java-8.0.28.jar) and click on OK
		- Your jar files are now added to the classpath.

5) Creating a WAR file in eclipse:
	- In your dynamic web project, go to src folder -->  main --> webapps --> right click on the Web App folder --> New --> HTML file --> give a name to the HTML file and create your Student Survey Form.
	- Similarly create a CSS file.
	- To export the project, go to the Dynamic Web Project and right click --> select export --> WAR file --> Give a name to your WAR file and click Finish


6)Creating an EC2 instance on AWS
	- Sign in to your amazon management console : https://aws.amazon.com/console/
	- Click on Services --> Compute --> EC2 --> Launch Instances.
	- To choose an AMI, search Tomcat powered by Bitnami under AWS marketplace and select the one that says free-tier eligible.
	- Click on Next: Configure Instance Details --> Next: Add Storage --> Next: Tag Instances --> Next: Configure Security Groups --> Review and Launch --> Launch 
	- A window will pop up to upload you key-pair value. Select create new key --> Select a key pair : enter a key pair value --> Download private key file to download the .pem file --> Launch instances.
	- Go to the dashboard, you will see a new instance added. Within a few minutes, it will be running.


7)Deploying WAR files on EC2
	- Download WinSCP to transfer local files.
	- Setup a connection to the EC2 instance:
		- Use public DNS of your instance as the hostname.
		- Use SCP as the Protocol.
		- Use 'bitnami' as the Username.
		- Go to 'Advanced Settings' --> Shell : sudo su - --> Under Authentication tab on the left, for Private Key File browse to the path of you .pem file. Click OK to convert .pem file to .ppk file.
		- Save your settings and connect to your instance.
	- Copy your WAR file to the path : /opt/bitnami/tomcat/webapps on your instance.
	- You should now be able to access the file through the browser