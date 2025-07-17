# The Anatomy of an Amp Workflow

<style>
.workflow{
  display:flex;
  flex-direction:column;
  gap:2rem;
  font-family:system-ui,-apple-system,sans-serif;
}

.row{
  display:grid;
  grid-template-columns: 1fr 220px;
  align-items:stretch;
  min-height:120px;
}

.body{padding-right:2rem;}

.label{
  display:flex;
  align-items:center;
  gap:1rem;
  font-size:1.3rem;
  font-weight:500;
  color:#fff;
}

.label .bar{
  flex:0 0 4px;
  height:100%;
  border-radius:2px;
}

.label.problem  .bar{background:#F34E3F;}
.label.plan     .bar{background:#F34E3F;}
.label.debug    .bar{background:#F34E3F;}
.label.test     .bar{background:#F34E3F;}
.label.verify   .bar{background:#F34E3F;}
.label.code     .bar{background:#F34E3F;}
.label.iterate  .bar{background:#F34E3F;}
</style>

<div style="background: #1a1a1a; color: #ffffff; padding: 3rem; border-radius: 8px; font-family: system-ui, -apple-system, sans-serif; max-width: 1200px; margin: 0 auto;">

<h1 style="color: #ffffff; font-size: 2.5rem; margin-bottom: 3rem; text-align: center; font-weight: 300; display: flex; align-items: center; justify-content: center; gap: 1rem;">The Anatomy of an <div style="display: inline-flex; align-items: center;"><!----><svg width="71" height="20" viewBox="0 0 71 20" color="white" fill="none" xmlns="http://www.w3.org/2000/svg" style="height: 2.5rem; width: auto; color: currentColor;">
    <path d="M3.41511 17.2983L7.88487 12.7653L9.51149 18.9412L11.8745 18.2949L9.52021 9.32758L0.6953 6.93747L0.0668945 9.35199L6.13929 11.0015L1.68809 15.5279L3.41511 17.2983Z" fill="#F34E3F"></path>
    <path d="M16.3045 12.0436L18.6675 11.3973L16.3132 2.43003L7.48827 0.0399246L6.85986 2.45444L14.312 4.47881L16.3045 12.0436Z" fill="#F34E3F"></path>
    <path d="M12.9124 15.4902L15.2754 14.8439L12.9211 5.87659L4.09618 3.48648L3.46777 5.901L10.9199 7.92537L12.9124 15.4902Z" fill="#F34E3F"></path>
    <path d="M30.0743 5.19107H30.114L25.4344 16.4945H22.5195L28.4087 2.3904H31.7994L37.6886 16.4945H34.7539L30.0743 5.19107ZM33.8616 13.9759H26.3267L27.0405 11.5581H33.1478L33.8616 13.9759Z" fill="currentColor"></path>
    <path d="M39.4619 16.4945V5.43284H42.1388V16.4945H39.4619ZM46.8581 10.3089C46.8581 9.39554 46.6995 8.73064 46.3822 8.31411C46.0649 7.89791 45.5956 7.68952 44.9744 7.68952C44.3925 7.68952 43.8639 7.86077 43.388 8.20331C42.9122 8.54583 42.5385 9.00263 42.2677 9.5734C41.9966 10.1445 41.8612 10.732 41.8612 11.3364L41.306 8.7574C41.4513 8.0994 41.7057 7.4981 42.0694 6.95406C42.4328 6.41006 42.9186 5.98378 43.5268 5.67464C44.1347 5.36579 44.842 5.2112 45.6485 5.2112C46.9176 5.2112 47.8858 5.61764 48.5535 6.43021C49.2208 7.24308 49.5548 8.36796 49.5548 9.80511V16.4945H46.8581V10.3089ZM54.3137 10.3089C54.3137 9.44936 54.1384 8.79767 53.7883 8.35441C53.4379 7.91116 52.952 7.68952 52.3308 7.68952C51.736 7.68952 51.2071 7.86077 50.7445 8.20331C50.2817 8.54583 49.9281 8.99255 49.6837 9.5432C49.4389 10.0941 49.3169 10.6851 49.3169 11.3163L48.2659 8.61634C48.4642 7.97159 48.788 7.39075 49.2376 6.87348C49.6868 6.35653 50.2355 5.95012 50.8834 5.65449C51.5309 5.3592 52.258 5.2112 53.0645 5.2112C53.9103 5.2112 54.6276 5.396 55.216 5.76532C55.804 6.13492 56.2437 6.66194 56.5346 7.34697C56.8252 8.03203 56.9708 8.85154 56.9708 9.80513V16.4945H54.3137L54.3137 10.3089Z" fill="currentColor"></path>
    <path d="M59.1943 19.9601V5.43285H61.8712V6.72238C62.3338 6.2256 62.889 5.84938 63.5369 5.59406C64.1844 5.33904 64.8852 5.2112 65.6387 5.2112C66.6035 5.2112 67.4927 5.45995 68.3057 5.95673C69.1187 6.45381 69.7597 7.14234 70.2291 8.02195C70.6982 8.90189 70.933 9.89926 70.933 11.0141C70.933 12.1289 70.6982 13.1231 70.2291 13.9961C69.7597 14.8694 69.1218 15.5443 68.3156 16.021C67.5091 16.4976 66.6035 16.7363 65.5991 16.7363C65.1098 16.7363 64.6405 16.679 64.1912 16.565C63.7417 16.451 63.3187 16.2829 62.9222 16.0613C62.5256 15.8397 62.1752 15.561 61.8712 15.2251V19.9601H59.1943ZM65.1232 14.2781C65.7311 14.2781 66.2733 14.1406 66.7492 13.8651C67.225 13.5899 67.595 13.2037 67.8596 12.7065C68.1239 12.2097 68.2561 11.6456 68.2561 11.0141C68.2561 10.329 68.1238 9.7346 67.8596 9.23087C67.595 8.72715 67.225 8.33772 66.7492 8.06225C66.2733 7.78711 65.7311 7.64919 65.1232 7.64919C64.4753 7.64919 63.9068 7.78364 63.4179 8.05217C62.9287 8.32103 62.5485 8.70699 62.2777 9.21073C62.0067 9.71445 61.8713 10.2956 61.8713 10.9536C61.8713 11.6386 62.0067 12.233 62.2777 12.7368C62.5485 13.2405 62.9287 13.6233 63.4179 13.8852C63.9068 14.1472 64.4753 14.2781 65.1232 14.2781Z" fill="currentColor"></path>
</svg>
<!----></div> Workflow</h1>

<div class="workflow">

  <div class="row">
    <div class="body">
      <p style="font-size: 1.5rem; line-height: 1.6; margin-bottom: 1rem;">
        Start by describing a real, tightly-scoped problem or desired integration in an Amp thread.
      </p>
      <p style="font-size: 1.5rem; line-height: 1.6; margin-bottom: 1rem;">
        Examples: "Integrate Groq API into Libre Chat," "Investigate Groq provider conversation flow issue," "Fix OpenRouter model dropdown population issue."
      </p>
      <p style="font-size: 1.5rem; line-height: 1.6;">
        Include any error output, screenshots, and summary of symptoms or gaps.
      </p>
    </div>
    <div class="label problem">
      <span class="bar"></span>
      Problem Definition
    </div>
  </div>

  <div class="row">
    <div class="body">
      <p style="font-size: 1.5rem; line-height: 1.6; margin-bottom: 1rem;">
        Ask for a research-backed plan from the Oracle before requesting code changes, e.g. "Use the Oracle to research… then create an implementation plan."
      </p>
      <p style="font-size: 1.5rem; line-height: 1.6;">
        Amp responds with detailed TODOs and step-by-step plans specific to the stack, based on source code investigation and external API documentation.
      </p>
    </div>
    <div class="label plan">
      <span class="bar"></span>
      Research & Planning
    </div>
  </div>

  <div class="row">
    <div class="body">
      <p style="font-size: 1.5rem; line-height: 1.6; margin-bottom: 1rem;">
        When blocked, paste exact errors or system output from your runtime (build, test, or app logs).
      </p>
      <p style="font-size: 1.5rem; line-height: 1.6;">
        Amp traces back the problem using source search ("search for OpenRouter-related code," "find where provider value is being passed") and iteratively proposes specific code or config adjustments.
      </p>
    </div>
    <div class="label debug">
      <span class="bar"></span>
      Debug & Iterate
    </div>
  </div>

  <div class="row">
    <div class="body">
      <p style="font-size: 1.5rem; line-height: 1.6; margin-bottom: 1rem;">
        After each code change, Amp will automatically pompt itself to test: "Now let me test the fix by running X," and report the resulting output or error.
      </p>
      <p style="font-size: 1.5rem; line-height: 1.6;">
        Amp examines build output, backend logs (e.g. podman, npm errors), and guides any missing dependency installs or required container restarts.
      </p>
    </div>
    <div class="label test">
      <span class="bar"></span>
      Test & Validate
    </div>
  </div>

  <div class="row">
    <div class="body">
      <p style="font-size: 1.5rem; line-height: 1.6; margin-bottom: 1rem;">
        For frontend changes, Amp will validate the UI/UX changes in the browser. Amp can also use an MCP such as Playwright to automate browser testing.
      </p>
      <p style="font-size: 1.5rem; line-height: 1.6;">
        Amp ties backend config, server environment, and frontend build together for end-to-end fixes.
      </p>
    </div>
    <div class="label verify">
      <span class="bar"></span>
      UI/UX Verification
    </div>
  </div>

  <div class="row">
    <div class="body">
      <p style="font-size: 1.5rem; line-height: 1.6; margin-bottom: 1rem;">
        If the first fix doesn't work, update the thread with current symptoms/logs, and repeat with Amp until resolved.
      </p>
      <p style="font-size: 1.5rem; line-height: 1.6;">
        The workflow is highly interactive and dialogue-driven, treating Amp as your pair-programming partner for both research and incremental implementation.
      </p>
    </div>
    <div class="label iterate">
      <span class="bar"></span>
      Continuous Iteration
    </div>
  </div>

</div>

</div>

</div>

---

## Core Principles

- **Tightly-scoped problems**: Focus on specific, actionable issues rather than broad requirements
- **Research-first approach**: For comprehensive changes, always start with investigation and planning before implementation
- **Error-driven debugging**: Use actual logs and outputs to guide problem-solving
- **End-to-end validation**: Verify fixes work from backend to frontend
- **Incremental iteration**: Test after each change and adjust based on results

## Example Thread Starters

✅ **Good**: "Integrate Groq API into Libre Chat - getting 401 errors on authentication"

✅ **Good**: "OpenRouter model dropdown not populating - see attached screenshot"

❌ **Avoid**: "Make the app better" or "Add AI features"

❌ **Avoid**: "Fix all the bugs" or "Optimize performance"

## Success Indicators

- [ ] Specific problem described with context
- [ ] Research plan requested and received
- [ ] Errors/logs shared for debugging
- [ ] Each fix tested and validated
- [ ] UI changes verified in browser
- [ ] Iterative improvement cycle maintained
