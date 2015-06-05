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

If 2fa is enabled must use Oauth, else can use basic.

Easy and better than basic: [generate a
token](https://github.com/settings/tokens) and assing it to a bash
variable.

## Queries

Before running a query set your token

    TOKEN="<your personal access token>"

### Number or repos by organization

    xargs -I{} --arg-file=mozilla.orgs                                             \
	    curl -s -H "Authorization: token $TOKEN" https://api.github.com/orgs/{}    \
		| jq -r '"\(.public_repos)\t\(.login)"'                                    \
		| sort -nr --key=1                                                         \
		| awk -F '\t' -v OFS='\t' '{sum += $1; print } END { print sum, "Total" }'
