---
name: Build a Localytics audience and size it
description: Create a behavioral audience, list audiences, calculate its segmentation size, and edit or delete it using the Localytics Campaigns And Audience API.
api: openapi/localytics-campaigns-audiences-openapi.yml
operations: [createAudiences, ListAudiences, AudienceSegmentation, GetAudienceSegmentationCount, editAudiences, DeleteAudience]
---

# Build a Localytics audience and size it

Base URL: `https://dashboard.localytics.com/api/v6`
Auth: HTTP Basic — organization-level API key as username, API secret as password.

## Steps

1. **Create the audience** — `POST /orgs/{org_id}/apps/{app_id}/audiences` (`createAudiences`).
   Supply an `AudienceParams` body (behavior/profile rules). `201` returns the audience; `422` on invalid rules.
2. **List audiences** — `GET /orgs/{org_id}/apps/{app_id}/audiences` (`ListAudiences`) to confirm it exists.
3. **Calculate size** — `POST /orgs/{org_id}/apps/{app_id}/audiences/{audience_id}/segmentation` (`AudienceSegmentation`).
4. **Read the size** — `GET /orgs/{org_id}/apps/{app_id}/audiences/{audience_id}` (`GetAudienceSegmentationCount`) returns the segmentation count; `404` if missing.
5. **Edit** — `PATCH /orgs/{org_id}/apps/{app_id}/audiences/{audience_id}` (`editAudiences`).
6. **Delete** — `DELETE /orgs/{org_id}/apps/{app_id}/audiences/{audience_id}` (`DeleteAudience`), `204` on success.

## Rules

- A sized audience can then be targeted by a push campaign (see localytics-create-push-campaign.md).
- Errors are HTTP-status based (see errors/localytics-problem-types.yml); honor rate limits (rate-limits/localytics-rate-limits.yml).
