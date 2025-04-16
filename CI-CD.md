### Workflow ###

* Checkout: Retrieves source code from GitHub
* Build - Back: Compile Java back-end with Maven (mvn clean install)
* Test & Coverage - Back: Runs tests and generates JaCoCo reports for code coverage (mvn test jacoco:report)
* Build - Front: Compiles Angular front-end (npm install)
* Test & Coverage - Front: Runs tests and generates Angular coverage report with lcov (npm run test -- --watch=false --code-coverage --browsers=ChromeHeadless)
* Analyse SonarQube: Analyzes back and front-end code quality (npx sonar-scanner)
* Build Docker: Builds front and back Docker images (docker build -t ${{ secrets.DOCKER_USERNAME }}/bobapp-back ./back | /bobapp-front ./front )
* Push Docker Hub : Push images to Docker Hub (docker push ${{ secrets.DOCKER_USERNAME }}/bobapp-back | /bobapp-front)


### KPIs ###

- Minimum coverage: 80% for the back-end and 80% for the front-end
- Build time maximum: less than 5 minutes for the complete pipeline
- Test frequency: each push on main

### Metrics analysis ###
- Back-end code coverage:
- Front-end code coverage:
- 
