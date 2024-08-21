# CodePipeline mock

Basic mock of [AWS CodePipeline API](https://docs.aws.amazon.com/codepipeline/latest/APIReference/Welcome.html), which can be used with the AWS SDK, `curl` etc.

## Usage

Start the mock server:

```bash
imposter up
```

Set the `endpoint` configuration property in the AWS SDK to `http://localhost:8080`, for example:

```typescript
const client = new CodePipelineClient({
  endpoint: 'http://localhost:8080',
  // ...
});
```

For more details, see the Getting Started section.

## Getting started

### Prerequisites

Install [Imposter CLI](https://docs.imposter.sh/run_imposter_cli/).

If using Homebrew:

```
brew tap gatehill/imposter
brew install imposter`
```

Other [installation options](https://docs.imposter.sh/run_imposter_cli/) are available.

### Start

Start the mock server:

```bash
imposter up
```

### Using the mock

When using the [AWS SDK](https://docs.aws.amazon.com/AWSJavaScriptSDK/v3/latest/Package/-aws-sdk-client-codepipeline/), set the `endpoint` configuration property when creating the client:

```typescript
const client = new CodePipelineClient({
  endpoint: 'http://localhost:8080',
  // ...
});

// list pipelines
const pipelines = await client.send(new ListPipelinesCommand({}));

// list pipeline executions
const executions = await client.send(new ListPipelineExecutionsCommand({
  pipelineName: 'my-pipeline',
}));
```
