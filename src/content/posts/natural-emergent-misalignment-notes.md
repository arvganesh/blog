---
title: "Notes on Natural Emergent Misalignment from Reward Hacking in Production RL"
pubDate: 2026-04-02
---

I wanted to share my notes on [Notes on Natural Emergent Misalignment from Reward Hacking in Production RL](https://www.anthropic.com/research/emergent-misalignment-reward-hacking).

## What they tried:
- Increased chance of Sonnet 3.7 reward hacking with synthetic document fine-tuning (SDF).
    - Why: Coding environments for RL have HUGE action spaces and sparse reward. Model priors make it unlikely that the "reward hacking" paths are explored so they use SDF.
- RL in coding environments susceptible to the reward hacking approaches fine-tuned on during SDF.
- Evaluated misalignment on held-out tasks. 

## Some results I found interesting:
- "(At the exact point the model begins to reward hack, [they saw] a sharp increase in all our misalignment evaluations."
- After learning to reward hack, the model attempted to sabotage the research project's codebase in ways that would make it harder to detect misalignment (12% of the time vs. 0% in baseline).
- Alignment faking found 50% of the time.
- Inoculation Prompting - When they tell the model it's okay to cheat, misaligned generalization completely disappears. WTF??? 
    - As they increased how "okay" it is to cheat in their prompts, measured misalignment seemed to reduce as well (take this with a grain of salt).

## My thoughts:

- In 2025 and 2026, we've seen a huge increase in the adoption of AI coding tools. As AI continues to be used to develop AI, frontier labs need to be careful about monitoring the output of their models. What if an AI researcher uses a subtly misaligned AI and ends up sabotaging the alignment of the new model they are working on? 
- This further highlights the importance of addressing misalignment during RL and pre-training.
    - I wonder whether, for frontier labs, RL or pre-training is more responsible for any misalignment present in models.
    - The thought of misalignment occurring due to pre-training data is particularly scary since it's probably very hard to detect. My hunch is that bad actors can more easily influence pre-training than post-training.
