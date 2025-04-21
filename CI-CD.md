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

### KPIs ###

- Minimum coverage: 80% for the back-end and 80% for the front-end
- Build time maximum: less than 5 minutes for the complete pipeline
- Test frequency: each push on main

### Metrics analysis ###
- Back-end code coverage: 32%
- Front-end code coverage: 76.92%
- Sonar Security rating: A (0 issue & 2 security Hotspots)
- Sonar Reliability rating: D (1 issue)
- Sonar Maintainability rating: A (10 issues)
