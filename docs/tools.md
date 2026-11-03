# Soft Fork tools

Muse pulled this reference from each tool's own help text on November 3, 2026. Both tools run inside Muse.

## podcast-helper

`podcast-helper` makes the episode audio, keeps the episode catalog and publishes episodes to the feed. The catalog is called the manifest.

- **Location:** `/opt/muse/skills/generate_podcast/scripts/podcast-helper`
- **Type:** a Python script of 2,318 lines in Muse's `generate_podcast` skill.
- **Helper file:** `podcast_telemetry.py` sits in the same folder. It records the timing and outcome of each `generate` attempt without recording any content. A copy is in [tools/podcast_telemetry.py](../tools/podcast_telemetry.py).

### Commands

- `generate`: makes an episode from start to finish.
- `manifest`: works with the catalog through `read`, `add-episode`, and `update-episode`.
- `publish`: publishes an episode to the feed.
- `migrate-feed`: moves a show to a new feed and starts it with the latest episode. The old feed becomes a read-only archive.
- `save-to-spotify`: saves an episode to the user's personal Spotify show.
- `update-cover`: replaces an episode's cover with new art.
- `generate-slug`: makes a short web-safe name from a title.

### Commands Soft Fork uses every day

- `podcast-helper manifest read` reads the catalog. The main job uses it as the duplicate check. The watchdog uses it to confirm the episode was published.
- `podcast-helper generate --script <script> --title "Soft Fork - <Month D, YYYY>" --description "<one sentence>" --speaker Maya=avocado_v2:MAI_01 --speaker Theo=avocado_v2:MAI_03 --series-id soft-fork-v1 --cover-prompt "<the exact cover prompt in the job>" --topics-file <topics>`
- `podcast-helper publish --slug <slug> --feed-title "Soft Fork"`

### Options for generate

- `--speaker Name=voice_id` matches each speaker to a voice. It is required once for each speaker.
- `--series-id` makes every episode in a series reuse the same cover.
- `--cover-prompt` describes the cover art to generate. Soft Fork passes its giraffe cover prompt word for word.
- `--topics-file` points to a short summary of the episode's topics. The summary is saved with the episode so later runs can avoid repeats.
- `--cover-image` is marked unavailable in the tool. An episode published with a supplied cover image fails.
- `--language` sets the language for the voices. It defaults to the current request's language.

## remote-storage

`remote-storage` uploads a workspace file to Muse's storage and returns a public link that expires. Soft Fork uses it to give Slack working links to the transcript, workshop, handout, and video highlight.

- **Location:** `/opt/hatch/bin/remote-storage`
- **Type:** a compiled Linux program of about 21 MB. It has no readable source, so this page and its help text are the only documentation. It can't run a feed outside Muse because the storage and the feed live on Muse's side.

### Commands

- `upload-file`: publishes a workspace file and prints a link that expires.
- `delete-file`: takes down an uploaded file before its link expires.
- `publish-episode`: uploads episode audio, updates the feed manifest, and rebuilds the RSS feed.
- `unpublish-episode`: removes an episode from a feed and rebuilds the RSS feed.
- `migrate-feed`: moves a show off its old feed in two calls, `--prepare` and then `--retire-into`.
- `restore-feed`: undoes a `migrate-feed` so the old feed accepts episodes again.

### Command Soft Fork uses every day

`/opt/hatch/bin/remote-storage upload-file --path <file>` uploads one file. The file must be inside the workspace.

- `--ttl-hours` sets how long the link works. It accepts 1 to 48 hours and defaults to 48.
- `--content-type` sets the file type. It is normally taken from the file extension.
