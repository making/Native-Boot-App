```
docker run --rm \
  -v "$PWD":/usr/src \
  -v "$HOME/.m2":/root/.m2 \
  -w /usr/src \
  oracle/graalvm-ce:20.0.0-java8 \
  ./mvnw clean package -Pgraal -DskipTests

mkdir bin
mv target/com.seroter.demo.nativeapp1application bin
cf push native-app --random-route -m 32m -b binary_buildpack -p ./bin -c ./com.seroter.demo.nativeapp1application
```
