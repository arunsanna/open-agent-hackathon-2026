# Open Agent Hackathon 2026 — dashboard sweep

Observed: 21 October 2026, approximately 23:03–23:05 UTC (19:03–19:05 EDT).
Scope: authenticated dashboard, linked Team Finder, onboarding/checklist state and Participant Journey Map. This supplements the existing resources intel repository; it does not re-inventory sponsor resources.

## Decision-useful read

The account is registered for Open Agent Hackathon 2026 and has completed social onboarding. Dashboard preparation is **2/3 complete**: profile and resources are complete; **team formation is incomplete**. There is **no team and no submission**, and no pending invitation or join request. A solo intention cannot be established from the observed account state. The build window begins **22 October at 00:00 UTC / 21 October at 20:00 EDT**.

No team was created, joined or selected. Those actions remain outstanding for Arun or a separately authorized operator.

## Connection and method

- Before any page read, `opencli --profile personal doctor` returned `extensionConnected:true`, `connectivity.ok:true`, and daemon running. CLI 2.0.0; extension 1.0.22. An update notice was informational; nothing was installed or changed.
- Used profile alias `personal`, session `hackathon-dashboard-sweep`, background window mode.
- Opened the supplied dashboard URL and its observed `/teams` link, using the same run-owned tab.
- Extracted page text and inspected checklist accessibility labels. Retrieved authenticated JSON bodies using `opencli browser network --detail <observed-key>`; these were captured GET responses, not manually issued write requests.
- After navigation, the network cache required a fresh network listing before a resource detail lookup succeeded. The successful 200 body is the evidence used below.
- No raw network capture, profile dump, token, cookie, email or credential was saved.

## Current checklist and journey state

| Item | Observed state | Evidence |
|---|---|---|
| Event enrollment | One joined event: Open Agent Hackathon 2026 | GET `/api/v1/hackathons/my/` returned a one-element array |
| Social onboarding | Complete; no onboarding required | GET `/api/v1/users/me/`: `onboarding_completed:true`, `needs_onboarding:false` |
| Social steps | Discord, LinkedIn and X completed on 16 October | GET `/api/v1/users/me/onboarding/`; LinkedIn and Twitter required, Discord optional |
| Community display | “2 of 2 done”; all three displayed social items complete | Dashboard text; required/optional distinction explains the count |
| Journey | `preparing` | GET `/api/v1/users/me/` |
| Profile | Dashboard marks complete | DOM aria-label `Complete your profile complete` |
| Team formation | Incomplete | DOM aria-label `Form a team incomplete` |
| Resources | Complete, 7/7 reviewed | DOM aria-label `Review hackathon resources complete`; progress response contains seven `is_read:true` records |
| Other stored checklist fields | `checklist_profile:false`, `checklist_browse_hackathons:true`, `checklist_resources:true`, `checklist_dismissed:false` | Profile GET body; legacy/stored profile flag differs from live UI |
| Team preference | `looking_for_team:false` | Profile GET body; this alone does not establish a solo selection |
| Submission | None; status `no_team` | Dashboard summary: `has_team:false`, `submission:null` |

The seven completed onboarding resources are Welcome Guide; Participant Journey Map; Hackathon Overview; How APPROACH Solutioning For Your Use Case; Event Calendar; FAQ; Participant Setup Guide. All seven were already marked read before this sweep. No resource was opened through its marking-as-reviewed control.

## Team status and available paths

Dashboard: “No team” and “Join or create a team to submit a project.”

Authenticated GET responses:

- `/api/v1/teams/my-all/` → `[]`
- `/api/v1/hackathons/019fd164-82b9-7382-a536-d9093c576ed2/teams/my/` → `null`
- `/api/v1/teams/my-invitations/` → `[]`
- `/api/v1/teams/my-join-requests/` → `[]`

Team Finder offers Create Team, Teams, Builders, My Invitations and My Requests. Its AI Team Builder says creating a proposed team sends invitations automatically; that flow was not used. Existing cards include solo builds, but none was inferred to belong to this account.

The event API allows teams of **1–5**. Journey Map guidance says each participant may belong to exactly one team, solo entries compete with teams, and composition locks when the first submission is created. The announcement asks participants to create/join a team or choose solo before kickoff; the dashboard deadline description says teams may still form until the first submission is created.

## Key dates and deadlines

All original portal times are UTC; Eastern conversions below use New York time.

| Milestone | UTC | Eastern | Source |
|---|---|---|---|
| Participant onboarding | 21 Oct 2026, 12:00–13:30 | 21 Oct, 08:00–09:30 EDT | Dashboard summary starts_at; Journey Map supplies end |
| Build opens | 22 Oct 2026, 00:00 | 21 Oct, 20:00 EDT | Joined-event API and Journey Map |
| Registration closes — dashboard/API | 22 Oct 2026, 23:59 | 22 Oct, 19:59 EDT | Joined-event API and dashboard summary |
| Registration closes — Journey Map | 22 Oct 2026, 23:45 | 22 Oct, 19:45 EDT | Journey Map; conflicts with dashboard/API |
| Submissions close / event ends | 27 Oct 2026, 23:45 | 27 Oct, 19:45 EDT | Joined-event API, dashboard summary and Journey Map agree |
| Judging begins | From 28 Oct 2026; time unspecified | Not converted | Journey Map |
| Results call | 6 Nov 2026, 16:00 | 6 Nov, 11:00 EST | Journey Map |

Build Day and Power Day workshop dates remain “to be confirmed” in the Journey Map; this sweep did not establish newer scheduling. The dashboard shows the onboarding YouTube link below.

## Useful observed links

- [Dashboard](https://hackathon.genai.works/dashboard)
- [Team Finder](https://hackathon.genai.works/teams)
- [Resources hub](https://hackathon.genai.works/resources) — the Journey Map is a resource button, not an observed standalone URL.
- [Event page](https://hackathon.genai.works/event/open-agent-hackathon-2026) — observed in Journey Map; not navigated.
- [Participant onboarding video](https://www.youtube.com/watch?v=48GKYJfwoB8) — dashboard summary event link; not played.
- [Hackathon Academy course](https://academy.genai.works/courses/open-agent-hackathon-2026/details) — observed in Journey Map; not navigated.
- [Mentor Hub](https://hackathon.genai.works/mentors) and [Messages](https://hackathon.genai.works/messages) — observed navigation links; not opened.

## Gaps and conflicting guidance

1. **Team/solo decision is unresolved in observed state.** No team exists. `looking_for_team:false` is not evidence that solo onboarding has been completed. No create/join/solo action was attempted.
2. **Registration deadline conflict:** dashboard/API say 23:59 UTC; Journey Map repeatedly says 23:45 UTC on 22 October. Preserve both; use the earlier cutoff for planning until the organizer clarifies.
3. **Demo requirements conflict:** dashboard summary says a running deployment, repository and demo of three minutes or less. Journey Map specifies a 1–4 minute video, slide deck, repository/README and sponsor technology explanation. A 1–3 minute video meets both stated duration ranges, but the full requirements still need confirmation before submission.
4. **Profile flag discrepancy:** live dashboard marks profile complete despite `checklist_profile:false`. This sweep records the discrepancy without calling the profile incomplete or trying to change it.
5. **Read completion is not technical readiness:** 7/7 review flags do not prove sponsor accounts, credits, framework, environment or integrations work. No readiness test was authorized or run.
6. No selected primary track can be established without a team workspace. The event lists three primary tracks plus the Wildcard bonus track.
7. Journey Map calls the build period 144 hours, while its explicit start/end boundaries span 143 hours 45 minutes. Use the explicit deadline.
8. No standalone onboarding/checklist URL was exposed by the dashboard links. The checklist is inline; its authenticated onboarding API and linked Journey Map supply the evidence. No URL was guessed.

## Evidence ledger

API origin: `https://hackathon-server.genai.works`.
All bodies below were read through OpenCLI network detail and returned HTTP 200.

| Captured GET body | What it proves |
|---|---|
| `/api/v1/hackathons/my/` | Enrollment, title, exact dates, timezone, team size 1–5, four tracks |
| `/api/v1/users/me/` | Non-identifying journey/checklist/team booleans only retained |
| `/api/v1/users/me/onboarding/` | Required/optional social steps and completed onboarding |
| `/api/v1/teams/my-all/` | No account teams |
| `/api/v1/teams/my-invitations/` | No invitations |
| `/api/v1/teams/my-join-requests/` | No join requests |
| `/api/v1/hackathons/019fd164-82b9-7382-a536-d9093c576ed2/teams/my/` | No current-event team |
| `/api/v1/hackathons/019fd164-82b9-7382-a536-d9093c576ed2/resources/progress/` | Seven pre-existing reviewed resources |
| `/api/v1/hackathons/019fd164-82b9-7382-a536-d9093c576ed2/resources/` | Required-resource titles and Participant Journey Map content |
| `/api/v1/hackathons/019fd164-82b9-7382-a536-d9093c576ed2/dashboard/summary/` | Schedule, deadlines, no-team/no-submission state, onboarding video |

Dashboard/initial API capture: approximately 23:03:01 UTC. Team-state capture: approximately 23:03:40 UTC. No guessed events endpoint was requested; this portal supplied `hackathons/my/` and `dashboard/summary/`.

## Read-only and house-clean receipt

- No state-changing clicks, joins, submissions, registrations, agreements, form fills or account changes.
- No commits, pushes, code changes, credential reads or configuration changes.
- Passive application telemetry occurred during normal navigation; no intentional application write request was issued.
- The sole authored filesystem file is `/tmp/hackathon-intel/dashboard-sweep.md`.
- Run-owned tab `CA2F321EDF6198AA708D142831E57433` was closed successfully.
- OpenCLI returned “Browser session tab lease released” for `hackathon-dashboard-sweep`.
- No retained scratch files, screenshots or extra tabs. No browser/daemon/extension update performed.
