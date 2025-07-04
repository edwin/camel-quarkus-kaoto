# Integration using Camel, Quarkus, and Kaoto

## Purpose
Displaying how to design a Camel integration by leveraging Kaoto, and deploy it by using Quarkus.

## Version
- Java 21
- Quarkus 3.20.1
- Apache Camel 4.10.2

## Build
```
$ podman build -f src/main/docker/Dockerfile.multistage -t camel-yaml-native-ubi9-micro-image .
```

## Result
```
.....
Build resources:
 - 5.71GB of memory (75.6% of 7.56GB system memory, determined at start)
 - 4 thread(s) (100.0% of 4 available processor(s), determined at start)
.....
------------------------------------------------------------------------------------------------------------------------
                      31.4s (10.2% of total time) in 1763 GCs | Peak RSS: 3.66GB | CPU load: 3.18
------------------------------------------------------------------------------------------------------------------------
Produced artifacts:
 /code/target/camelexample-1.0.0-native-image-source-jar/build-artifacts.json (build_info)
 /code/target/camelexample-1.0.0-native-image-source-jar/camelexample-1.0.0-runner (executable)
 /code/target/camelexample-1.0.0-native-image-source-jar/camelexample-1.0.0-runner-build-output-stats.json (build_info)
========================================================================================================================
Finished generating 'camelexample-1.0.0-runner' in 5m 5s.
[INFO] [io.quarkus.deployment.pkg.steps.NativeImageBuildRunner] objcopy --strip-debug camelexample-1.0.0-runner
[INFO] [io.quarkus.deployment.QuarkusAugmentor] Quarkus augmentation completed in 313918ms
.....
```

## How to Run
```
$ podman run -p 8080:8080 camel-yaml-native-ubi9-micro-image

__  ____  __  _____   ___  __ ____  ______
 --/ __ \/ / / / _ | / _ \/ //_/ / / / __/
 -/ /_/ / /_/ / __ |/ , _/ ,< / /_/ /\ \
--\___\_\____/_/ |_/_/|_/_/|_|\____/___/
2025-07-04 09:42:06,065 INFO  [org.apa.cam.qua.cor.CamelBootstrapRecorder] (main) Apache Camel Quarkus 3.20.0 is starting
2025-07-04 09:42:06,065 INFO  [org.apa.cam.mai.MainSupport] (main) Apache Camel (Main) 4.10.2 is starting
2025-07-04 09:42:06,071 INFO  [org.apa.cam.mai.BaseMainSupport] (main) Auto-configuration summary
2025-07-04 09:42:06,071 INFO  [org.apa.cam.mai.BaseMainSupport] (main)     [MicroProfilePropertiesSource] camel.main.routesIncludePattern = camel/hello.camel.yaml
2025-07-04 09:42:06,071 INFO  [org.apa.cam.mai.BaseMainSupport] (main)     [MicroProfilePropertiesSource] camel.context.name = quarkus-camel-example
2025-07-04 09:42:06,075 INFO  [org.apa.cam.imp.eng.AbstractCamelContext] (main) Apache Camel 4.10.2 (quarkus-camel-example) is starting
2025-07-04 09:42:06,102 INFO  [org.apa.cam.imp.eng.AbstractCamelContext] (main) Using ThreadPoolFactory: org.apache.camel.opentelemetry.OpenTelemetryInstrumentedThreadPoolFactory@6f07d414
2025-07-04 09:42:06,113 INFO  [org.apa.cam.imp.eng.AbstractCamelContext] (main) Routes startup (total:1)
2025-07-04 09:42:06,113 INFO  [org.apa.cam.imp.eng.AbstractCamelContext] (main)     Started route-2544 (timer://my-timer)
2025-07-04 09:42:06,113 INFO  [org.apa.cam.imp.eng.AbstractCamelContext] (main) Apache Camel 4.10.2 (quarkus-camel-example) started in 37ms (build:0ms init:0ms start:37ms)
2025-07-04 09:42:06,115 INFO  [io.quarkus] (main) quarkus-camel-example 1.0.0 native (powered by Quarkus 3.20.0) started in 0.086s. Listening on: http://0.0.0.0:8080
2025-07-04 09:42:06,115 INFO  [io.quarkus] (main) Profile prod activated.
2025-07-04 09:42:06,115 INFO  [io.quarkus] (main) Installed features: [camel-core, camel-management, camel-micrometer, camel-microprofile-health, camel-observability-services, camel-opentelemetry, camel-timer, camel-xml-io-dsl, camel-yaml-dsl, cdi, micrometer, opentelemetry, smallrye-context-propagation, smallrye-health, vertx]
2025-07-04 09:42:07,114 INFO  [route-2544] (Camel (camel-1) thread #1 - timer://my-timer) Hello World from Camel - route-2544
2025-07-04 09:42:08,114 INFO  [route-2544] (Camel (camel-1) thread #1 - timer://my-timer) Hello World from Camel - route-2544

```