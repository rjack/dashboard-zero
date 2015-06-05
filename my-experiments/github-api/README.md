# GitHub API

Playing with GitHub API to extract some metrics.

## Documentation

* [Getting started](https://developer.github.com/guides/)
* [Libraries](https://developer.github.com/libraries/)

## Headers

* `Media Type`: `github.v3`
* `X-RateLimit-Limit` and `X-RateLimit-Remaining`

## Auth

Anon: 60 req / hour, need auth to increase limits.

Ff 2fa is enabled must use Oauth, else can use basic.
