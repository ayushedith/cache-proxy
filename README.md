# cache-proxy

A simple Deno server that proxies requests to another service, with stale-while-revalidate caching, only refetching on a given probability. The cache is only updated if the request was successful. cache-proxy is intended to reduce load on the origin while also providing resiliency to server errors, for situations where data changes are unpredictable and outdated responses are acceptable. The Content-Type and Cache-Control response headers are preserved; beyond that, only the request path and response body are used.

Example config.ts file:
```ts
export const baseURL = 'https://example.com'
export const refetchProbability = 0.1
export const port = 1234
```

To run:
```sh
deno run --allow-net server.ts
```
