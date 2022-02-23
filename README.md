# Concourse

# concourse-ci-cd
Concourse CI pipeline of Maven Spring project

This is the simple spring boot maven hello project that contains a REST API to test the project is running successfully. It contains the concourse_ci directory that contains all about the concourse CI/CD pipeline.

**prerequisite**

- Docker
- Docker Compose
- Maven

**local testing**

Run `mvn clean package`
Then run `java -jar target/hello-springboot-0.0.1-SNAPSHOT.jar`

Now Spring boot application is running locally, Verify it by hitting the below URL

`http://localhost:8080/api/hello`

# Setup Concourse and CI/CD pipeline steps

- Download the Docker compose file

        `wget https://concourse-ci.org/docker-compose.yml`
- Run the Docker Compose File

        `docker-compose up -d`
- Download the fy CLI tool from the localhost:8080

- Give execute permission to the fly CLI

        `chmod +x fly`
- Copy the fly CLI to the /usr/bin

        `sudo cp fly /usr/bin/`
- Login to the concourse

        `fly -t tutorial login -c http://localhost:8080 -u test -p test`
- Create Concourse Pipeline

        `fly -t tutorial set-pipeline -p spring-boot-service -c concourse_ci/pipeline.yml`
- Unpause Concourse Pipeline

        `fly -t tutorial unpause-pipeline -p spring-boot-service`

**For more info follow the mentioned blog:**

https://blog.knoldus.com/concourse-ci-cd-pipeline/
