# Webhooks

Webhooks allow you to build or set up integrations which subscribe to certain events on GitBook.com. When one of those events is triggered, we’ll send a HTTP POST payload to the webhook’s configured URL. 

### Example of Integrations

- [https://slack-service.gitbook.com](https://slack-service.gitbook.com), Source Code: [GitbookIO/services-slack](https://github.com/GitbookIO/services-slack)

### Events

When configuring a webhook, you can choose which events you would like to receive payloads for. You can even opt-in to all current and future events. Only subscribing to the specific events you plan on handling is useful for limiting the number of HTTP requests to your server. You can change the list of subscribed events through the UI anytime.

By default, webhooks are only subscribed to all events. The available events are:

| Name | Description |
| ---- | ----------- |
| `all` | Any time any event is triggered (Wildcard Event). |
| `publish` | Content of the book has been updated. |

### Delivery headers

HTTP requests made to your webhook’s configured URL endpoint will contain several special headers:

| Header | Description |
| ------ | ----------- |
| `X-GitBook-Event` | Name of the event that triggered this delivery. |
| `X-GitBook-Signature` | HMAC hex digest of the payload, using the hook’s secret as the key (if configured). |
| `X-GitBook-Delivery` | Unique ID for this delivery. |


Also, the `User-Agent` for the requests will have the prefix `GitBook/`.