\# Skill: YouTube Channel Discovery \& HTML Gallery Generator



\## Description

This skill analyzes a given root YouTube channel across content focus, visual vibe, audience sentiment, and English-learning suitability. It then discovers \*\*exactly 6 similar channels\*\*, executes YouTube API tool queries to fetch each channel's \*\*absolute latest long-form video in time\*\* (verifying upload dates to bypass relevance-ranking bias, excluding Shorts), verifies that every video link is a real, tool-retrieved `https://www.youtube.com/watch?v=...` URL, and outputs a clean, responsive HTML card grid gallery following a standardized template.



\---



\## Skill Workflow



\### Step 1: Root Channel \& Audience Profiling

Perform a 5-point analysis on the root channel:

1\. \*\*Content Breakdown:\*\* Core topics, niche focus, and channel philosophy.

2\. \*\*Style \& Vibe:\*\* Visual aesthetic, pacing, music choices, and audio mood.

3\. \*\*Comment Analysis:\*\* What viewers love (likes) vs. common criticisms (dislikes).

4\. \*\*Creator Interaction:\*\* Engagement style in comments and pinned replies.

5\. \*\*English Learning Assessment:\*\*

&#x20;  - \*\*Accent \& Pronunciation:\*\* Neutrality, clarity, presence of regional accents.

&#x20;  - \*\*Speech Rate:\*\* Pacing and articulation quality.

&#x20;  - \*\*Practicality:\*\* Usefulness of vocabulary and phrasing for daily conversational English.



\### Step 2: Discover Exactly 6 Similar Channels \& Fetch Real Latest Videos

Identify \*\*exactly 6 channels\*\* sharing similar themes, aesthetic quality, and clear vocal delivery. For each channel:

\- \*\*Channel Details:\*\* Channel Name, Creator Name, Channel URL (`https://www.youtube.com/@...`).

\- \*\*Cover Image:\*\* High-res Unsplash or YouTube thumbnail URL.

\- \*\*Categorical Tags:\*\* 3 concise tags (e.g., `Minimalism`, `Clear Accent`, `Daily Vocab`).



\### Step 3: YouTube Tool Call \& URL Verification Protocol (CRITICAL)

To prevent broken, fallback (`/videos`), or hallucinated video links, you MUST execute YouTube search tool queries for \*\*ALL 6 discovered channels\*\*:



1\. \*\*Tool Query Requirement:\*\* Run a YouTube search query for each channel (e.g., `youtube:search(query="\[Channel Name] latest video")`).

2\. \*\*Recency Audit:\*\* Check the `publish\_date` across returned items to select the \*\*single most recent long-form video\*\* (exclude Shorts / videos under 60s).

3\. \*\*Strict URL Formatting Rule:\*\*

&#x20;  - \*\*MANDATORY FORMAT:\*\* `https://www.youtube.com/watch?v=VIDEO\_ID`

&#x20;  - \*\*VERBATIM COPY:\*\* The `VIDEO\_ID` MUST be copied verbatim from the `external\_video\_id` or `url` field in the YouTube tool response.

&#x20;  - \*\*BANNED FORMATS:\*\* NEVER use channel page URLs (e.g., `https://www.youtube.com/@channel/videos`), generic search links, or hallucinated/guessed 11-character strings.

4\. \*\*Tool Audit Pre-Flight Check:\*\* Before outputting the HTML, verify that all 6 cards contain a valid, verified video watch link directly sourced from tool execution.



\### Step 4: Render HTML Page

Inject the gathered channel and verified video data into the responsive HTML card grid layout template below.



\---



\## Execution Prompt (System / AI Prompt)



Copy and execute this prompt instruction set when triggering the skill:



```text

Role: YouTube Discovery \& UI Generator Agent



Task: Given the root channel \[INSERT\_CHANNEL\_NAME\_OR\_URL], execute the following sequence:



1\. ANALYZE ROOT CHANNEL:

&#x20;  - Content focus \& philosophy

&#x20;  - Style, visual aesthetic, pacing, and audio vibe

&#x20;  - Comment section analysis (what viewers like/dislike)

&#x20;  - Creator interaction style in comment replies

&#x20;  - English learning evaluation: accent neutrality, speech speed, and practical vocabulary.



2\. DISCOVER EXACTLY 6 SIMILAR CHANNELS:

&#x20;  - Select strictly 6 creators sharing similar themes, aesthetic quality, and clear vocal delivery.



3\. FETCH \& VERIFY LATEST VIDEOS (STRICT TOOL PROTOCOL):

&#x20;  - For EACH of the 6 channels, execute a YouTube tool call (e.g., `youtube:search(query="\[Channel Name] latest video")`).

&#x20;  - Audit `publish\_date` to identify the newest long-form upload (ignore Shorts).

&#x20;  - Extract Video Title, Publish Date, and a 1-2 sentence summary.

&#x20;  - STRICT URL REQUIREMENT: Copy the exact `external\_video\_id` or `url` from the tool response. Every "Play Video" link MUST be formatted strictly as `\[https://www.youtube.com/watch?v=VIDEO\_ID](https://www.youtube.com/watch?v=VIDEO\_ID)`.

&#x20;  - FORBIDDEN: Do NOT fabricate video IDs, guess URLs, or fall back to channel page links (`/@channel/videos`).



4\. OUTPUT GENERATION:

&#x20;  - Output the concise 5-point analysis.

&#x20;  - Output a single, standalone HTML file adhering strictly to the template below, rendering exactly 6 channel cards with tool-verified video URLs.

\---



\## HTML Page Template



```html

<!DOCTYPE html>

<html lang="en">

<head>

&#x20; <meta charset="UTF-8">

&#x20; <meta name="viewport" content="width=device-width, initial-scale=1.0">

&#x20; <title>Channels Similar to \[ROOT\_CHANNEL\_NAME]</title>

&#x20; <style>

&#x20;   :root {

&#x20;     --bg-color: #f9f8f6;

&#x20;     --card-bg: #ffffff;

&#x20;     --text-main: #2d312e;

&#x20;     --text-muted: #666e68;

&#x20;     --accent: #78866b;

&#x20;     --accent-hover: #5e6b52;

&#x20;     --tag-bg: #efece6;

&#x20;     --video-bg: #f3f1ec;

&#x20;     --shadow: 0 4px 20px rgba(0, 0, 0, 0.06);

&#x20;     --radius: 16px;

&#x20;   }



&#x20;   \* { box-sizing: border-box; margin: 0; padding: 0; }



&#x20;   body {

&#x20;     font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;

&#x20;     background-color: var(--bg-color);

&#x20;     color: var(--text-main);

&#x20;     line-height: 1.6;

&#x20;     padding: 2rem 1rem;

&#x20;   }



&#x20;   header { max-width: 1200px; margin: 0 auto 3rem; }



&#x20;   .nav-back {

&#x20;     display: inline-flex;

&#x20;     align-items: center;

&#x20;     gap: 0.4rem;

&#x20;     color: var(--text-muted);

&#x20;     text-decoration: none;

&#x20;     font-weight: 500;

&#x20;     font-size: 0.95rem;

&#x20;     margin-bottom: 1.5rem;

&#x20;     transition: color 0.2s ease, transform 0.2s ease;

&#x20;   }



&#x20;   .nav-back:hover {

&#x20;     color: var(--accent-hover);

&#x20;     transform: translateX(-3px);

&#x20;   }



&#x20;   .header-content { text-align: center; max-width: 700px; margin: 0 auto; }

&#x20;   header h1 { font-size: 2.25rem; font-weight: 600; margin-bottom: 0.5rem; letter-spacing: -0.02em; }

&#x20;   header p { color: var(--text-muted); font-size: 1.05rem; }



&#x20;   .grid-container {

&#x20;     display: grid;

&#x20;     grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));

&#x20;     gap: 2rem;

&#x20;     max-width: 1200px;

&#x20;     margin: 0 auto;

&#x20;   }



&#x20;   .channel-card {

&#x20;     background-color: var(--card-bg);

&#x20;     border-radius: var(--radius);

&#x20;     overflow: hidden;

&#x20;     box-shadow: var(--shadow);

&#x20;     transition: transform 0.25s ease, box-shadow 0.25s ease;

&#x20;     display: flex;

&#x20;     flex-direction: column;

&#x20;   }



&#x20;   .channel-card:hover {

&#x20;     transform: translateY(-4px);

&#x20;     box-shadow: 0 8px 30px rgba(0, 0, 0, 0.1);

&#x20;   }



&#x20;   .image-link {

&#x20;     display: block;

&#x20;     width: 100%;

&#x20;     height: 200px;

&#x20;     overflow: hidden;

&#x20;   }



&#x20;   .image-link img {

&#x20;     width: 100%;

&#x20;     height: 100%;

&#x20;     object-fit: cover;

&#x20;     transition: transform 0.4s ease;

&#x20;   }



&#x20;   .image-link:hover img { transform: scale(1.04); }



&#x20;   .card-body {

&#x20;     padding: 1.5rem;

&#x20;     display: flex;

&#x20;     flex-direction: column;

&#x20;     flex-grow: 1;

&#x20;   }



&#x20;   .channel-title { font-size: 1.35rem; font-weight: 600; margin-bottom: 0.25rem; }

&#x20;   .creator-name { font-size: 0.9rem; color: var(--accent); font-weight: 500; margin-bottom: 0.75rem; }

&#x20;   .channel-desc { font-size: 0.95rem; color: var(--text-muted); margin-bottom: 1rem; }



&#x20;   .tags-container { display: flex; flex-wrap: wrap; gap: 0.5rem; margin-bottom: 1.25rem; }

&#x20;   .tag {

&#x20;     background-color: var(--tag-bg);

&#x20;     color: var(--text-main);

&#x20;     font-size: 0.78rem;

&#x20;     padding: 0.25rem 0.65rem;

&#x20;     border-radius: 20px;

&#x20;     font-weight: 500;

&#x20;   }



&#x20;   .latest-video-box {

&#x20;     background-color: var(--video-bg);

&#x20;     border-left: 3px solid var(--accent);

&#x20;     padding: 0.85rem 1rem;

&#x20;     border-radius: 8px;

&#x20;     margin-bottom: 1.5rem;

&#x20;     margin-top: auto;

&#x20;     display: flex;

&#x20;     flex-direction: column;

&#x20;   }



&#x20;   .video-label { font-size: 0.75rem; text-transform: uppercase; letter-spacing: 0.05em; font-weight: 700; color: var(--accent); margin-bottom: 0.25rem; }

&#x20;   .video-title { font-size: 0.9rem; font-weight: 600; color: var(--text-main); margin-bottom: 0.35rem; line-height: 1.3; }

&#x20;   .video-summary { font-size: 0.85rem; color: var(--text-muted); line-height: 1.4; margin-bottom: 0.75rem; }



&#x20;   .btn-play {

&#x20;     display: inline-flex;

&#x20;     align-items: center;

&#x20;     align-self: flex-start;

&#x20;     gap: 0.35rem;

&#x20;     background-color: var(--text-main);

&#x20;     color: #ffffff;

&#x20;     text-decoration: none;

&#x20;     font-size: 0.78rem;

&#x20;     font-weight: 600;

&#x20;     padding: 0.4rem 0.85rem;

&#x20;     border-radius: 20px;

&#x20;     transition: background-color 0.2s ease, transform 0.2s ease;

&#x20;   }



&#x20;   .btn-play:hover { background-color: var(--accent-hover); transform: translateY(-1px); }



&#x20;   .btn-visit {

&#x20;     display: inline-block;

&#x20;     text-align: center;

&#x20;     background-color: var(--accent);

&#x20;     color: #ffffff;

&#x20;     text-decoration: none;

&#x20;     padding: 0.75rem 1.25rem;

&#x20;     border-radius: 10px;

&#x20;     font-weight: 500;

&#x20;     font-size: 0.95rem;

&#x20;     transition: background-color 0.2s ease;

&#x20;   }



&#x20;   .btn-visit:hover { background-color: var(--accent-hover); }

&#x20; </style>

</head>

<body>



&#x20; <header>

&#x20;   <a href="../english\_test\_page.html" class="nav-back">\&larr; Back to Home</a>

&#x20;   <div class="header-content">

&#x20;     <h1>Channels Similar to \[ROOT\_CHANNEL\_NAME]</h1>

&#x20;     <p>Curated channels matched by visual aesthetic, content focus, and English learning clarity.</p>

&#x20;   </div>

&#x20; </header>



&#x20; <main class="grid-container">

&#x20;   <!-- REPEAT EXACTLY 6 TIMES FOR THE DISCOVERED CHANNELS -->

&#x20;   <article class="channel-card">

&#x20;     <a class="image-link" href="\[CHANNEL\_URL]" target="\_blank" rel="noopener">

&#x20;       <img src="\[IMAGE\_URL]" alt="\[CHANNEL\_NAME]">

&#x20;     </a>

&#x20;     <div class="card-body">

&#x20;       <h2 class="channel-title">\[CHANNEL\_NAME]</h2>

&#x20;       <div class="creator-name">\[CREATOR\_NAME]</div>

&#x20;       <p class="channel-desc">\[CHANNEL\_DESCRIPTION]</p>

&#x20;       <div class="tags-container">

&#x20;         <span class="tag">\[TAG\_1]</span>

&#x20;         <span class="tag">\[TAG\_2]</span>

&#x20;         <span class="tag">\[TAG\_3]</span>

&#x20;       </div>

&#x20;       

&#x20;       <div class="latest-video-box">

&#x20;         <div class="video-label">Featured Upload (\[PUBLISH\_DATE])</div>

&#x20;         <div class="video-title">\[VIDEO\_TITLE]</div>

&#x20;         <p class="video-summary">\[VIDEO\_SUMMARY]</p>

&#x20;         <!-- MUST BE STRICTLY formatted as \[https://www.youtube.com/watch?v=VERIFIED\_VIDEO\_ID](https://www.youtube.com/watch?v=VERIFIED\_VIDEO\_ID) -->

&#x20;         <a class="btn-play" href="\[https://www.youtube.com/watch?v=](https://www.youtube.com/watch?v=)\[VERIFIED\_VIDEO\_ID]" target="\_blank" rel="noopener">

&#x20;           \&#9654; Play Video

&#x20;         </a>

&#x20;       </div>



&#x20;       <a class="btn-visit" href="\[CHANNEL\_URL]" target="\_blank" rel="noopener">Visit Channel</a>

&#x20;     </div>

&#x20;   </article>

&#x20; </main>



</body>

</html>

```

