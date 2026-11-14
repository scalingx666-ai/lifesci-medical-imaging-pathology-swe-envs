# Issue

**Title:** Bump OpenTelemetry.Api from 1.16.0 to 1.19.1

## Description

Updated [OpenTelemetry.Api](https://github.com/open-telemetry/opentelemetry-dotnet) from 1.16.0 to 1.19.1.

<details>
<summary>Release notes</summary>

_Sourced from [OpenTelemetry.Api's releases](https://github.com/open-telemetry/opentelemetry-dotnet/releases)._

## 1.19.1

For highlights and announcements pertaining to this release see: [Release Notes > 1.19.1](https://github.com/open-telemetry/opentelemetry-dotnet/blob/main/RELEASENOTES.md#​1191).

The following changes are from the previous release [1.19.0](https://github.com/open-telemetry/opentelemetry-dotnet/releases/tag/core-1.19.0).

* NuGet: [OpenTelemetry v1.19.1](https://www.nuget.org/packages/OpenTelemetry/1.19.1)

  * Fixed `NotSupportedException` thrown when building a `TracerProvider` or `MeterProvider` with a large number of wildcard source/meter patterns on `net8.0`, and a related `OutOfMemoryException` that could occur when many such providers were built over the lifetime of a process.
    ()

  See [CHANGELOG](https://github.com/open-telemetry/opentelemetry-dotnet/blob/core-1.19.1/src/OpenTelemetry/CHANGELOG.md) for details.

* NuGet: [OpenTelemetry.Api v1.19.1](https://www.nuget.org/packages/OpenTelemetry.Api/1.19.1)

  No notable changes.

  See [CHANGELOG](https://github.com/open-telemetry/opentelemetry-dotnet/blob/core-1.19.1/src/OpenTelemetry.Api/CHANGELOG.md) for details.

* NuGet: [OpenTelemetry.Api.ProviderBuilderExtensions v1.19.1](https://www.nuget.org/packages/OpenTelemetry.Api.ProviderBuilderExtensions/1.19.1)

  No notable changes.

  See [CHANGELOG](https://github.com/open-telemetry/opentelemetry-dotnet/blob/core-1.19.1/src/OpenTelemetry.Api.ProviderBuilderExtensions/CHANGELOG.md) for details.

* NuGet: [OpenTelemetry.Exporter.Console v1.19.1](https://www.nuget.org/packages/OpenTelemetry.Exporter.Console/1.19.1)

  No notable changes.

  See [CHANGELOG](https://github.com/open-telemetry/opentelemetry-dotnet/blob/core-1.19.1/src/OpenTelemetry.Exporter.Console/CHANGELOG.md) for details.

* NuGet: [OpenTelemetry.Exporter.InMemory v1.19.1](https://www.nuget.org/packages/OpenTelemetry.Exporter.InMemory/1.19.1)

  No notable changes.

  See [CHANGELOG](https://github.com/open-telemetry/opentelemetry-dotnet/blob/core-1.19.1/src/OpenTelemetry.Exporter.InMemory/CHANGELOG.md) for details.

* NuGet: [OpenTelemetry.Exporter.OpenTelemetryProtocol v1.19.1](https://www.nuget.org/packages/OpenTelemetry.Exporter.OpenTelemetryProtocol/1.19.1)

  No notable changes.

  See [CHANGELOG](https://github.com/open-telemetry/opentelemetry-dotnet/blob/core-1.19.1/src/OpenTelemetry.Exporter.OpenTelemetryProtocol/CHANGELOG.md) for details.

* NuGet: [OpenTelemetry.Exporter.Zipkin v1.19.1](https://www.nuget.org/packages/OpenTelemetry.Exporter.Zipkin/1.19.1)

  No notable changes.

  See [CHANGELOG](https://github.com/open-telemetry/opentelemetry-dotnet/blob/core-1.19.1/src/OpenTelemetry.Exporter.Zipkin/CHANGELOG.md) for details.

* NuGet: [OpenTelemetry.Extensions.Hosting v1.19.1](https://www.nuget.org/packages/OpenTelemetry.Extensions.Hosting/1.19.1)

  No notable changes.
 ... (truncated)

## 1.19.1-rc.1

The following changes are from the previous release [1.19.0](https://github.com/open-telemetry/opentelemetry-dotnet/releases/tag/core-1.19.0).

* NuGet: [OpenTelemetry v1.19.1-rc.1](https://www.nuget.org/packages/OpenTelemetry/1.19.1-rc.1)

  * Fixed `NotSupportedException` thrown when building a `TracerProvider` or `MeterProvider` with a large number of wildcard source/meter patterns on `net8.0`, and a related `OutOfMemoryException` that could occur when many such providers were built over the lifetime of a process.
    ()

  See [CHANGELOG](https://github.com/open-telemetry/opentelemetry-dotnet/blob/core-1.19.1-rc.1/src/OpenTelemetry/CHANGELOG.md) for details.

* NuGet: [OpenTelemetry.Api v1.19.1-rc.1](https://www.nuget.org/packages/OpenTelemetry.Api/1.19.1-rc.1)

  No notable changes.

  See [CHANGELOG](https://github.com/open-telemetry/opentelemetry-dotnet/blob/core-1.19.1-rc.1/src/OpenTelemetry.Api/CHANGELOG.md) for details.

* NuGet: [OpenTelemetry.Api.ProviderBuilderExtensions v1.19.1-rc.1](https://www.nuget.org/packages/OpenTelemetry.Api.ProviderBuilderExtensions/1.19.1-rc.1)

  No notable changes.

  See [CHANGELOG](https://github.com/open-telemetry/opentelemetry-dotnet/blob/core-1.19.1-rc.1/src/OpenTelemetry.Api.ProviderBuilderExtensions/CHANGELOG.md) for details.

* NuGet: [OpenTelemetry.Exporter.Console v1.19.1-rc.1](https://www.nuget.org/packages/OpenTelemetry.Exporter.Console/1.19.1-rc.1)

  No notable changes.

  See [CHANGELOG](https://github.com/open-telemetry/opentelemetry-dotnet/blob/core-1.19.1-rc.1/src/OpenTelemetry.Exporter.Console/CHANGELOG.md) for details.

* NuGet: [OpenTelemetry.Exporter.InMemory v1.19.1-rc.1](https://www.nuget.org/packages/OpenTelemetry.Exporter.InMemory/1.19.1-rc.1)

  No notable changes.

  See [CHANGELOG](https://github.com/open-telemetry/opentelemetry-dotnet/blob/core-1.19.1-rc.1/src/OpenTelemetry.Exporter.InMemory/CHANGELOG.md) for details.

* NuGet: [OpenTelemetry.Exporter.OpenTelemetryProtocol v1.19.1-rc.1](https://www.nuget.org/packages/OpenTelemetry.Exporter.OpenTelemetryProtocol/1.19.1-rc.1)

  No notable changes.

  See [CHANGELOG](https://github.com/open-telemetry/opentelemetry-dotnet/blob/core-1.19.1-rc.1/src/OpenTelemetry.Exporter.OpenTelemetryProtocol/CHANGELOG.md) for details.

* NuGet: [OpenTelemetry.Exporter.Zipkin v1.19.1-rc.1](https://www.nuget.org/packages/OpenTelemetry.Exporter.Zipkin/1.19.1-rc.1)

  No notable changes.

  See [CHANGELOG](https://github.com/open-telemetry/opentelemetry-dotnet/blob/core-1.19.1-rc.1/src/OpenTelemetry.Exporter.Zipkin/CHANGELOG.md) for details.

* NuGet: [OpenTelemetry.Extensions.Hosting v1.19.1-rc.1](https://www.nuget.org/packages/OpenTelemetry.Extensions.Hosting/1.19.1-rc.1)

  No notable changes.

  See [CHANGELOG](https://github.com/open-telemetry/opentelemetry-dotnet/blob/core-1.19.1-rc.1/src/OpenTelemetry.Extensions.Hosting/CHANGELOG.md) for details.
 ... (truncated)

## 1.19.1-beta.1

The following changes are from the previous release [1.19.0-beta.1](https://github.com/open-telemetry/opentelemetry-dotnet/releases/tag/coreunstable-1.19.0-beta.1).

* NuGet: [OpenTelemetry.Exporter.Prometheus.AspNetCore v1.19.1-beta.1](https://www.nuget.org/packages/OpenTelemetry.Exporter.Prometheus.AspNetCore/1.19.1-beta.1)

  * Updated OpenTelemetry core component version(s) to `1.19.1`.
    ()

  See [CHANGELOG](https://github.com/open-telemetry/opentelemetry-dotnet/blob/coreunstable-1.19.1-beta.1/src/OpenTelemetry.Exporter.Prometheus.AspNetCore/CHANGELOG.md) for details.

* NuGet: [OpenTelemetry.Exporter.Prometheus.HttpListener v1.19.1-beta.1](https://www.nuget.org/packages/OpenTelemetry.Exporter.Prometheus.HttpListener/1.19.1-beta.1)

  * Updated OpenTelemetry core component version(s) to `1.19.1`.
    ()

  See [CHANGELOG](https://github.com/open-telemetry/opentelemetry-dotnet/blob/coreunstable-1.19.1-beta.1/src/OpenTelemetry.Exporter.Prometheus.HttpListener/CHANGELOG.md) for details.

* NuGet: [OpenTelemetry.Shims.OpenTracing v1.19.1-beta.1](https://www.nuget.org/packages/OpenTelemetry.Shims.OpenTracing/1.19.1-beta.1)

  * Updated OpenTelemetry core component version(s) to `1.19.1`.
    ()

  See [CHANGELOG](https://github.com/open-telemetry/opentelemetry-dotnet/blob/coreunstable-1.19.1-beta.1/src/OpenTelemetry.Shims.OpenTracing/CHANGELOG.md) for details.

## 1.19.0

For highlights and announcements pertaining to this release see: [Release Notes > 1.19.0](https://github.com/open-telemetry/opentelemetry-dotnet/blob/main/RELEASENOTES.md#​1190).

The following changes are from the previous release [1.18.0](https://github.com/open-telemetry/opentelemetry-dotnet/releases/tag/core-1.18.0).

* NuGet: [OpenTelemetry v1.19.0](https://www.nuget.org/packages/OpenTelemetry/1.19.0)

  * Added Schema URL to internally created `Resource` instances.
    ()

  * Reduced allocations when formatting self-diagnostics events with up to three parameters.
    ()

  * Added `AlwaysRecordSampler`.
    ()

  * Fixed `CircularBufferBuckets` so the first delta histogram insertion after a reset does not result in an unnecessary scale reduction.
    ()

  * Improved wildcard source/meter name matching to avoid excessive matching time at runtime.
    ()

  * Fixed lazy logger provider builds after a failure from reusing partially initialized provider state.
    ()

  See [CHANGELOG](https://github.com/open-telemetry/opentelemetry-dotnet/blob/core-1.19.0/src/OpenTelemetry/CHANGELOG.md) for details.

* NuGet: [OpenTelemetry.Api v1.19.0](https://www.nuget.org/packages/OpenTelemetry.Api/1.19.0)

  * Reduced allocations when creating log record attributes from an array.
    ()

  * Reduced allocations when setting baggage through the `params` overload.
    ()

  * Reduced allocations when constructing `SpanAttributes` from an array.
    ()

  * Fixed parsing of an inbound `tracestate` header whose member value trimmed to an empty value that previously threw an `IndexOutOfRangeException` internally and could silently truncate the tracestate.
    ()

  See [CHANGELOG](https://github.com/open-telemetry/opentelemetry-dotnet/blob/core-1.19.0/src/OpenTelemetry.Api/CHANGELOG.md) for details.

* NuGet: [OpenTelemetry.Api.ProviderBuilderExtensions v1.19.0](https://www.nuget.org/packages/OpenTelemetry.Api.ProviderBuilderExtensions/1.19.0)

  No notable changes.

  See [CHANGELOG](https://github.com/open-telemetry/opentelemetry-dotnet/blob/core-1.19.0/src/OpenTelemetry.Api.ProviderBuilderExtensions/CHANGELOG.md) for details.

* NuGet: [OpenTelemetry.Exporter.Console v1.19.0](https://www.nuget.org/packages/OpenTelemetry.Exporter.Console/1.19.0)

 ... (truncated)

## 1.19.0-rc.1

The following changes are from the previous release [1.18.0](https://github.com/open-telemetry/opentelemetry-dotnet/releases/tag/core-1.18.0).

* NuGet: [OpenTelemetry v1.19.0-rc.1](https://www.nuget.org/packages/OpenTelemetry/1.19.0-rc.1)

  * Added Schema URL to internally created `Resource` instances.
    ()

  * Reduced allocations when formatting self-diagnostics events with up to three parameters.
    ()

  * Added `AlwaysRecordSampler`.
    ()

  * Fixed `CircularBufferBuckets` so the first delta histogram insertion after a reset does not result in an unnecessary scale reduction.
    ()

  * Improved wildcard source/meter name matching to avoid excessive matching time at runtime.
    ()

  * Fixed lazy logger provider builds after a failure from reusing partially initialized provider state.
    ()

  See [CHANGELOG](https://github.com/open-telemetry/opentelemetry-dotnet/blob/core-1.19.0-rc.1/src/OpenTelemetry/CHANGELOG.md) for details.

* NuGet: [OpenTelemetry.Api v1.19.0-rc.1](https://www.nuget.org/packages/OpenTelemetry.Api/1.19.0-rc.1)

  * Reduced allocations when creating log record attributes from an array.
    ()

  * Reduced allocations when setting baggage through the `params` overload.
    ()

  * Reduced allocations when constructing `SpanAttributes` from an array.
    ()

  * Fixed parsing of an inbound `tracestate` header whose member value trimmed to an empty value that previously threw an `IndexOutOfRangeException` internally and could silently truncate the tracestate.
    ()

  See [CHANGELOG](https://github.com/open-telemetry/opentelemetry-dotnet/blob/core-1.19.0-rc.1/src/OpenTelemetry.Api/CHANGELOG.md) for details.

* NuGet: [OpenTelemetry.Api.ProviderBuilderExtensions v1.19.0-rc.1](https://www.nuget.org/packages/OpenTelemetry.Api.ProviderBuilderExtensions/1.19.0-rc.1)

  No notable changes.

  See [CHANGELOG](https://github.com/open-telemetry/opentelemetry-dotnet/blob/core-1.19.0-rc.1/src/OpenTelemetry.Api.ProviderBuilderExtensions/CHANGELOG.md) for details.

* NuGet: [OpenTelemetry.Exporter.Console v1.19.0-rc.1](https://www.nuget.org/packages/OpenTelemetry.Exporter.Console/1.19.0-rc.1)

  * Extended key/value list attribute handling to cover additional dictionary shapes (`IEnumerable<KeyValuePair<string, string?>>` and `IDictionary`). These attributes will be serialized as JSON objects.
    ()
 ... (truncated)

## 1.19.0-beta.1

The following changes are from the previous release [1.18.0-beta.1](https://github.com/open-telemetry/opentelemetry-dotnet/releases/tag/coreunstable-1.18.0-beta.1).

* NuGet: [OpenTelemetry.Exporter.Prometheus.AspNetCore v1.19.0-beta.1](https://www.nuget.org/packages/OpenTelemetry.Exporter.Prometheus.AspNetCore/1.19.0-beta.1)

  * **Breaking Change** The `PrometheusTranslationStrategy` enum was renamed to `PrometheusAspNetCoreTranslationStrategy`.
    ()

  * Fixed OpenMetrics `_created` series being emitted for metric points with a default start time.
    ()

  * Prometheus text/OpenMetrics escaping of label values, label names and help text is now more efficient.
    ()

  * A scrape request whose connection is aborted, or whose `X-Prometheus-Scrape-Timeout-Seconds` deadline elapses, now stops waiting for an in-progress metrics collection instead of continuing to wait for it to finish. The collection itself is not cancelled and continues running in the background.
    ()

  * Updated OpenTelemetry core component version(s) to `1.19.0`.
    ()

  See [CHANGELOG](https://github.com/open-telemetry/opentelemetry-dotnet/blob/coreunstable-1.19.0-beta.1/src/OpenTelemetry.Exporter.Prometheus.AspNetCore/CHANGELOG.md) for details.

* NuGet: [OpenTelemetry.Exporter.Prometheus.HttpListener v1.19.0-beta.1](https://www.nuget.org/packages/OpenTelemetry.Exporter.Prometheus.HttpListener/1.19.0-beta.1)

  * **Breaking Change** The `PrometheusTranslationStrategy` enum was renamed to `PrometheusHttpListenerTranslationStrategy`.
    ()

  * Fixed OpenMetrics `_created` series being emitted for metric points with a default start time.
    ()

  * Prometheus text/OpenMetrics escaping of label values, label names and help text is now more efficient.
    ()

  * Added `PrometheusHttpListenerOptions.ScrapeResponseTimeoutMilliseconds` (default `60000`) which bounds how long a scrape request waits for its response. `X-Prometheus-Scrape-Timeout-Seconds` request header values may only shorten this limit. The limit bounds the request's wait only: a metrics collection already running when it is reached is not cancelled and continues running in the background.
    ()

  * Updated OpenTelemetry core component version(s) to `1.19.0`.
    ()

  See [CHANGELOG](https://github.com/open-telemetry/opentelemetry-dotnet/blob/coreunstable-1.19.0-beta.1/src/OpenTelemetry.Exporter.Prometheus.HttpListener/CHANGELOG.md) for details.

* NuGet: [OpenTelemetry.Shims.OpenTracing v1.19.0-beta.1](https://www.nuget.org/packages/OpenTelemetry.Shims.OpenTracing/1.19.0-beta.1)

  * Updated OpenTelemetry core component version(s) to `1.19.0`.
    ()

  See [CHANGELOG](https://github.com/open-telemetry/opentelemetry-dotnet/blob/coreunstable-1.19.0-beta.1/src/OpenTelemetry.Shims.OpenTracing/CHANGELOG.md) for details.

## 1.18.0

For highlights and announcements pertaining to this release see: [Release Notes > 1.18.0](https://github.com/open-telemetry/opentelemetry-dotnet/blob/main/RELEASENOTES.md#​1180).

The following changes are from the previous release [1.17.0](https://github.com/open-telemetry/opentelemetry-dotnet/releases/tag/core-1.17.0).

* NuGet: [OpenTelemetry v1.18.0](https://www.nuget.org/packages/OpenTelemetry/1.18.0)

  * Fixed self-diagnostics log lines being silently dropped when an event message or parameter contained enough 3-byte UTF-8 characters to overflow the internal buffer estimate. Such content is now truncated.
    ()

  * Fixed activity creation throwing when multiple tracer providers return a sampler attribute with the same key.
    ()

  * Added the `otel.sdk.processor.log.processed` SDK self-observability metric.
    ()

  * Added the `otel.sdk.processor.span.processed` SDK self-observability metric.
    ()

  * `BatchActivityExportProcessor` and `SimpleActivityExportProcessor` no longer forward spans to the exporter once `Shutdown` has been called, and `BatchActivityExportProcessor.Shutdown` now waits for in-flight `OnEnd` calls to finish enqueueing before flushing.
    ()

  * Fix logger, meter and tracer providers leaking background threads if an exception is thrown by their constructor after resource creation.
    ()

  * `CircularBufferBuckets.Copy` optimized to use bulk array copies.
    ()

  * Restored configured `MaxScale` after delta exponential histogram collection.
    ()

  See [CHANGELOG](https://github.com/open-telemetry/opentelemetry-dotnet/blob/core-1.18.0/src/OpenTelemetry/CHANGELOG.md) for details.

* NuGet: [OpenTelemetry.Api v1.18.0](https://www.nuget.org/packages/OpenTelemetry.Api/1.18.0)

  * Avoid formatting exceptions and creating exception attributes when `RecordException` is called on a span that is not recorded.
    ()

  See [CHANGELOG](https://github.com/open-telemetry/opentelemetry-dotnet/blob/core-1.18.0/src/OpenTelemetry.Api/CHANGELOG.md) for details.

* NuGet: [OpenTelemetry.Api.ProviderBuilderExtensions v1.18.0](https://www.nuget.org/packages/OpenTelemetry.Api.ProviderBuilderExtensions/1.18.0)

  No notable changes.

  See [CHANGELOG](https://github.com/open-telemetry/opentelemetry-dotnet/blob/core-1.18.0/src/OpenTelemetry.Api.ProviderBuilderExtensions/CHANGELOG.md) for details.

* NuGet: [OpenTelemetry.Exporter.Console v1.18.0](https://www.nuget.org/packages/OpenTelemetry.Exporter.Console/1.18.0)

  * Added support for serializing attribute values that are key/value lists (`IEnumerable<KeyValuePair<string, object?>>`). These attributes will be serialized as JSON objects.
    ()

 ... (truncated)

## 1.18.0-rc.1

The following changes are from the previous release [1.17.0](https://github.com/open-telemetry/opentelemetry-dotnet/releases/tag/core-1.17.0).

* NuGet: [OpenTelemetry v1.18.0-rc.1](https://www.nuget.org/packages/OpenTelemetry/1.18.0-rc.1)

  * Fixed self-diagnostics log lines being silently dropped when an event message or parameter contained enough 3-byte UTF-8 characters to overflow the internal buffer estimate. Such content is now truncated.
    ()

  * Fixed activity creation throwing when multiple tracer providers return a sampler attribute with the same key.
    ()

  * Added the `otel.sdk.processor.log.processed` SDK self-observability metric.
    ()

  * Added the `otel.sdk.processor.span.processed` SDK self-observability metric.
    ()

  * `BatchActivityExportProcessor` and `SimpleActivityExportProcessor` no longer forward spans to the exporter once `Shutdown` has been called, and `BatchActivityExportProcessor.Shutdown` now waits for in-flight `OnEnd` calls to finish enqueueing before flushing.
    ()

  * Fix logger, meter and tracer providers leaking background threads if an exception is thrown by their constructor after resource creation.
    ()

  * `CircularBufferBuckets.Copy` optimized to use bulk array copies.
    ()

  * Restored configured `MaxScale` after delta exponential histogram collection.
    ()

  See [CHANGELOG](https://github.com/open-telemetry/opentelemetry-dotnet/blob/core-1.18.0-rc.1/src/OpenTelemetry/CHANGELOG.md) for details.

* NuGet: [OpenTelemetry.Api v1.18.0-rc.1](https://www.nuget.org/packages/OpenTelemetry.Api/1.18.0-rc.1)

  * Avoid formatting exceptions and creating exception attributes when `RecordException` is called on a span that is not recorded.
    ()

  See [CHANGELOG](https://github.com/open-telemetry/opentelemetry-dotnet/blob/core-1.18.0-rc.1/src/OpenTelemetry.Api/CHANGELOG.md) for details.

* NuGet: [OpenTelemetry.Api.ProviderBuilderExtensions v1.18.0-rc.1](https://www.nuget.org/packages/OpenTelemetry.Api.ProviderBuilderExtensions/1.18.0-rc.1)

  No notable changes.

  See [CHANGELOG](https://github.com/open-telemetry/opentelemetry-dotnet/blob/core-1.18.0-rc.1/src/OpenTelemetry.Api.ProviderBuilderExtensions/CHANGELOG.md) for details.

* NuGet: [OpenTelemetry.Exporter.Console v1.18.0-rc.1](https://www.nuget.org/packages/OpenTelemetry.Exporter.Console/1.18.0-rc.1)

  * Added support for serializing attribute values that are key/value lists (`IEnumerable<KeyValuePair<string, object?>>`). These attributes will be serialized as JSON objects.
    ()

  See [CHANGELOG](https://github.com/open-telemetry/opentelemetry-dotnet/blob/core-1.18.0-rc.1/src/OpenTelemetry.Exporter.Console/CHANGELOG.md) for details.

 ... (truncated)

## 1.18.0-beta.1

The following changes are from the previous release [1.17.0-beta.1](https://github.com/open-telemetry/opentelemetry-dotnet/releases/tag/coreunstable-1.17.0-beta.1).

* NuGet: [OpenTelemetry.Exporter.Prometheus.AspNetCore v1.18.0-beta.1](https://www.nuget.org/packages/OpenTelemetry.Exporter.Prometheus.AspNetCore/1.18.0-beta.1)

  * Fix concurrent scrapes returning an empty response under contention. Now the exporter will return an HTTP 500 error instead.
    ()

  * Waiting for concurrent scrapes to finish before collecting no longer blocks, which could stall concurrent scrapes being waited on.
    ()

  * Fixed the interaction between `PrometheusAspNetCoreOptions.TranslationStrategy` and content negotiation. The configured strategy is now applied before content negotiation, instead of the negotiated escaping scheme replacing the strategy's, and the `Content-Type` header now reports the escaping scheme that was applied rather than the one that was negotiated.
    ()

  * Fixed metric values and histogram bucket bounds being written with 17 significant digits instead of their shortest round-trippable representation.
    ()

  * Fixed the canonical representation used for histogram `le` and summary `quantile` label values falling back to 17 significant digits incorrectly.
    ()

  * Fixed a race where a slow scrape could return an HTTP 200 instead of 408.
    ()

  * Updated OpenTelemetry core component version(s) to `1.18.0`.
    ()

  See [CHANGELOG](https://github.com/open-telemetry/opentelemetry-dotnet/blob/coreunstable-1.18.0-beta.1/src/OpenTelemetry.Exporter.Prometheus.AspNetCore/CHANGELOG.md) for details.

* NuGet: [OpenTelemetry.Exporter.Prometheus.HttpListener v1.18.0-beta.1](https://www.nuget.org/packages/OpenTelemetry.Exporter.Prometheus.HttpListener/1.18.0-beta.1)

  * Fix concurrent scrapes returning an empty response under contention. Now the exporter will return an HTTP 500 error instead.
    ()

  * Waiting for concurrent scrapes to finish before collecting no longer blocks, which could stall concurrent scrapes being waited on.
    ()

  * A scrape which is still collecting when the listener is disposed now returns an HTTP 503 response.
    ()

  * Shutting down the listener no longer waits indefinitely for its request processing loop to stop, and no longer throws if the loop faulted.
    ()

  * Fixed the interaction between `PrometheusHttpListenerOptions.TranslationStrategy` and content negotiation. The configured strategy is now applied before content negotiation, instead of the negotiated escaping scheme replacing the strategy's, and the `Content-Type` header now reports the escaping scheme that was applied rather than the one that was negotiated.
    ()

  * Fixed metric values and histogram bucket bounds being written with 17 significant digits instead of their shortest round-trippable representation.
    ()

  * Fixed the canonical representation used for histogram `le` and summary `quantile` label values falling back to 17 significant digits incorrectly.
    ()

 ... (truncated)

## 1.17.0

For highlights and announcements pertaining to this release see: [Release Notes > 1.17.0](https://github.com/open-telemetry/opentelemetry-dotnet/blob/main/RELEASENOTES.md#​1170).

The following changes are from the previous release [1.17.0-rc.1](https://github.com/open-telemetry/opentelemetry-dotnet/releases/tag/core-1.17.0-rc.1).

* NuGet: [OpenTelemetry v1.17.0](https://www.nuget.org/packages/OpenTelemetry/1.17.0)

  No notable changes.

  See [CHANGELOG](https://github.com/open-telemetry/opentelemetry-dotnet/blob/core-1.17.0/src/OpenTelemetry/CHANGELOG.md) for details.

* NuGet: [OpenTelemetry.Api v1.17.0](https://www.nuget.org/packages/OpenTelemetry.Api/1.17.0)

  No notable changes.

  See [CHANGELOG](https://github.com/open-telemetry/opentelemetry-dotnet/blob/core-1.17.0/src/OpenTelemetry.Api/CHANGELOG.md) for details.

* NuGet: [OpenTelemetry.Api.ProviderBuilderExtensions v1.17.0](https://www.nuget.org/packages/OpenTelemetry.Api.ProviderBuilderExtensions/1.17.0)

  No notable changes.

  See [CHANGELOG](https://github.com/open-telemetry/opentelemetry-dotnet/blob/core-1.17.0/src/OpenTelemetry.Api.ProviderBuilderExtensions/CHANGELOG.md) for details.

* NuGet: [OpenTelemetry.Exporter.Console v1.17.0](https://www.nuget.org/packages/OpenTelemetry.Exporter.Console/1.17.0)

  No notable changes.

  See [CHANGELOG](https://github.com/open-telemetry/opentelemetry-dotnet/blob/core-1.17.0/src/OpenTelemetry.Exporter.Console/CHANGELOG.md) for details.

* NuGet: [OpenTelemetry.Exporter.InMemory v1.17.0](https://www.nuget.org/packages/OpenTelemetry.Exporter.InMemory/1.17.0)

  No notable changes.

  See [CHANGELOG](https://github.com/open-telemetry/opentelemetry-dotnet/blob/core-1.17.0/src/OpenTelemetry.Exporter.InMemory/CHANGELOG.md) for details.

* NuGet: [OpenTelemetry.Exporter.OpenTelemetryProtocol v1.17.0](https://www.nuget.org/packages/OpenTelemetry.Exporter.OpenTelemetryProtocol/1.17.0)

  No notable changes.

  See [CHANGELOG](https://github.com/open-telemetry/opentelemetry-dotnet/blob/core-1.17.0/src/OpenTelemetry.Exporter.OpenTelemetryProtocol/CHANGELOG.md) for details.

* NuGet: [OpenTelemetry.Exporter.Zipkin v1.17.0](https://www.nuget.org/packages/OpenTelemetry.Exporter.Zipkin/1.17.0)

  No notable changes.

  See [CHANGELOG](https://github.com/open-telemetry/opentelemetry-dotnet/blob/core-1.17.0/src/OpenTelemetry.Exporter.Zipkin/CHANGELOG.md) for details.

* NuGet: [OpenTelemetry.Extensions.Hosting v1.17.0](https://www.nuget.org/packages/OpenTelemetry.Extensions.Hosting/1.17.0)

  No notable changes.

 ... (truncated)

## 1.17.0-rc.1

The following changes are from the previous release [1.16.0](https://github.com/open-telemetry/opentelemetry-dotnet/releases/tag/core-1.16.0).

* NuGet: [OpenTelemetry v1.17.0-rc.1](https://www.nuget.org/packages/OpenTelemetry/1.17.0-rc.1)

  * Fixed a metric point reclaim data race on CPU ARM architectures.
    ()

  * The library is now marked as trim and AOT compatible.
    ()

  * Replaced the vendored copy of
    `EnvironmentVariablesConfigurationProvider` with a direct
    `Microsoft.Extensions.Configuration.EnvironmentVariables` package dependency.
    Consumers gain automatic pickup of upstream bug fixes and security patches;
    no public API or behavioural change.
    ()

  * Added a verbose `OpenTelemetry-Sdk` self-diagnostics event that is emitted
    when an activity is dropped because its local (in-process) parent is not
    recorded.
    ()

  * Added support for a Schema URL on `Resource` instances.
    ()

  * Fixed a metric storage leak that occurred when meters and instruments were
    repeatedly created and disposed.
    ()

  * Added `ExcludedTagKeys` property to `MetricStreamConfiguration` to support
    excluding specific tag keys from metric streams.
    ()

  See [CHANGELOG](https://github.com/open-telemetry/opentelemetry-dotnet/blob/core-1.17.0-rc.1/src/OpenTelemetry/CHANGELOG.md) for details.

* NuGet: [OpenTelemetry.Api v1.17.0-rc.1](https://www.nuget.org/packages/OpenTelemetry.Api/1.17.0-rc.1)

  * Fixed `TraceContextPropagator` to normalize empty `tracestate` header values
    to `null` when extracting trace context.
    (,
    )

  * The library is now marked as trim and AOT compatible.
    ()

  * **Experimental (pre-release builds only):** Updated `EnvironmentVariableCarrier.Get`
    to read only the normalized environment variable name, following the updated
    .
    Non-normalized carrier keys are no longer matched, even when they would
    normalize to the requested key.
 ... (truncated)

## 1.17.0-beta.1

The following changes are from the previous release [1.16.0-beta.1](https://github.com/open-telemetry/opentelemetry-dotnet/releases/tag/coreunstable-1.16.0-beta.1).

* NuGet: [OpenTelemetry.Exporter.Prometheus.AspNetCore v1.17.0-beta.1](https://www.nuget.org/packages/OpenTelemetry.Exporter.Prometheus.AspNetCore/1.17.0-beta.1)

  * Added a verbose-level diagnostic event for ignored metrics.
    ()

  * The library is now marked as trim and AOT compatible.
    ()

  * Fix double unit suffixes in metric names when using OpenMetrics.
    ()

  * Fix incorrect handling of leading digits in metric names for OpenMetrics.
    ()

  * Add `PrometheusAspNetCoreOptions.ScopeInfoEnabled` property to enable or
    disable scope labels in Prometheus metrics. Defaults to `true`.
    ()

  * Added support for the `dots` and `values` Prometheus UTF-8 name escaping
    schemes when negotiated via the `Accept` header.
    ()

  * Add `PrometheusAspNetCoreOptions.TargetInfoEnabled` property to enable or
    disable the `target_info` metric in Prometheus metrics. Defaults to `true`.
    ()

  * Added support for the `allow-utf-8` Prometheus UTF-8 name escaping scheme
    when negotiated via the `Accept` header.
    ()

  * Add `PrometheusAspNetCoreOptions.ResourceConstantLabels` property to select
    resource attributes to add to each metric as constant labels. Defaults to
    `null` (no resource attributes are added as metric labels).
    ()

  * Add `PrometheusAspNetCoreOptions.MaxScrapeResponseSizeBytes` to configure
    the maximum size of a scrape response. The default is now ~166 MiB.
    ()

  * A scrape whose serialized output exceeds the maximum scrape response size
    limit now responds with HTTP 500.
    ()

  * Fixed the Prometheus text exposition format emitting redundant comments.
    ()

  * Made `Accept` header content negotiation consistent with the
    `PrometheusHttpListener` endpoint.
 ... (truncated)

Commits viewable in [compare view](https://github.com/open-telemetry/opentelemetry-dotnet/compare/core-1.16.0...core-1.19.1).
</details>

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=OpenTelemetry.Api&package-manager=nuget&previous-version=1.16.0&new-version=1.19.1)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

Dependabot will resolve any conflicts with this PR as long as you don't alter it yourself. You can also trigger a rebase manually by commenting `@dependabot rebase`.

[//]: # (dependabot-automerge-start)
[//]: # (dependabot-automerge-end)

---

<details>
<summary>Dependabot commands and options</summary>
<br />

You can trigger Dependabot actions by commenting on this PR:
- `@dependabot rebase` will rebase this PR
- `@dependabot recreate` will recreate this PR, overwriting any edits that have been made to it
- `@dependabot show <dependency name> ignore conditions` will show all of the ignore conditions of the specified dependency
- `@dependabot ignore this major version` will close this PR and stop Dependabot creating any more for this major version (unless you reopen the PR or upgrade to it yourself)
- `@dependabot ignore this minor version` will close this PR and stop Dependabot creating any more for this minor version (unless you reopen the PR or upgrade to it yourself)
- `@dependabot ignore this dependency` will close this PR and stop Dependabot creating any more for this dependency (unless you reopen the PR or upgrade to it yourself)

</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7ea6d424d0b0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.