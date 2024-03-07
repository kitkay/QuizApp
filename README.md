# Kotlin Android Quiz App
- This quiz app is written using kotlin language

## CI/CD Pipeline
- CI/CD used for this project is going to be github actions
- From Android Studio to git to Playstore
- Events -> Jobs -> Runners -> Steps -> Actions (Github Actions)

## HowTo CI/CD using code
### Using Android Studio
- Create folder named `.github/workflows` then inside workflows add file `Androidbuild.yml`    

### Using Github Actions
- Go to github then click `actions` then setup workflows `set up a workflow yourself`

### Add this setting to either of the two options above
```
name: QuizAppBuild
on:
pull_request:
branches: [ main ]
push:
branches: [ main ]

jobs:
build:
runs-on: ubuntu-latest
steps:
- name: Checkout
uses: actions/checkout@v4.1.0

      - name: Setup Java JDK
        uses: actions/setup-java@v3.13.0
        with:
          java-version: '17'
          distribution: 'adopt'

      - name: Build with Gradle
        run: ./gradlew build

      - name: Upload a Build Artifact
        uses: actions/upload-artifact@v3.1.3
        with:
          name: QuizApp.apk
          path: app/build/outputs/apk/debug/app-debug.apk
```