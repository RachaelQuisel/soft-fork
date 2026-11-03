# Soft Fork workflow

This follows Muse's saved prompts in [prompts/muse-soft-fork-prompts.md](../prompts/muse-soft-fork-prompts.md).

```mermaid
flowchart TD
    A[ai-tools-daily<br/>Muse cloud job, daily about 7:43 AM PT] --> B{Today's episode already<br/>in the podcast manifest?}
    B -- Yes --> Z[Post a one-line note and stop]
    B -- No --> C[Start from yesterday's snips file<br/>research only what is new]
    C --> D[Search with browser.search news vertical<br/>open real pages and videos<br/>prefer the last 7 days]
    D --> E[Must-check sources<br/>How I AI, Lenny's, Built on Air,<br/>demo videos on YouTube, X, and TikTok]
    E --> F[Save 10 to 14 verified snips<br/>plus one Workshop pick]
    F --> G[Read recent episode topics<br/>steer toward fresh material]
    G --> H[Write a 45-minute script<br/>Maya and Theo: cold open, 2 deep dives,<br/>roundup and close]
    H --> I[podcast-helper generate<br/>fixed voices, giraffe cover, soft-fork-v1]
    I --> J[podcast-helper publish to the Soft Fork feed on muse.ai]
    J --> K[Save transcript.txt]
    F --> L[60-minute workshop<br/>workshop.md and handout.md]
    K --> M[Deliver to Muse's main chat]
    L --> M
    M --> N[Post episode, transcript, workshop<br/>and handout links to Slack #podcast]
    N --> O[Build and post a teaching-moment video highlight]
    O --> P{All checks pass?}
    P -- Yes --> Q[Normal delivery]
    P -- No --> R[Email Rachael and start the chat<br/>message with LOUD]
    S[ai-tools-daily-watchdog<br/>daily about 10:43 AM PT] --> T{Today's episode published?}
    T -- Yes --> U[Stay silent]
    T -- No --> R
```

A third job, ai-tools-daily-instagram, is saved but has been disabled since October 15, 2026, so it is left out of the chart.
