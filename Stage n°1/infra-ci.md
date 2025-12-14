# Continuous Integration (CI) - Documentation

Continuous Integration (CI) is an essential development practice that allows you to regularly merge code changes into a shared repository and automatically validate these changes. This documentation outlines the basic principles, benefits, and provides concrete examples for setting up a CI pipeline.

## 1. Why Continuous Integration?

- **Early Error Detection**  
  Every commit triggers automated tests, allowing bugs to be detected quickly and preventing regressions.

- **Improved Code Quality**  
  Regular execution of tests and static analysis ensures cleaner and more maintainable code.

- **Rapid Development Cycle**  
  Instant feedback on changes enables frequent and reliable updates.

- **Enhanced Collaboration**  
  Continuous Integration facilitates teamwork by centralizing changes and providing build reports accessible to the entire team.

## 2. Components of a CI Pipeline

A typical CI pipeline includes the following stages:

- **Build (Compilation)**  
  Prepare and compile the application.

- **Test**  
  Run unit and functional tests to validate the code.

- **Static Analysis**  
  Check the code quality with tools like PHPStan or Rector.

- **Deployment**  
  Automatically deploy the application to a test or production environment after the previous stages have been validated.

## 3. Example of a CI Pipeline with GitLab CI

Below is a simple example of a `.gitlab-ci.yml` file for a PHP project:

````yaml
# filepath: /Users/yanis.seghier/Documents/legolas/.gitlab-ci.yml
stages:
  - build
  - test
  - deploy

build:
  stage: build
  image: php:8.2-cli
  script:
    - echo "Building the application..."
    - composer install --no-interaction --prefer-dist

test:
  stage: test
  image: php:8.2-cli
  script:
    - echo "Running tests..."
    - vendor/bin/phpunit --colors=always

deploy:
  stage: deploy
  image: alpine:latest
  script:
    - echo "Deploying the application..."
    - ./deploy.sh
  only:
    - main

