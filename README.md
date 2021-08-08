# Httpie
[httpie](https://github.com/lukeed/httpie) "like" request wrapper that use new Node.js http client [undici](https://github.com/nodejs/undici) under the hood.

## Features

- Implement httpie features.
- Able to automatically detect domains and paths to assign the right Agent (use a LRU cache to avoid repetitive computation).
- [**WIP**] Precise Rate-limit with the package `p-ratelimit`.
- [**WIP**] Built-in retry mechanism with **custom policies**.

Thanks to undici:

- Support [HTTP redirections](https://developer.mozilla.org/en-US/docs/Web/HTTP/Redirections) with the `maxRedirections` argument
- Bare metal rate-limit protection by using Undici Agent maximum connections.
- Implement high-level API for undici **stream** and **pipeline** method.
- Optimization and performance of the new client (**around 2.5x faster** than Node.js native http client).
- Work well with **newest** Node.js API [AbortController](https://nodejs.org/dist/latest-v16.x/docs/api/globals.html#globals_class_abortcontroller) to cancel http request.

## Requirements
- [Node.js](https://nodejs.org/en/) version 14 or higher

## Getting Started

This package is available in the Node Package Repository and can be easily installed with [npm](https://docs.npmjs.com/getting-started/what-is-npm) or [yarn](https://yarnpkg.com).

```bash
$ npm i @myunisoft/httpie
# or
$ yarn add @myunisoft/httpie
```

## Usage example

The MyUnisoft httpie client is very similar to lukeed httpie http client.

```js
import * as httpie from "@myunisoft/httpie";

try {
  const response = await httpie.post("https://jsonplaceholder.typicode.com/posts", {
    body: {
      title: "foo",
      body: "bar",
      userId: 1
    }
  });

  console.log(response.statusCode);
  console.log(response.statusMessage);
  console.log(response.data);
}
catch (error) {
  console.log(error.message);
  console.log(error.statusCode);
  console.log(error.headers);
  console.log(error.data);
}
```

## API

- [Request API](./docs/request.md)
- [Work and manage Agents](./docs/agents.md)
