# Soft Fork workflow

This chart follows Muse's prompts in [prompts/muse-soft-fork-prompts.md](../prompts/muse-soft-fork-prompts.md). [tools.md](tools.md) explains each command.

```mermaid
flowchart TD
    A[ai-tools-daily<br/>Muse cloud job at about 7:43 AM PT] --> B{podcast-helper manifest read<br/>Is today's episode in the catalog?}
    B -- Yes --> Z[Post a one-line note and stop]
    B -- No --> C[Open yesterday's snips file<br/>Research only new or changed items]
    C --> D[Search news results and open real pages and videos<br/>Prefer the last 7 days]
    D --> E[Check How I AI, Lenny's, Built on Air,<br/>and demo videos on YouTube, X, and TikTok]
    E --> F[Save 10 to 14 verified snips and a workshop pick]
    F --> G[podcast-helper manifest read<br/>Check recent topics to avoid repeats]
    G --> H[Write a 45-minute script for Maya and Theo]
    H --> I[podcast-helper generate<br/>voices, soft-fork-v1 cover, and topics file]
    I --> J[podcast-helper publish --feed-title Soft Fork]
    J --> K[Copy the script to transcript.txt]
    F --> L[Write workshop.md and handout.md]
    K --> M[Deliver the summary and links to Muse's main chat]
    L --> M
    M --> N[remote-storage upload-file<br/>transcript, workshop, and handout]
    N --> O[Post episode and links to Slack #podcast]
    O --> P[Build the video highlight<br/>remote-storage upload-file and post to #podcast]
    P --> Q{Do all checks pass?}
    Q -- Yes --> R[Normal delivery]
    Q -- No --> S[Email Rachael<br/>Start the chat message with LOUD]
    T[ai-tools-daily-watchdog<br/>at about 10:43 AM PT] --> U{podcast-helper manifest read<br/>Is today's episode published?}
    U -- Yes --> V[Stay silent]
    U -- No --> S
```

The saved Instagram job has been turned off since October 15, 2026, so the chart leaves it out.
