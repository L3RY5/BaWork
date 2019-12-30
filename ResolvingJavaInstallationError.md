## Resolving Java installation error##

___
!!Bij het installeren van java op je Linux system als voorbereiding voor de installaties van MongoDB, Elasticsearch en Graylog, komen we een paar errors tegen. Deze documetatie is als handleiding voor het oplossen van de grootste of meest voorkomende probleem "error bericht die ik steeds krijg ". Dit betekent dat 
.....   !!
Deze Document is opgesteld op 30/10/2019
___


Java is een programmeertaal die gebruikt wordt bij zowel software development als web applicaties. Voor een volledige Java Development omgeving moeten we Java Development Kit (JDK) en Java Runtime Environment (JRE) installeren. In deze handleiding gaan we stap voor stop alle installeren voor de Debian 10 Buster Linux systeem waarop we onze Graylog server zullen installeren en configureren 


###1.Requirements###

Ten eerste gaan we "Sudo" installeren. Sudo zorgt ervoor dat je een commando kan runnen met de rechten van een Root gebruiker(Admin), vb: sudo apt-get install programmanaam. Soms kopieer je een commando van een andere pagina naar jouw terminal, met Sudo geïnstalleerd zul  je nooit de error krijgen dat het systeem "sudo" niet herkend.

`apt-get install sudo`

Nu gaan we een handelingen achter elkaar doen. de eerste commando zorgt ervoor dat de gebruiker in admin mode gaat(root). Met de tweede zorgen we ervoor dat onze systeem geüpdatet wordt. De laatste pakket bevat ALSA(Advanced Linux Sound Architecture).

>sudo -u
>
> apt update
>
>apt install wget libasound2 libasound2-data


###2.Download de Java pakket###
Nu gaan de de laatste JAVA SE Development Kit Downloaden doormidde van deze code

`wget --no-cookies --no-check-certificate --header "Cookie: oraclelicense=accept-securebackup-cookie" https://download.oracle.com/otn-pub/java/jdk/13.0.1+9/cec27d702aa74d5a8630c65ae61e4305/jdk-13.0.1_linux-x64_bin.deb`


###3.Installeer Oracle JAVA###
Nu de JAVA pakket gedownload is kunnen we het installeren dus gebruik de Debian package installer utility(dpkg)

`dpkg -i jdk-13.0.1_linux-x64_bin.deb`

!!hier was normaal error, dusafbeelding van die pc nemen zetten en de stappen die gedaan gen erbij zetten. als je deze error krijgt gelieven de stappen in 3.1 error naam te doen  anders ga naar stap 3.2 zet JAVA default versie


####!!!3.1 Error error naam####


####3.2 zet JAVA default versie####
Als je meerder er meerder versies van JAVA heb op hetzelfde systeem kun je de volgende commando's gebruiken om versie 13 de standaard te maken.

>update-alternatives --install /usr/bin/java java  /usr/lib/jvm/jdk-13.0.1/bin/java 2
>
>update-alternatives --config java


Om de installatie te voltooien we twee andere elementen als standaard instellen voor de JDK-installatie. De JAVAC en de JAR.
JAVAC is de JAVA-compiler die aanwezig is in de JDK en JAR is een data compressing zoals ZIP, JAR is de JAVA class file, metadata en all bij horende bronnen.


>update-alternatives --install /usr/bin/jar jar /usr/lib/jvm/jdk-13.0.1/bin/jar 2
>
>update-alternatives --install /usr/bin/javac javac /usr/lib/jvm/jdk-13.0.1/bin/javac 2
>
>update-alternatives --set jar /usr/lib/jvm/jdk-13.0.1/bin/jar
>
>update-alternatives --set javac /usr/lib/jvm/jdk-13.0.1/bin/javac


###4.controleer versie###
Nu de JAVA installaite voltooid is, kunnen we  de installatie controlleren door de  versie op te vragen.

>java -version
>
>!!!uitput van mijn versie(afbeelding)


###5.JAVA Environment Variables###
Meeste applicaties van JAVA gebruiken de verschillende variabelen om te kunnen werken. We gaan een script maken met alle variabelen die JAVA nodig heeft. Om dit te kunnen doen gaan we eerst VIM installeren. Vim is een tekst editor in Linux.

`apt-get install vim`

Nu Vim geïnstalleerd is kunnen we een script maken en alle variabele toevoegen.

`vi /etc/profile.d/jdk.sh`

Voeg de volgende waardes toe en sla de document op.

>export J2SDKDIR=/usr/lib/jvm/jdk-13.0.1
>
>export J2REDIR=/usr/lib/jvm/jdk-13.0.1
>
>export PATH=$PATH:/usr/lib/jvm/jdk-13.0.1/bin:/usr/lib/jvm/jdk-13.0.1/db/bin
>
>export JAVA_HOME=/usr/lib/jvm/jdk-13.0.1
>
>export DERBY_HOME=/usr/lib/jvm/jdk-13.0.1/db

Sluit het script, en de command line run je de volgende commando om de setting op te laden in deze  shell

`source /etc/profile.d/jdk.sh`

Na de succesvolle installatie kunnen we terug gaan naar de installatie van graylog. We gaan veder vanaf het deel "2.Intall MongoDB op de Virtual pc"














 




