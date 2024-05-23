
## INSTALL 

npm install @opentelemetry/sdk-node \
  @opentelemetry/api \
  @opentelemetry/auto-instrumentations-node \
  @opentelemetry/sdk-metrics \
  @opentelemetry/sdk-trace-node

  @opentelemetry/core
  @opentelemetry/node
  @opentelemetry/plugin-https
  @opentelemetry/exporter-zipkin
  @opentelemetry/tracing


## SETUP 

Create a file named instrumentation.ts (or instrumentation.js if not using TypeScript) , which will contain your instrumentation setup code.

```
/*instrumentation.ts*/
import { NodeSDK } from '@opentelemetry/sdk-node';
import { ConsoleSpanExporter } from '@opentelemetry/sdk-trace-node';
import { getNodeAutoInstrumentations } from '@opentelemetry/auto-instrumentations-node';
import {
  PeriodicExportingMetricReader,
  ConsoleMetricExporter,
} from '@opentelemetry/sdk-metrics';

const sdk = new NodeSDK({
  traceExporter: new ConsoleSpanExporter(),
  metricReader: new PeriodicExportingMetricReader({
    exporter: new ConsoleMetricExporter(),
  }),
  instrumentations: [getNodeAutoInstrumentations()],
});

sdk.start();
```


## RUN

```
$ npx ts-node --require ./instrumentation.ts app.ts


$ node --require ./instrumentation.js app.js
```
Listening for requests on http://localhost:8080

## SETUP FOR BROWSER

```
<script type="module" src="document-load.ts"></script>
```


## USEFUL LINK
https://www.youtube.com/watch?v=r8UvWSX3KA8

## RECEIVER


## PROCESSOR

## EXPORTER