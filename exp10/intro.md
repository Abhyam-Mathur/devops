# Experiment 10: SonarQube

## Aim
Study SonarQube for static code analysis, quality gates, and CI/CD integration.

## Objectives
- Understand SonarQube server and scanner roles
- Learn how quality gates block bad code from deployment
- Run an analysis workflow using a token-based scan
- Connect SonarQube with Jenkins

## Theory
SonarQube is an open-source platform that checks source code for:
- Bugs
- Vulnerabilities
- Code smells
- Duplication
- Technical debt

It does static analysis, so the code does not need to run first.

## Architecture
SonarQube uses two parts:
- SonarQube Server: stores results, applies rules, and shows the dashboard
- Sonar Scanner: reads the code and sends analysis results to the server

Both are required. Without the server, there is nowhere to store results. Without the scanner, nothing gets analyzed.

## Quick Comparison
| Term | Meaning |
|---|---|
| Quality Gate | Pass/fail rule set before deployment |
| Bug | Code likely to fail at runtime |
| Vulnerability | Security weakness |
| Code Smell | Poorly written but working code |
| Technical Debt | Effort needed to fix issues |

## Start the Server
Example Docker Compose file:
```yaml
version: '3.8'

services:
  sonar-db:
    image: postgres:13
    container_name: sonar-db
    environment:
      POSTGRES_USER: sonar
      POSTGRES_PASSWORD: sonar
      POSTGRES_DB: sonarqube
    volumes:
      - sonar-db-data:/var/lib/postgresql/data

  sonarqube:
    image: sonarqube:lts-community
    container_name: sonarqube
    ports:
      - "9000:9000"
    environment:
      SONAR_JDBC_URL: jdbc:postgresql://sonar-db:5432/sonarqube
      SONAR_JDBC_USERNAME: sonar
      SONAR_JDBC_PASSWORD: sonar
    depends_on:
      - sonar-db

volumes:
  sonar-db-data:
```

Run it:
```bash
docker-compose up -d
```

Open:
```text
http://localhost:9000
```

## Sample Java App
Create a small Java project with intentional issues such as division by zero, unused variables, duplicated code, and unsafe string concatenation.

Example Sonar settings in `pom.xml`:
```xml
<properties>
  <sonar.projectKey>sample-java-app</sonar.projectKey>
  <sonar.host.url>http://localhost:9000</sonar.host.url>
  <sonar.login>YOUR_TOKEN_HERE</sonar.login>
</properties>
```

## Token Flow
1. Log in to SonarQube
2. Open My Account
3. Generate a token from the Security tab
4. Copy the token immediately
5. Pass the token to the scanner

## Run the Scan
With Maven:
```bash
mvn sonar:sonar -Dsonar.login=YOUR_TOKEN
```

With the scanner CLI:
```bash
docker run --rm \
  --network sonarqube-lab \
  -e SONAR_TOKEN="YOUR_TOKEN" \
  -v "$(pwd):/usr/src" \
  sonarsource/sonar-scanner-cli \
  -Dsonar.host.url=http://sonarqube:9000 \
  -Dsonar.projectBaseDir=/usr/src \
  -Dsonar.projectKey=sample-java-app
```

## Jenkins Integration
Typical pipeline stages:
- Checkout
- SonarQube Analysis
- Quality Gate
- Build
- Deploy

## Result
SonarQube helps catch code quality and security problems early and can block deployment when the quality gate fails.
