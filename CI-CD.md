### Workflow ###
ci.yml:
* Checkout: Retrieves source code from GitHub
* Build - Back: Compile Java back-end with Maven (mvn clean install)
* Test & Coverage - Back: Runs tests and generates JaCoCo reports for code coverage (mvn test jacoco:report)
* Build - Front: Compiles Angular front-end (npm install)
* Test & Coverage - Front: Runs tests and generates Angular coverage report with lcov (npm run test -- --watch=false --code-coverage --browsers=ChromeHeadless)
* Analyse SonarQube: Analyzes back and front-end code quality (npx sonar-scanner)

docker-publish.yml:
* Build Docker: Builds front and back Docker images (docker compose build)
* Push Docker Hub : Push images to Docker Hub (docker push ${{ secrets.DOCKER_USERNAME }}/bobapp-back | /bobapp-front)

To launch Docker images:
Clone the project repository (git clone...), go into it and launch "docker compose up" in a terminal
After that go to "http://localhost:4200/"
