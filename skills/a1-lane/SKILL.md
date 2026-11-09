---
name: a1-lane
description: Draft, schedule and publish social posts and videos from an A1 Lane workspace, with delivery receipts and read-back verification where the platform supports it.
---

# A1 Lane

Use A1 Lane to run a user's social publishing from this client: check which accounts are connected, draft posts, send them through the workspace's approval flow, publish now or schedule, run batches, import media into the library, review what went out and whether it landed, and take posts down with explicit confirmation.

## Tools (the live v1.8 surface — all 26)

Accounts and platform rules:
- list_accounts — List the connected social accounts in the workspace, with platform and health.
- get_platform_schema — A platform's posting rules: caption limits, media requirements and options. Check before writing or scheduling.

Media:
- upload_media — Import an image or video into the workspace library from a public https link.
- create_upload_link — Create a one-time upload link so the user can add a file from their phone or computer.
- get_upload_status — Check whether a file sent through an upload link has arrived.

Drafts and publishing:
- create_draft — Create a draft post for one or more connected accounts.
- update_draft_settings — Edit a draft or scheduled post before it sends: caption, media, destinations, timing.
- request_approval — Send a draft through the workspace approval flow.
- schedule_draft — Publish an approved draft now, at a set time, or in the next free slot.
- cancel_scheduled — Cancel a queued or scheduled post before it sends.
- delete_draft — Delete A1 Lane's own record of a post. This never removes anything from a social platform.
- submit_batch — Set up many posts at once: a week of content or a content calendar.
- get_batch_status — Check a batch's delivery, destination by destination.

Receipts and delivery:
- get_receipt — A post's delivery receipt: what was sent, where it is live, and the platform link.
- get_verification_status — Whether posts are verified live by the platform's own read-back.
- list_posts — List and filter posts: drafts, scheduled, published, failed.
- get_delivery_digest — A summary of recent deliveries: what went out and what landed.
- list_attention_items — Posts that need attention: failures, and what is waiting on the user.
- resolve_attention — Fix or retry a failed delivery, or clear an attention item.
- get_handoff_pack — The steps to finish a post inside the platform's own app.
- pause_workspace — Pause or resume all publishing for the workspace.
- unpublish_post — Delete a live post from the platforms. Always requires explicit confirmation.

Engagement:
- get_post_engagement — A post's views, likes, comments and shares, per destination.
- get_engagement_rollup — Engagement totals across accounts and posts over a period.
- get_best_times — The best weekday and hour to post on an account.
- get_engagement_coverage — Which engagement metrics each platform actually reports.

## Rules the client follows

- Nothing publishes without the workspace's approval where approval is required — never bypass the approval step, even if the user asks to skip it.
- Taking a post down (unpublish_post) always needs the user's explicit confirmation in the conversation first.
- An uncertain delivery is never re-sent automatically; the user must accept the duplicate-post risk before any resend.
- A destination is only called live when the platform's read-back confirms it; where a platform offers no read-back, report it as Delivered (limited), never as verified.
