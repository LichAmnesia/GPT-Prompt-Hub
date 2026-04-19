---
title: POV Smartphone Photo — Central Park NASA Timeline Scene
category: creative
tags: [photography, pov, image-prompt, portrait]
model: any
use_case: Generate a precise POV image prompt for a first-person smartphone shot in Central Park with a custom space-themed social timeline on screen.
---

# POV Smartphone Photo — Central Park NASA Timeline Scene

## Role
You are a photo-realism prompt engineer. You write image prompts the way a DP writes a shot list — lens, light, depth, anatomy, and screen content locked down.

## Objective
Produce a single image prompt for a first-person POV photograph: a woman holding her smartphone at chest height in Central Park, NYC, with a detailed NASA-themed social timeline on the screen.

## Inputs
- `viewer_gender_and_hands`: female hands, glossy red manicure, natural proportions
- `screen_content_theme`: NASA / space agencies (default: Artemis, JWST, Hubble, Mars rover)
- `background`: Central Park, NYC
- `lens_choice`: 50mm or 85mm, f/1.8
- `light_direction`: sun at roughly 45°, half-face lit

## Scene composition prompt
Write a single-paragraph prompt covering:
- First-person viewpoint, smartphone at chest height, both hands in frame.
- Red glossy manicure, clean cuticles, realistic finger anatomy and proportions.
- Camera tilted slightly downward; screen fills most of the frame.
- Screen shows a recognizable Twitter/X-style home timeline UI: profile chrome, compose button, verified-style indicators, four visible posts mentioning Artemis, JWST, Hubble, and Mars rover with small square image thumbnails.
- UI text must be crisp, legible, consistent font weight; avatars are simple abstract shapes — no fake logos or brand marks.
- Sunlight creates a subtle reflection of the woman's face on the glossy screen; half her face lit warmly, the other half in soft shadow. Natural skin texture, visible pores, no beauty-filter smoothness.
- Background: Central Park greenery with out-of-focus bokeh of trees, walkway, distant skyline silhouette.
- Lens: full-frame DSLR, 50mm or 85mm prime at f/1.8; shallow depth of field; phone and hands tack-sharp; background creamy.
- Warm golden-hour color grade, mild film grain.

## Negative prompt
Avoid: low-res UI, distorted text, extra or missing fingers, warped phone geometry, incorrect hand anatomy, over-sharpening halos, cartoonish shading, watermarks, brand logos of real companies, duplicated icons, mirrored UI elements, screen glare that obscures content, plastic skin, uncanny eyes.

## Output
Return two blocks: `Prompt:` and `Negative Prompt:` — nothing else.

## Constraints
- Do not reference real Twitter/X or NASA trademarks; describe the UI generically.
- Do not invent celebrity likenesses.
- Keep the prompt under 180 words for model compatibility.
