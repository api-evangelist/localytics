---
name: Create and manage a Localytics push campaign
description: Create a push notification campaign for an app, verify it, then archive or delete it using the Localytics Campaigns And Audience API.
api: openapi/localytics-campaigns-audiences-openapi.yml
operations: [CreatePushCampaign, GetPushCampaign, editPushCampaign, ArchivePushCampaign, DeletePushCampaign]
---

# Create and manage a Localytics push campaign

Base URL: `https://dashboard.localytics.com/api/v6`
Auth: HTTP Basic — organization-level API key as username, API secret as password.

## Steps

1. **Create the campaign** — `POST /orgs/{org_id}/apps/{app_id}/push/campaigns` (`CreatePushCampaign`).
   Supply the `PushCampaignParams` body (creatives, schedule, target rules). A `201` returns the new campaign.
   Invalid parameters return `422`; bad credentials return `401`.
2. **Verify it** — `GET /orgs/{org_id}/apps/{app_id}/push/campaigns/{campaign_id}` (`GetPushCampaign`).
   `200` returns the campaign; `404` if the id is wrong.
3. **Edit if needed** — `PUT /orgs/{org_id}/apps/{app_id}/push/campaigns/{campaign_id}` (`editPushCampaign`).
4. **Archive when done** — `PUT /orgs/{org_id}/apps/{app_id}/push/campaigns/{campaign_id}/archive` (`ArchivePushCampaign`).
5. **Delete to remove entirely** — `DELETE /orgs/{org_id}/apps/{app_id}/push/campaigns/{campaign_id}` (`DeletePushCampaign`), `204` on success.

## Rules

- Actual message delivery goes through the separate Push API (`POST https://messaging.localytics.com/v2/push/<app_id>`); include a `request_id` GUID there to de-duplicate retries within 24 hours (see conventions/localytics-conventions.yml).
- Errors are HTTP-status based (401/403/404/422/500); no `application/problem+json` (see errors/localytics-problem-types.yml).
- Respect documented rate limits (rate-limits/localytics-rate-limits.yml); back off on `429`.
