#Stage 1
#base image for Build
FROM  maven:latest AS build-stage

#Setting the work directory
WORKDIR /app

#Copying the pom.xml from the device to the workdir (app)
COPY pom.xml /app/

#Copying the src folder to the Workdir(/app/src)
COPY src /app/src/

#cleans the previous builds and install all the packages 
RUN mvn clean install

#Stage 2
#base image for Build
FROM openjdk:23-slim-bullseye

#Setting the work directory
WORKDIR /app

#Copying the jar file from build-stage to the workdir (app)
COPY --from=build-stage /app/target/real-time-chat-app-0.0.1-SNAPSHOT.jar /app/chatapp.jar

# Make port 80 available to the world outside this container
EXPOSE 8080

# Run chatapp.jar when the container launches
CMD ["java","-jar","chatapp.jar"] 
