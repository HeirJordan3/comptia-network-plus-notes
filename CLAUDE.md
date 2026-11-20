# CLAUDE.md

This repo holds my CompTIA Network+ (N10-009) study notes, following Professor Messer's free N10-009 course.

## When I paste a Messer video transcript
1. Write a study guide as a new markdown file in the right domain folder:
   `domain-#-name/<objective>-<video-title-kebab-case>.md`
   Example: `domain-1-networking-concepts/1.1-understanding-the-osi-model.md`
2. Start the file with `[← Back to index](../README.md)`, then a source line:
   `**Source video:** [<Video title> – Professor Messer](https://www.professormesser.com/network-plus/n10-009/n10-009-video/n10-009-training-course/) *(length)*`
3. In README.md, change that video's `- [ ]` to `- [x]` and turn its title into a link to the new file.
4. Append the new key terms to `key-terms/key-terms.json` (fields: term, definition, analogy, example, examTip, section).

## Study guide format
- I'm an entry-level developer who's new to networking. Explain simply, building from the basics, and don't assume concepts not covered yet.
- At least one real-world analogy per concept.
- A practical example on a real network or in a dev environment.
- What CompTIA is likely to test, plus common exam traps and mix-ups.
- Conversational and easy to scan: short sections, no walls of text.
- Add Mermaid diagrams (```mermaid code blocks, which GitHub renders) wherever a picture helps: data flows, device chains, comparisons, size ladders. Keep them small and simple.
- End with a **Key Terms** section. Each term gets: Term, Analogy, Example, Exam tip (port numbers, OSI layer, etc. where relevant).

## Rules
- Write notes in my own words. Never copy transcript text or anything from Messer's paid Course Notes.
- Accuracy over embellishment. Flag anything you're unsure of.
- Don't commit or push unless I ask.
