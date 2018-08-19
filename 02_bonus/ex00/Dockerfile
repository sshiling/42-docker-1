FROM debian

RUN apt-get update 
RUN apt-get install default-jdk -y
RUN apt-get install screen -y
RUN apt-get install wget -y
RUN mkdir minecraft && cd minecraft
RUN wget -O minecraft_server.jar https://s3.amazonaws.com/Minecraft.Download/versions/1.7.4/minecraft_server.1.7.4.jar
#RUN screen -S "Minecraft server"
EXPOSE 25565
RUN network="bridge"
RUN java -Xmx1024M -Xms1024M -jar minecraft_server.jar nogui
