# Project Title
Jenkins is used for Continuous Integration/Continuous Delivery/Continuous Deployment purpose

# How to configure Jenkins Job to Package(war) and to deploy war file in remote server(tomcat)
Step 1: Configuration chnages on Tomcat server
vi /opt/tomcat/conf/tomcat-users.xml
<role rolename="manager-script"/>
<role rolename="manager-gui"/>
<role rolename="admin-gui"/>
<user username="admin" password="admin_123" roles="manager-gui"/>
<user username="admin" password="admin_123" roles="admin-gui"/>
 <user username="admin" password="admin_123" roles="manager-script" />

vi /opt/tomcat/webapps/manager/META-INF/context.xml 
<!--  <Valve className="org.apache.catalina.valves.RemoteAddrValve"
         allow="127\.\d+\.\d+\.\d+|::1|0:0:0:0:0:0:0:1" /> -->

 vi /opt/tomcat/webapps/host-manager/META-INF/context.xml
<!--  <Valve className="org.apache.catalina.valves.RemoteAddrValve"
         allow="127\.\d+\.\d+\.\d+|::1|0:0:0:0:0:0:0:1" /> -->
         
         
 Step 2: install git,maven and Deploy to container Plugins from Manage Jenkins => Manage Plugins
 install git and maven on the jenkins machine
 
 Step 3:Configure job
 New Item => Enter an item name : <Job_name> => select Freestyle project => click on "Ok"
=>General : Description : <this is my first jenkins job> =>Source Code Management:  Git : Repository URL : <https://github.com/krishnamaram2                                                                                                                                          /middleware.git>
  =>Build : Add build step : Execute shell : <mvn package>  => Post-build Actions : Add post-build action : select Deploy war/ear to a container : War ear files :**/*.war  : context path : Student 
  Containers: add container : select tomcat 8.x and add credentials and tomcat url: http://18.212.64.27:8080/ => click on save and apply
