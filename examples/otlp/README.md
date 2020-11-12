# What is this?
A demo application that sends metrics and logs to an [Open Telemetry Collector](https://github.com/open-telemetry/opentelemetry-collector-contrib).

Messages in the Collector are forwarded to Jaeger, Zipkin, Prometheus, and Azure Monitor.

This is significant because the demo application is independent of the logging backend. Client
libraries for individual backends are not necessary, so no code changes are required to support
Zipkin, Azure Monitor etc. Instead, they can be specified as Exporters in a YAML file that
configures the Collector.

# What is missing?
This demo app shows manual instrumentation. It does not use a separate java agent for automatic
instrumentation.

# Instructions
1. Create an instance of App Insights with a Log Analytics Workspace
2. Place the App Insights Instrumentation key in `otel-collector-config-demo.yaml`
3. Start the Collector, Zipkin, Jaeger, and Prometheus: `cd docker && docker-compose up`
4. Run the java app by clicking the play button next to the main function in
`src\main\java\io.opentelemetry.example.otlp.OtlpExporterExample`
5. Access logs and metrics:
    * Jaeger (logs): `http://0.0.0.0:16686`
    * Zipkin (logs): `http://0.0.0.0:9411`
    * Prometheus (metrics): `http://0.0.0.0:9090`
    * Azure Monitor (logs): query for `dependencies` (There is usually ~2 min lag)
