---
title: Headers
layout: doc-section
doc-order: 5.1
---

### Description

The Headers policy allows you to forward arbitrary values from the gateway as headers in the responseo object.

### Usage

To enable the Expression policy, add `headers` in [gateway.config.yml][gateway.config.yml] in the [policies][policies] section.

```yaml
policies:
  - headers
  # other policies
```

### Example

```yml
pipelines:
  api:
    policies:
      -
        headers:
          - action:
              headersPrefix: 'eg-',
              forwardHeaders:
                id: 'consumer.id'
                consumer-name: 'consumer.name'
                consumer-type: 'consumer.type'
                requestID: 'requestID'
                scopes: 'consumer.token.scopes'

```

### Options Reference
* `headersPrefix`: String with prefix to be added for each header. Defaults to empty string `''`
* `forwardHeaders`: Object with header name and an [expression][expression] that's catching the value

[gateway.config.yml]: {{ site.baseurl }}{% link docs/configuration/gateway.config.yml/index.md %}
[expression]: {{ site.baseurl }}{% link docs/policies/expression.md %}
[policies]: {{ site.baseurl }}{% link docs/configuration/gateway.config.yml/policies.md %}
