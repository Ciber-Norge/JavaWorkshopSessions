# JavaWorkshopSessions

Java-fagpraksisen vil skape engasjement rundt Java og nye teknologier. I den anledning vil vi arrangere et frivillig opplegg for å sette seg inn i bleeding-edge teknologier. Jeg foreslår at vi gjør dette ved å løse en praktisk problemstilling, for eksempel en eksempel applikasjon. 
 
Målet med dette teknologifokuset vil være at du som utvikler kan selges ut med ekspertkompetanse på nye (og mer spennende?) teknologier. 
  
Forslag til løsninger som allerede har dukket opp er:
  -          Mangekampapplikasjon (plasseringsberegning, påmelding)
  -          Event-registrering (ettersom SharePoint påmeldingen fungerer så bra, kanskje vi kan gjøre det bedre)
  -          Andre forslag??? 
   
Teknologi som så langt er nevnt:
   -          NoSQL
   -          Mikroservices (Spring Boot/Spark/dropwizard)
   -          Alternativer til Spring/Hibernate-stacken
   -          Docker
   -          Andre forslag??? 
    
Eneste krav jeg må sette er at det skal være moderne Java teknologi (f.eks. Java 8 eller alternative JVM-språk) som benyttes.

<h2>Docker containers used in this project:</h2>
<h3>Docker container for graylog</h3>
<p>This project ueses a docker container to host it's logging service with graylog2.</p>
<h4>Setup</h4>
<code>docker pull graylog2/allinone</code>
<p>In the below command, replace "adminPassword" with the desired admin password for the graylog server.</p>
<code>docker run --name graylog -v /shared/graylog/data:/var/opt/graylog/data -v /shared/graylog/logs:/var/log/graylog -d -t -p 20201:9000 -p 20202:12201 -p 20203:12202 -p 20204:12203 -e GRAYLOG_PASSWORD=adminPassword graylog2/allinone</code>
<p>After web interface is up and running, add inputs under system -> inputs</p>
<ul>
<li>GELF HTTP input on port 12201</li>
<li>GELF TCP input on port 12202</li>
<li>GELF UPD input on port 12203</li>
</ul>

<h3>Docker container for MySQL</h3>
<p>The event-service in this project uses MySQL</p>
<h4>Setup</h4>
<code>docker pull mysql</code>
<p>In the below command, replace "adminPassword", "username" and "userPassword" with the desired values.</p>
<code>sudo docker run --name event-mysql -e MYSQL_ROOT_PASSWORD=rootPassword -e MYSQL_USER=username -e MYSQL_PASSWORD=userPassword -e MYSQL_DATABASE=event_db -d -p 20101:3306 mysql</code>
<p><bold>TODO: </bold>Add persistance to MySQL</p>

Resources:
 - Trello board: https://trello.com/b/hD3K1BVG/java-workshop-sessions
 - Shared drive resources https://drive.google.com/folderview?id=0B-PXuk6P1_iefm9oTGZvc2JOQkpjaTNWT0VTNlZyaE5HZ1U4STVZdGV1ZW1RRGJpOVNEcXc&usp=sharing

 
    -Michael
