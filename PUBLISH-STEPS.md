# Publish steps — A1 Lane Gemini CLI extension

Status: **PUBLISHED 2026-11-09.** The repository is live and public at
https://github.com/a1lane/a1lane, the `gemini-cli-extension` topic is on
it (verified by read-back), and the manifest was audited against the
official Gemini CLI extension reference + MCP server documentation on
2026-11-09 — no field gaps (`name` matches the repo/directory name,
`contextFileName` points at the shipped `GEMINI.md`, `httpUrl` is the
documented field for a streamable-HTTP server, `oauth.enabled` is the
documented OAuth switch).

## Steps

1. **Decide the repository — DONE 2026-11-09.** Public repository
   `a1lane/a1lane` under the `a1lane` org; the repo name matches the
   manifest `name` (`a1lane`), so no manifest rename was needed.
2. **Add the gallery topic — DONE 2026-11-09.** Topic
   **`gemini-cli-extension`** added and read back. Gallery check on
   2026-11-09: **not yet listed** at https://geminicli.com/extensions/
   (repo created the same day; the gallery crawler is reported to
   re-index daily). Re-check the gallery search for "a1lane" from
   2026-11-10; if it is still absent after several days, revisit whether
   a release tag is required for indexing.
3. **Test the real install path (owner: Pax, in the clean interop
   sitting).** On a clean machine or profile:
   `gemini extensions install https://github.com/a1lane/a1lane`, restart
   the CLI, `/mcp auth a1lane`, complete the OAuth sign-in with the
   reviewer account (never the founder's tenant-zero workspace — run the
   workspace fingerprint check in the sitting pack first), run `/mcp`
   and confirm 26 tools, then one draft → read-back proof with NO
   publish. The full draft → approval → publish → receipt journey on
   Bluesky stays a separate, later proof.
4. **Tag a release (owner: Pax) — STILL OWED.** No tags or releases
   exist yet (checked 2026-11-09). Tag `v1.8.0` on the current main.
   `gemini extensions update` reads the version from
   `gemini-extension.json`; bump `version` on every change. The shipped
   version is `1.8.0`, matching the frozen MCP surface — if the
   extension's own versioning should diverge from the server surface
   later, record the decision here.
5. **Announce (owner: Pax).** Add the install command to A1 Lane's MCP
   client guides (https://a1lane.ai/docs/mcp-clients) once the gallery
   listing is live.

## Market note (secondary sources, UNVERIFIED against Google directly)

Multiple June–October 2026 write-ups report that Gemini CLI stopped
serving free/individual Google AI tiers in June 2026 and those users were
moved to Antigravity CLI, with Gemini CLI continuing for API-key and Code
Assist Standard/Enterprise users. If that holds, this extension's audience
is the remaining Gemini CLI base — still worth the near-zero cost of
publishing, but set expectations accordingly, and consider a follow-up
Antigravity `mcp_config.json` variant (different file/key format:
`serverUrl`) as a separate small package. Not built here.
