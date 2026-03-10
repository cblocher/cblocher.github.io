<div class="inner-narrow" style="padding: 4rem 0;">

  <h1 style="text-align: center; margin-bottom: 1rem;">Gamifying a style guide: Headline Hero</h1>
  <p style="text-align: center; color: var(--text-secondary); margin-bottom: 3rem; font-size: 1.25rem;"><em>Content style guides are often boring and ignored. I wanted to turn ours into an interactive game using Gemini.</em></p>

  <img src="/assets/images/onboarding_hero_mockup_top.png" alt="Headline Hero Laptop Mockup" style="width: 100%; height: auto; border-radius: 8px; margin-bottom: 3rem; box-shadow: 0 4px 12px rgba(0,0,0,0.1);" />

  ## The Idea: "Vibe Coding"

  Reading and memorizing content guidelines can be a tedious task. To make it more engaging, I utilized an 8-page PDF outlining guidelines for headings and URLs. My goal was to completely "vibe code" an interactive game without writing a single line of code myself.

  <div style="display: flex; justify-content: center; margin: 3rem 0;">
    <img src="/assets/images/onboarding_guidelines_pdf_icon.png" alt="PDF Source Material" style="max-width: 100%; border-radius: 4px; box-shadow: 0 2px 8px rgba(0,0,0,0.05);" />
  </div>

  ## The Build

  I provided the source PDF to Google Gemini and prompted it to generate the HTML, CSS, and JS necessary for an 8-bit, "Space Invaders" style game. The objective? Shoot down "Passive Voice" and "Jargon."

  <div style="display: flex; justify-content: center; margin: 3rem 0;">
    <img src="/assets/images/gemini_prompt_interface.png" alt="Prompting Gemini Canvas" style="max-width: 100%; border-radius: 4px; box-shadow: 0 2px 8px rgba(0,0,0,0.05);" />
  </div>

  Gemini Canvas rapidly generated the functional frontend code, iterating completely through conversational prompting.

  <div style="display: flex; justify-content: center; margin: 3rem 0;">
    <img src="/assets/images/onboarding_html_code_vscode.png" alt="Final HTML Code" style="max-width: 100%; border-radius: 4px; box-shadow: 0 2px 8px rgba(0,0,0,0.05);" />
  </div>

  ## Deliver & Learnings

  I shared the preview link with the team, and finalized hosting it directly on GitHub Pages. The "Headline Hero" game received positive feedback from testers, proving that you don't need to be a software developer to create functional, engaging internal tools.

  **Next Steps:** Planning "Documentation Quest," a sequel featuring a "boss level."

  <div style="display: flex; justify-content: center; margin: 2rem 0 4rem 0;">
    <iframe style="width: 100%; height: 500px; max-width: 800px; border-radius: 8px; border: 1px solid #E5E7EB; box-shadow: 0 4px 12px rgba(0,0,0,0.1);" src="https://gemini.google.com/share/4876b92999ed" allowfullscreen>
      Your browser does not support iframes.
    </iframe>
  </div>

</div>
