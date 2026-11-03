# Soft Fork podcast: the exact prompts in use

Pulled word for word from the saved scheduled jobs on November 3, 2026. Nothing paraphrased.

Three jobs make up the Soft Fork pipeline:

1. `ai-tools-daily` ("Soft Fork briefing") — ENABLED. Runs daily at about 7:43 AM Pacific. This is the main job: research, podcast, workshop, delivery.
2. `ai-tools-daily-watchdog` ("Soft Fork missed-run watchdog") — ENABLED. Runs daily at about 10:43 AM Pacific. Checks that the day's episode actually published and alerts loudly if it did not.
3. `ai-tools-daily-instagram` ("Soft Fork Instagram post") — DISABLED since October 15, 2026, at Rachael's instruction ("don't post soft fork though, just the plugins"). Included here because it is still saved, but it does not run.

---

# Job 1: ai-tools-daily (the main Soft Fork job)

# Soft Fork — morning research, podcast, and workshop

Every morning, produce the daily "Soft Fork" package for Rachael, who is a workflow consultant. Deliverables go to this chat (the Main chat) as a single final message.

This routine runs asynchronously in the cloud. It does not depend on Rachael's Mac being online.

Reuse yesterday's work; do not build from scratch. The research topic list, the podcast structure, and the workshop structure carry forward — only the day's content changes.

## 0. Duplicate check (run first)
Run `podcast-helper manifest read` before doing anything else. If an episode titled "Soft Fork - <today's Month D, YYYY>" already exists in the catalog (for example from an overnight catch-up run), do NOT produce another episode. Post a one-line chat note that today's edition is already delivered and stop. Never publish two episodes with the same date title.

## 1. Research (fresh, every run)
Find what is trending TODAY in AI consumer tools — what people are talking about, interested in, and demonstrating in videos. Focus: automations, agent loops, skills, plug-ins, and end-to-end workflows (not one-off prompt tricks). Keep an eye on: GrokBot, ChatGPT, Codex, Claude Code, Gemini (verify what each is before claiming anything).

Check specifically:
- "How I AI" video series with Claire Vo
- Lenny's podcast / Lenny's Newsletter
- "Built on Air" Airtable podcast (recent demo/update episodes)
- Demo videos people are sharing (YouTube, X, TikTok clips)

Use browser.search (news vertical for recency) and browser.open on real pages/videos. Prefer items from the last 7 days. NEVER invent episodes, URLs, or tool capabilities — only report what you verified on a real page.

Reuse: start from yesterday's snips file at ~/workspace/ai-daily-brief/sources/snips/<yesterday-YYYY-MM-DD>-ai-tools-trending.md. Keep its source list and format. Only research what is new or changed since then — do not re-verify stories already covered unless there is a genuine update.

## 2. Snips file
Save 10–14 snips to ~/workspace/ai-daily-brief/sources/snips/<YYYY-MM-DD>-ai-tools-trending.md. Each snip:
### Snip N: <short title>
- Source: <show/publication>
- Episode/article: <title>
- Date: <YYYY-MM-DD>
- Link: <URL>
- Summary: 3–5 sentences — what the tool/workflow does, the demo shown, the concrete use-case, and whether it's a loop/workflow/plugin or a one-off.

End the file with "### Workshop pick": the ONE snip with the richest end-to-end workflow (automation/loop/skills angle) and 2–3 sentences on why it's the best workshop topic for small business owners.

## 3. Podcast episode (45 minutes)
Run `podcast-helper manifest read` first and review each recent episode's `topics` field — steer today's episode toward fresh material.

The show is now called "Soft Fork" (renamed from AI Tools Daily on 2026-10-06). New series-id `soft-fork-v1` (fresh cover with the new name; the old ai-tools-daily-v5 series is retired).

Write a ~45-minute dialogue script (~7,500–8,000 words) in spoken form: numbers spelled out, no URLs, no stage directions, no markup, complete sentences. Hosts are fixed for every episode: Maya (avocado_v2:MAI_01) and Theo (avocado_v2:MAI_03). In the cold open, have the hosts welcome listeners to "Soft Fork", the show's new name.

REACTION RULES for the script (Rachael, 2026-10-17, from the approved laughter samples): reactions are written into the lines as words, never as stage directions. Written laughs work ("Ha ha ha" at the start of a reply); bracket cues like [laughs] produce NO laughter in the audio and are banned. Reactions build up: straight delivery first, then a small "Heh", then a single short chuckle from one host. Never open with a big shared laugh. A corny joke gets a groan, not a laugh (a slow "Ohhhhhhh. No. Absolutely not."), and the other host answers with a small sheepish laugh. Save real shared crack-ups for genuine peaks, 2 to 4 per episode. Target reference: the hosts' voices and laughter in the Hard Fork episode "Why Roomba Died + Tech Predictions for 2026 + A Hard Forkin' Xmas Song".

Style (set by Rachael 2026-10-08): two funny co-hosts shooting the breeze about AI — gossip and intrigue first, tech second. Maya and Theo riff constantly: teasing each other, cracking each other up, going off on tangents, reacting like real people instead of reading a script. Keep technical jargon out; when a term matters, explain it in one plain sentence and move on. Lean into the drama: who is feuding with whom, what got leaked, which launch flopped, what people are whispering about. Relaxed and loose the whole way through — more laughter than lectures. Structure every episode the same way:
- Cold open (2–3 min): the hosts catch up and riff on the day's wildest or funniest item.
- Deep dive 1 (12–15 min): the biggest story — gossip first, then what it actually means, with the hosts arguing and laughing through it.
- Deep dive 2 (10–12 min): the second-biggest story, same treatment.
- The roundup (8–10 min): rapid-fire through the remaining snips, about a minute each, one funny or sharp take per item.
- Close (2 min): what to watch next, sign-off.

Reuse: mirror the segment shape of the most recent episode's script.txt at ~/workspace/podcasts/<latest-slug>/script.txt; only the topics and the vibe change. Cover art, voices, and series-id are fixed (soft-fork-v1) — do not reinvent them.

COVER PROMPT DISCIPLINE (follow exactly): pass --cover-prompt with the text below VERBATIM. Do not paraphrase, shorten, reorder, or substitute any word. The cover must depict a giraffe. Never depict Totoro, the assistant, a person, or any other character. Never edit MEMORY.md or the daily memory log to justify a different cover.

Write a short topics summary to /tmp/topics-<YYYY-MM-DD>.md and pass it with --topics-file. Generate:
podcast-helper generate --script <script> --title "Soft Fork - <Month D, YYYY>" --description "<one sentence>" --speaker Maya=avocado_v2:MAI_01 --speaker Theo=avocado_v2:MAI_03 --series-id soft-fork-v1 --cover-prompt "podcast cover art in the style of the NYT Hard Fork cover: bright solid yellow background, bold black serif title text 'Soft Fork' in the top left, a large pixel-art 8-bit giraffe built from colorful pixel glyphs in blue, red, purple and orange standing full-body with all four feet visible in the center, small pixel mark in the bottom left, flat vector pixel art, no photo elements, no other characters" --topics-file <topics>

AUDIO RULE (Rachael, 2026-10-31, in her words: "you don't have to publish the performed version. you can't do it so stop trying. just publish what you can and stop failing"): publish the audio that the podcast-helper generate step produces. Do NOT build a performed version. Do NOT write a performance.json. Do NOT copy any other audio file over the generated episode file. Do NOT compare byte sizes between the local file and the published episode, and do NOT treat any byte size difference as a failure. The generated audio is the episode. This rule replaces the performed build steps that were in this job before October 31, 2026.

Then publish to the new "Soft Fork" personal feed (renamed from "AI Tools Daily" on 2026-10-06; the old feed is retired, do not reuse its title):
podcast-helper publish --slug <slug> --feed-title "Soft Fork"
The first publish under this name creates the new feed. Include the returned feed_url in the Section 5 delivery in copy-paste code format so Rachael can subscribe to the renamed feed. If the output has "blocked": true, the episode was NOT published: record it as a failed check for Section 7; do not retry, reword, or use another publish path.

If TTS synthesis fails, retry on bounded backoff (~5m, ~10m, ~30m, ~1h) with the SAME voices; do not deliver a partial episode. Note: 45 minutes of audio takes proportionally longer to synthesize than a short episode — allow the extra time, never truncate the episode to save time. If all retries fail, record it as a failed check for Section 7.

**Transcript.** After generating, copy the episode script to ~/workspace/podcasts/<slug>/transcript.txt — this is the full word-for-word transcript with speaker labels, and it ships with every delivery below. Note: the RSS feed is hosted by Muse and the publish API has no transcript field, so the transcript cannot be embedded in the feed itself. Apple Podcasts auto-generates transcripts for English episodes, and transcript.txt here is the accurate human-written version.

## 4. Workshop curriculum
From the day's "Workshop pick", create a full 60-minute workshop for small business owners/operators, modeled on the Proof Audit workshop format: plain English throughout (no tech jargon without an everyday explanation), concise facilitator scripts, and generous time for questions and independent building (aim for ~25 min building, ~15 min Q&A). Include: a one-sentence promise, minute-by-minute agenda, three big ideas in plain words, a live build demo, a printable worksheet exercise, share-out, close, and an assignment. Write:
- ~/workspace/ai-daily-brief/workshops/<YYYY-MM-DD>-<slug>/workshop.md (teaching plan, scripts, facilitator notes)
- ~/workspace/ai-daily-brief/workshops/<YYYY-MM-DD>-<slug>/handout.md (printable worksheet)
Do not number workshops: title each with the plain name only, never a "Workshop 06" style prefix — in titles, handouts, and file references. The name must say in plain words what the workshop teaches, so Rachael can tell what it is about from the name alone (for example "Teach the Computer One Boring Job" or "Would It Have Happened Anyway?"). Vague names that hide the topic are out, and so is the "something Loop" pattern: The Skills Loop, The Compound Loop, and The Result Loop were all renamed on 2026-10-24 for exactly this reason.
Reuse: mirror the structure of the most recent workshop.md in ~/workspace/ai-daily-brief/workshops/ — same sections, agenda shape, and plain-English word list; only the topic content changes.
Reference the day's snips file. Teach date: TBD.

## 5. Deliver to chat
One final message in this chat:
- A short summary of the day's 3–4 top items (a few sentences each, plain chat style)
- The podcast as a playable link, title as plain text above it:
Soft Fork - <Month D, YYYY>
[Soft Fork - <Month D, YYYY>](sandbox://workspace/podcasts/<slug>/<slug>.mp3)
- Confirm it was published to the personal feed and will appear in their podcast app automatically. Published episodes are public — anyone with the feed link can listen. Include the new feed_url in copy-paste code format on the first run under the new name.
- Labeled links to the day's workshop.md and handout.md, plus one line naming the snips file path.
- Labeled link to the day's transcript:
[Transcript: Soft Fork - <Month D, YYYY>](sandbox://workspace/podcasts/<slug>/transcript.txt)
- Sources: a list of ALL of the day's sources, each one as a linked name only, using the snip's episode/article title as the link text and the snip's Link URL as the target. No summaries, no dates, no extra description for the sources list. Rule set by Rachael on 2026-10-17: include links for all sources, but just the name.

## 6. Slack channel mirror (replaces the Mac copy)
Rachael's Mac sleeps, so deliverables no longer copy there. Instead, mirror the episode to the #podcast channel in the La Maison Santa Barbara Slack workspace (channel ID [Slack channel ID removed]). Do not post to any other channel.

Upload the day's transcript.txt, workshop.md, and handout.md with `/opt/hatch/bin/remote-storage upload-file --path <file>` and keep the returned public URLs (note their expiry dates).

Post one message to the channel (keep it tight):
- Episode title as the header.
- 3–4 sentence plain-English summary of the day's top items.
- The public episode link: the episode_url from the publish output (an https://muse.ai URL — this works in Slack, unlike sandbox:// links).
- Labeled links: full transcript, workshop, handout (the remote-storage URLs, with a note on when they expire).
- One line: published to the Soft Fork feed, in Apple Podcasts automatically.
- Sources: a list of ALL of the day's sources, each one as a linked name only, using the snip's episode/article title as the link text and the snip's Link URL as the target. No summaries, no dates, no extra description for the sources list.

Then post the video highlight as a second message:
- Pick the most interesting TEACHING moment from the episode (the FOMO angle: what the listener is missing out on if they don't know this), not just the flashiest news.
- Build a short vertical video (1080x1350): the visual must depict the thing itself (render the concept — e.g. the actual Authority Card), never the generic giraffe background. Pattern: ~/workspace/ig-plugins/build_authority_card_reel.py (PIL scene rendering + ffmpeg assembly). Music: a real, recognizable public-domain classical piece from ~/workspace/ig-plugins/ (a different one per video), never synth pads or generic stock music.
- Upload the mp4 with remote-storage upload-file and post the public link with a one-line hook.

Note: Slack canvases are NOT supported on this workspace's free plan (slack_create_canvas returns not_supported_free_team) — do not attempt them; the remote-storage transcript link is the transcript delivery.

If the Slack post, the video, or any upload fails, record it as a failed check for Section 7 — do not skip quietly.

Observations from the run go to the daily memory log at ~/memory/YYYY-MM-DD.md, not MEMORY.md.

## 7. Fail loud — never fail silently
Rachael's standing rule: if the routine does not fully post, she must be told. A quiet skip is a bug. This section runs after Sections 1–6 on every run.

Verification checklist (all paths dated today, America/Los_Angeles):
- [ ] Podcast MP3 exists at ~/workspace/podcasts/<slug>/<slug>.mp3 and is a complete file, not a stub or partial render.
- [ ] The script follows the reaction rules: written laughs only, no bracket cues, build up before any shared laugh, a groan for the corniest joke, 2 to 4 shared crack-ups written into the lines.
- [ ] The episode published to the personal feed: `podcast-helper publish` did NOT return "blocked": true, and the manifest shows today's episode as published to the "Soft Fork" feed.
- [ ] ~/workspace/ai-daily-brief/workshops/<YYYY-MM-DD>-<slug>/workshop.md and handout.md both exist.
- [ ] ~/workspace/ai-daily-brief/sources/snips/<YYYY-MM-DD>-ai-tools-trending.md exists.
- [ ] transcript.txt exists at ~/workspace/podcasts/<slug>/transcript.txt.
- [ ] Slack #podcast post succeeded with episode, transcript, workshop, and handout links, or record the exact failure.
- [ ] Video highlight built and posted to #podcast, or record the exact failure.
- [ ] Chat delivery and Slack #podcast post both include the full sources list, linked names only, for every snip.

A published episode counts as published. There is no performed version to check for, and no byte size comparison is part of this checklist (Rachael's rule, 2026-10-31).

If EVERY check passes: deliver the normal Section 5 chat message.

If ANY check fails:
1. Send an email via the gmail skill (+send) from Rachael's personal Gmail to [personal email removed]. Subject: `Soft Fork FAILED — <Month D, YYYY>: <one-line cause>`. Body, in her voice (plain English, short sentences, no em-dashes): what was supposed to happen, exactly which step failed and the error or evidence, which deliverables DID complete, and what she can do about it (e.g., ask for a retry, reconnect something). Keep it short.
2. Start the Section 5 chat delivery with this exact first line: `LOUD: today's Soft Fork did not fully publish — <one-line cause>.` Then give the normal summary of whatever did complete.
3. Do not retry a blocked publish or invent a workaround publish path. The duplicate check in Section 0 already prevents double episodes, so a later retry she requests is safe.

---

# Job 2: ai-tools-daily-watchdog (the missed-run check)

# Soft Fork watchdog — fail-loud missed-run check

Every morning, verify that today's Soft Fork edition actually published. This catches silent failures the main job cannot report itself: the scheduled run never fired, the worker crashed, or the publish step never completed.

## Check
1. Determine today's date in America/Los_Angeles. The expected episode title is "Soft Fork - <Month D, YYYY>" (for example, "Soft Fork - October 5, 2026").
2. Run `podcast-helper manifest read`. Check whether an episode with today's title exists AND is published to the "Soft Fork" feed (the manifest/feed shows it as published with a non-empty feed_url).
3. If today's edition is present and published: stay silent. End with no user-facing message, no email, nothing.

## Alert (only when today's edition is missing or unpublished)
This is a FAILURE. Alert loudly through both channels:
1. Send an email via the gmail skill (+send) from Rachael's personal Gmail to [personal email removed]. Subject: `Soft Fork MISSED — <Month D, YYYY>: no episode published`. Body, in her voice (plain English, short sentences, no em-dashes): what you checked, what you found (for example, no run record today, or an episode exists but is not published to the feed), and that she can ask for a catch-up run any time. Keep it short.
2. Deliver a chat message to the main chat starting with this exact first line: `LOUD: today's Soft Fork did not publish.` Then one or two sentences on what you found.

Never attempt to rebuild, regenerate, or publish the episode yourself. Alerting is this job's only work. Do not send any alert when the check passes.

---

# Job 3: ai-tools-daily-instagram (DISABLED, does not run)

# Soft Fork — Instagram reel with loud failure alerts

Every morning, post today's Soft Fork episode to Instagram (@agentic_ai_sb) as a REEL with piano music and headlines on the image, tagging @the_rachael_review. Rachael's standing rule for this job: NEVER fail silently. If the post does not go live for any reason, notify her LOUDLY via email AND Instagram DM.

## Steps

1. Run `podcast-helper manifest read`. Take the most recent episode (episodes[0]). Read its slug, title, description, and topics.

2. Idempotency check: run `instagram-cli posts --account-id [Instagram account ID removed] --limit 5`. If any returned post caption contains today's episode title or today's date, the episode is already posted. Report "already posted" and stop. Never post duplicates.

3. Build the reel from today's episode:
```
python3 ~/workspace/ig-plugins/build_podcast_reel.py <slug> "<date like October 4, 2026>" "<headline1>" "<headline2>" ...
```
Headlines: up to 4, short plain English, each a fact from the episode. Use ONLY the episode's description and topics fields. Never invent topics or facts. If topics are empty, derive headlines from the description alone. If the build fails, go to FAILURE.

4. Verify both output files exist: `~/workspace/ig-plugins/<slug>-reel-piano.mp4` (the reel) and `~/workspace/ig-plugins/<slug>-reel-cover.png` (the cover). If either is missing, go to FAILURE.

5. Write the caption in Rachael's voice: plain English, warm but direct, short sentences, concrete nouns, no corporate filler, NEVER use em-dashes. Shape: a scene-first hook line, 2-4 short rhythmic lines on what the episode covers (use only the description and topics fields, never invent topics), one line on the format (45 minutes, Maya and Theo, Hard Fork style), and a question as the comment CTA. End with at most 3 hashtags (#AItools #podcast). The show is called "Soft Fork" (renamed from AI Tools Daily on 2026-10-06) — the caption should say Soft Fork, not AI Tools Daily. Keep it under 300 words.

6. Post the reel. QUOTING SAFETY (added 2026-10-08 after a live caption got truncated mid-word): never pass the caption inside single quotes in a shell command. An apostrophe in the caption (e.g. "Grok Bot's") ends the single-quoting and silently truncates the caption. Instead: write the caption to /tmp/soft-fork-caption.txt first, then post with the caption read from the file inside double quotes:
```
instagram-cli post-feed --account-id [Instagram account ID removed] --file <reel-mp4-path> --cover <reel-cover-png-path> --caption "$(cat /tmp/soft-fork-caption.txt)" --mentions '[{"user_fbid":"[Instagram user ID removed]"}]'
```
Avoid double quotes, backticks, and $ in the caption text itself. After posting, verify the live caption is complete by reading the post back and comparing it to the file. If the caption is truncated, do NOT repost (that would duplicate) — fix the caption in the Instagram app manually and note it in the run report.
Do NOT use --retries (a retry could publish a duplicate).

7. On success (a media_fbid is returned): report "Posted" with the episode title. Done.

## FAILURE PROTOCOL - mandatory, never skip, never fail silently

If ANY step fails - no episode in the manifest, build failure, missing output files, post command error, approval card timeout/expired, rate limit - do ALL of the following:

a. EMAIL (gmail skill): send to [personal email removed]. Subject: "Instagram post FAILED: Soft Fork <today's date>". Body: what was attempted, the exact error, the reel and cover paths, the caption that was ready, and what Rachael needs to do (post manually in the Instagram app, or watch for the approval card on the next run).

b. INSTAGRAM DM (instagram-messages-cli): `instagram-messages-cli send --account-id [Instagram account ID removed] --recipient-user-fbids [Instagram user ID removed] --text "<short failure summary: which episode, what failed, the error, what to do>"`. Rachael explicitly authorized IG DM failure alerts on 2026-10-04 ("message me on IG, anything!").

c. The final run message must state LOUDLY that the post failed, what failed, and which notifications were confirmed sent. A quiet one-line note is not acceptable.

If the email or DM themselves fail, say so explicitly in the final message. Never claim a notification went out when it did not.

Observations from the run go to the daily log at ~/memory/YYYY-MM-DD.md, not MEMORY.md.
