#!readme

We have 3 files inside sonarqube directory:
1. docker-compose.yml
2. sonargolang/sonar-golang-plugin-1.2.11-rc3.jar
3. presetup.sh

A. Before we run docker-compose build you can move the sonar-golang plugin files into tmp files, 
1. you can copy manually or you can run presetup.sh and don't have to change the docker-compose.yml
2. you can change the path in the docker-compose.yml number 20 to your file location
   ex.
     - /yourlocation/sonar-golang-plugin-1.2.11-rc3.jar:/opt/sonarqube/extensions/plugins/sonar-golang-plugin-1.2.11-rc3.jar
B. Go to sonarqube directory (USING CLI) and run "docker-compose up -d"
C. the data is mounted to local host using volume, you can check it with run "docker volume ls"
    DRIVER              VOLUME NAME
    local               sonarqube_postgresql_data
    local               sonarqube_sonarqube_bundled-plugins
    local               sonarqube_sonarqube_conf
    local               sonarqube_sonarqube_data
    local               sonarqube_sonarqube_db
    local               sonarqube_sonarqube_extensions
   check the mounted location using "docker volume inspect <volume-name>"
D. There will be two container running named Sonarqube and PostgreSQL
E. Access the sonarQube using BUI to http://localhost:9000
F. To stop all the process you can run docker-compose down --volume
