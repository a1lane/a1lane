# Publish steps — A1 Lane Gemini CLI extension

Status: package assembled 2026-11-08. **Not published.** No repository has
been created and nothing has been pushed anywhere.

## Steps

1. **Decide the repository (owner: Pax; founder confirms org/visibility).**
   Create a public GitHub repository holding this folder's contents at its
   root. Two naming constraints from the Gemini CLI extension reference:
   - The manifest `name` must match the extension's directory name, and on
     a GitHub install the directory takes the repository's name. So either
     name the repository **`a1lane`** (matching the manifest as shipped),
     or rename the manifest `name` to the repository name before
     publishing. `a1lane` as a repo name under the `a1lane` org may not be
     available/desirable — decide at publish time; availability UNVERIFIED.
   - Candidate homes: the existing `github.com/a1lane` org (which holds
     `a1lane-mcp`, the registry repo) or the founder's account. Founder's
     call if a new repo under a different owner is wanted.
2. **Add the gallery topic (owner: Pax).** On the repository, add the
   GitHub topic **`gemini-cli-extension`**. Per the expansion brief, the
   Gemini CLI extensions gallery (geminicli.com/extensions — the
   reference doc confirms an extension's `description` is displayed there)
   indexes public repositories carrying this topic automatically, with no
   application or email. The auto-indexing mechanism itself is UNVERIFIED
   against official Google documentation in this pass; after adding the
   topic, check the gallery listing appears and note the date.
3. **Test the real install path (owner: Pax).** On a clean machine or
   profile: `gemini extensions install <repo URL>`, restart the CLI,
   `/mcp auth a1lane`, complete the OAuth sign-in with the reviewer
   account, run `/mcp` and confirm 26 tools, then run one full
   draft → approval → publish → receipt journey on Bluesky (the reviewer
   workspace's real account). Also confirm the `url` vs `httpUrl` field
   question against that CLI version and update the manifest/README if
   needed (see README notes).
4. **Tag a release (owner: Pax).** `gemini extensions update` reads the
   version from `gemini-extension.json`; bump `version` on every change.
   The shipped version is `1.8.0`, matching the frozen MCP surface — if
   the extension's own versioning should diverge from the server surface
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
