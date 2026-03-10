<div class="inner-narrow" style="padding: 4rem 0;">

  <h1 style="text-align: center; margin-bottom: 1rem;">How I built a custom Claude AI skill for content design</h1>
  <p style="text-align: center; color: var(--text-secondary); margin-bottom: 3rem; font-size: 1.25rem;"><em>Content design is often misunderstood or under-resourced. Here is how I trained an AI partner to help.</em></p>

  <img src="/assets/images/project_ai_skill.png" alt="AI Skill Hero Image" style="width: 100%; height: auto; border-radius: 8px; margin-bottom: 3rem; box-shadow: 0 4px 12px rgba(0,0,0,0.1);" />

  ## The Problem: Generic AI output

  Standard LLMs like ChatGPT or Claude can help with writing, but they often lack the specific technical context and business rules of a project. Generic AI outputs miss the nuance of technical architecture, leading to hallucinations or "AI-sounding" filler that doesn't align with our design systems.

  <div style="display: flex; justify-content: center; margin: 3rem 0;">
    <img src="/assets/images/comic_generic_prompts.png" alt="Generic prompts need retooling each time." style="max-width: 100%; border-radius: 4px; box-shadow: 0 2px 8px rgba(0,0,0,0.05);" />
  </div>
  <p style="text-align: center; font-size: 0.9rem; color: var(--text-secondary); margin-top: -2rem; margin-bottom: 3rem;"><em>Generic prompts need retooling each time.</em></p>

  ## Content Is King? My Kingdom for Context!

  Content is disconnected without context. I needed a way to provide AI with the right background without having to re-prompt it every single time I started a new task.

  <div style="display: flex; justify-content: center; margin: 3rem 0;">
    <img src="/assets/images/comic_content_context.png" alt="Content is disconnected without context." style="max-width: 100%; border-radius: 4px; box-shadow: 0 2px 8px rgba(0,0,0,0.05);" />
  </div>

  ## The Solution & Setup

  I built a custom Claude "Project" (skill) that acts as a dedicated content design partner. It is pre-loaded with specific knowledge to guide its responses. 

  Gathering context is everything. Once provided, the skill does the rest. I uploaded the following core documents to ground the AI:
  *   **Technical Debt considerations**
  *   **Voice & Tone Style Guide**
  *   **Information Architecture overview**

  <div style="display: flex; justify-content: center; margin: 3rem 0;">
    <img src="/assets/images/workflow_diagram.png" alt="Gathering context workflow" style="max-width: 100%; border-radius: 4px; box-shadow: 0 2px 8px rgba(0,0,0,0.05);" />
  </div>
  <p style="text-align: center; font-size: 0.9rem; color: var(--text-secondary); margin-top: -2rem; margin-bottom: 3rem;"><em>Gathering context is everything. Once provided, the skill does the rest.</em></p>

  ## The Results

  The custom skill drastically altered how I worked. It reduced my baseline editing time by **60%** and significantly improved accuracy for technical terms compared to standard zero-shot prompting.

  Surprises often reveal better ways to do things. The AI began catching structural inconsistencies before I even began drafting the final copy.

  <div style="display: flex; justify-content: center; margin: 3rem 0;">
    <img src="/assets/images/comic_ai_unexpected.png" alt="Surprises often reveal better ways to do things." style="max-width: 100%; border-radius: 4px; box-shadow: 0 2px 8px rgba(0,0,0,0.05);" />
  </div>

  ## Learnings

  1.  **Memory matters:** Claude’s ability to recall specific guidelines from the uploaded knowledge base is impressive.
  2.  **Guardrails are necessary:** Strict negative prompts are required to avoid "Corporate AI" fluff words (like "delve" or "robust").
  3.  **Structure over words:** Providing the AI with structural frameworks (like markdown templates) yields far better results than just asking it to "write."

</div>
