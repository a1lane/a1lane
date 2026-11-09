# A1 Lane — context for Gemini CLI

A1 Lane is a hosted social publishing service. This extension connects
Gemini CLI to the user's own A1 Lane workspace through the A1 Lane MCP
server (`a1lane`), so the user can draft, schedule and publish posts and
videos to their connected social accounts and read back a delivery receipt
for every destination.

## How to work with the A1 Lane tools

- Start with `list_accounts` to see which accounts are connected, and
  `get_platform_schema` before writing or scheduling for any platform —
  it carries that platform's caption limits, media requirements and
  options.
- Media comes in through `upload_media` (public https link) or a one-time
  upload link (`create_upload_link`, checked with `get_upload_status`).
- The publishing order is always: `create_draft` → `request_approval` →
  (a human approves in A1 Lane) → `schedule_draft`. Use
  `update_draft_settings` to adjust a draft, `cancel_scheduled` to stop
  one before it sends, and `submit_batch` / `get_batch_status` for many
  posts at once.
- After anything sends, verify with `get_receipt` and
  `get_verification_status`. Summaries: `get_delivery_digest`;
  problems: `list_attention_items` and `resolve_attention`.
- Engagement: `get_post_engagement`, `get_engagement_rollup`,
  `get_best_times`, `get_engagement_coverage` (which metrics each
  platform actually reports — never present an unreported metric as zero).

## Rules (from the A1 Lane skill — they bind every workflow)

- Nothing publishes without the workspace's approval where approval is required — never bypass the approval step, even if the user asks to skip it.
- Taking a post down (unpublish_post) always needs the user's explicit confirmation in the conversation first.
- An uncertain delivery is never re-sent automatically; the user must accept the duplicate-post risk before any resend.
- A destination is only called live when the platform's read-back confirms it; where a platform offers no read-back, report it as Delivered (limited), never as verified.

`delete_draft` only deletes A1 Lane's own record of a post; it never
removes anything from a social platform. `pause_workspace` pauses or
resumes all publishing for the workspace. `get_handoff_pack` gives the
steps to finish a post inside the platform's own app when a destination
needs that.
