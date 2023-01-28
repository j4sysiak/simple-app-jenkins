właściwe repo do tego projektu:
c:\Users\Jacek\Documents\GitHub\simple-app\

opis w description projektu w Jenkinsie:  http://localhost:8080/job/simple-app/

Projekt simple-app
to już robisz po wszystkich instalacjach lokalnych: docker / nexus / jenkins
aplikacja do testowania: c:\Users\Jacek\Documents\GitHub\simple-app\
git: https://github.com/j4sysiak/simple-app

odpalasz Ubuntu 20.04 LTS  (z wsl2 windowsa)
odpalasz dockera z Ubuntu:  sudo dockerd
odpalasz Jenkinsa z Ubuntu: sudo service jenkins start  / http://localhost:8080  admin / admin  (czekaj z 5 min aż się to gówno uruchomi ...)

odpalasz nexusa z Ubuntu:   powinien się sam uruchomić ze startem dockera
docker ps
CONTAINER ID   IMAGE             COMMAND                  CREATED      STATUS         PORTS                                       NAMES
53af593a1c94   sonatype/nexus3   "/opt/sonatype/nexus…"   6 days ago   Up 6 minutes   0.0.0.0:8081->8081/tcp, :::8081->8081/tcp   jacek_nexus_1
odpalenie: http://localhost:8081   admin / admin

-----------------------------------------------
ważna jest wersja w konfiguracji:  0.0.9  - taka wersja objawi się w nexusie w repozytorium simpleapp-release:
http://localhost:8081/#browse/browse:simpleapp-release

w InteliJ na projekcie starujesz w pliku pom.xml wersją np. 0.0.9 i robisz builda - powstaje plik war:
C:\Users\Jacek\Documents\GitHub\simple-app\target\simple-app-0.0.9.war
robisz commit i push go gita.
i teraz zmieniasz wersję w konfiguracji Jenkinsa tego projektu (częśc do repozytorium nexusa) na 0.0.9 i nazwę pliku target\simple-app-0.0.9.war

po uruchomieniu joba w tymm projekcie otrzymujemy w nexusie wersję:
http://localhost:8081/#browse/browse:simpleapp-release:in%2Fjavahome%2Fsimple-app%2F0.0.9%2Fsimple-app-0.0.9.war

