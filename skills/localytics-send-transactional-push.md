---
name: Send a Localytics transactional push
description: Submit a batch of transactional push notifications to app users via the Localytics Transactional Push API, choosing the right target_type, de-duplicating with request_id, and handling the documented error and rate-limit responses.
api: openapi/_original/localytics-transactional-push-openapi.json
operations: ["POST /v2/push/{app_id}"]
---

# Send a Localytics transactional push

Base URL: `https://messaging.localytics.com`
Spec: served live by the provider at `https://messaging.localytics.com/swagger.json` (OpenAPI 3.0.3, `info.version` 2.0.0).
Auth: HTTP Basic — the **Push API key** as username and the **Push API secret** as password, both from the Settings screen of the Localytics dashboard. These are a different pair from the org-level API key/secret used by the Query, Profile, Events, Export and Import APIs.

> This API has **no `operationId`s**. Address its one meaningful operation by method and path: `POST /v2/push/{app_id}`.

## Steps

1. **Pick the `target_type`.** It is required and it changes every other rule in the request:
   - `customer_id` — many `messages` entries in one batch, each with its own `target` and optional per-message labels. Rate limit **1000 requests/second**.
   - `audience_id` — exactly **one** message. Rate limit **2 requests/minute**.
   - `profile` — exactly **one** message. Rate limit **100 requests/10 minutes**.
   - `broadcast` — exactly **one** message. Rate limit **2 requests/minute**.
2. **Build the batch body.** `POST /v2/push/{app_id}` with `application/json` and a `BatchRequest`: `target_type` and `messages` are required; `request_id`, `campaign_key`, `labels`, `all_devices` and `test` are optional. `additionalProperties` is `false` — an unrecognized key is a `400`, not a warning.
3. **Set `request_id` for safe retries.** A caller-supplied id, max 255 characters. Localytics de-duplicates within **24 hours** at the `app_id` + `customer_id` level. For non-`customer_id` target types a duplicate `request_id` inside the rolling window is **rejected with `400`** rather than silently ignored — so reuse it only when you intend a retry of the same batch.
4. **Set `campaign_key` if you want reporting.** Optional, max 255 characters, no whitespace, pattern `^[\w\-.]+$`. Requests sharing a `campaign_key` roll up into one dashboard performance report. You are limited to **100 new `campaign_key`s per `app_id`**, and the key is immutable once used — only its display name can be edited later.
5. **Attach labels consistently.** Up to ten labels (`label1`..`label10`) at batch level and/or per message. Per-message labels merge with batch-level labels and win on conflict. A message may use the **flat** shape (`label1` directly on the message) or the **nested** shape (a `labels` object) — mixing both on one message returns `400`.
6. **Handle the response.** `202` means the batch was accepted and queued — it is **not** a delivery confirmation. Then handle the documented failures below.

## Errors

| Status | Meaning | What to do |
|---|---|---|
| `202` | Accepted and queued for delivery | Success; delivery is asynchronous |
| `400` | Malformed request — bad JSON, invalid labels, duplicate `request_id`, campaign-key limit reached | Fix the payload; do not retry unchanged |
| `401` | Missing or invalid API credentials | Check you are using the **Push** key/secret, not the org key/secret |
| `403` | Caller not authorized for this `app_id`/`audience_id`, or the app is misconfigured (e.g. no push certificate) | Do not retry; fix configuration |
| `422` | JSON cannot be parsed at all | Fix serialization |
| `429` | Rate exceeded for the requested `target_type` | Back off — see step 1. **No `Retry-After` or `X-RateLimit-*` header is returned**, so use your own backoff schedule |
| `500` | Internal server error | Retry with backoff |

## Rules

- **No rate-limit headers exist on this API.** Nothing tells you your remaining budget; track it client-side against the per-`target_type` limits.
- **Errors are not RFC 9457.** Responses carry an ad-hoc `Error` schema, not `application/problem+json`.
- **There is no test mode credential.** The `test` boolean on the batch body is the only isolation switch; there is no test/live key separation. See `sandbox/localytics-sandbox.yml`.
- **High-volume senders should use gRPC instead.** `push.PushService/StreamPush` (see `grpc/localytics-push.proto`) is a bidirectional stream taking up to 10,000 messages and 30,000 `customer_ids` per message, and returns per-customer `PushFailure` messages the REST endpoint cannot express. Its sandbox endpoint is `trans-api-grpc.sandbox53.localytics.com:50051`.

## References

- Docs: https://docs.localytics.com/dev/push-api.html
- Spec: `openapi/_original/localytics-transactional-push-openapi.json`
- Conventions: `conventions/localytics-conventions.yml`
- Errors: `errors/localytics-problem-types.yml`
- Rate limits: `rate-limits/localytics-rate-limits.yml`
