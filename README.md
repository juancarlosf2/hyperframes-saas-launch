# HyperFrames SaaS Launch

A reusable agent skill for making editable SaaS launch videos, app trailers, and feature demos. It takes a real product workflow from storyboard to animated UI, preview, and export. A style reference can inform the pace, framing, and transitions while the scenes and assets come from your product.

## Install

From your project, install the skill for Codex. Add `-g` to make it available across projects.

```sh
npx skills add juancarlosf2/hyperframes-saas-launch --skill hyperframes-saas-launch -a codex
```

You can also download the repository and copy the [skill folder](skills/hyperframes-saas-launch) into your agent's skills directory. See the [Skills CLI](https://github.com/vercel-labs/skills#install-a-skill) for supported agents.

When you ask for a video, the skill checks for a suitable editor. It defaults to [HyperFrames](https://hyperframes.heygen.com/#get-started) and prompts you to add the official editor skills if they are missing.

```sh
npx skills add heygen-com/hyperframes
```

You can specify After Effects or another editor that you have set up. The workflow checks whether its skill and runtime are available before building.

## Try it

> Make a short launch video for this app. Show a user completing its main workflow, make the result easy to read, and end with our call to action. Use the product screens in this project.

The [skill](skills/hyperframes-saas-launch/SKILL.md) covers the production process. The [motion and review guide](skills/hyperframes-saas-launch/references/motion-and-review.md) includes a sample shot map and checks for fast transitions and readable UI.
