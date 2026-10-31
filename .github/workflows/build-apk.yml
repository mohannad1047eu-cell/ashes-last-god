name: Build Ashes APK

on:
  workflow_dispatch:

permissions:
  contents: read

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

      - name: Extract game project
        run: unzip -q Ashes-APK-Repository.zip

      - uses: actions/setup-java@v4
        with:
          distribution: temurin
          java-version: '17'

      - uses: android-actions/setup-android@v3

      - name: Install Android SDK
        run: sdkmanager 'platforms;android-35' 'build-tools;35.0.0'

      - uses: gradle/actions/setup-gradle@v4
        with:
          gradle-version: '8.9'

      - name: Build APK
        run: gradle -p Ashes-APK-Repository assembleDebug

      - uses: actions/upload-artifact@v4
        with:
          name: Ashes-Game-APK
          path: Ashes-APK-Repository/app/build/outputs/apk/debug/app-debug.apk
        
