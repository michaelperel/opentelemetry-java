# Instructions
1. Start the collector, zipkin, jaeger, and prometheus: `cd docker && docker-compose up`
2. Run the java app by clicking the play button next to the main function in
`src\main\java\io.opentelemetry.example.otlp.OtlpExporterExample`
3. Access logs and metrics:
    * Jaeger (logs): `http://0.0.0.0:16686`
    * Zipkin (logs): `http://0.0.0.0:9411`
    * Prometheus (metrics): `http://0.0.0.0:9090`
