# App Store Assets Skills

[简体中文](README.zh-CN.md)

Create store artwork from real app screenshots. Choose the skill for your target store, review the artwork in local HTML, and approve the design before PNG export.

| Target store | Skill | Deliverables |
| --- | --- | --- |
| Apple App Store | [codoop-app-store-assets](.agents/skills/codoop-app-store-assets/SKILL.md) | App Store screenshots, Product Page Header, and Search Results artwork |
| Xiaomi App Store | [codoop-xiaomi-store-assets](.agents/skills/codoop-xiaomi-store-assets/SKILL.md) | Phone listing screenshots and app brand display artwork |

## Xiaomi App Store artwork

Provide real Android screenshots and the app icon. Phone listing screenshots use 1080 × 1920 for portrait or 1920 × 1080 for landscape, according to the app's orientation. Brand display artwork uses a separate 1080 × 480 canvas. Check the developer console for whether to submit it. See the [Xiaomi requirements](.agents/skills/codoop-xiaomi-store-assets/references/xiaomi.md), [review template](.agents/skills/codoop-xiaomi-store-assets/assets/review.html), and [Xiaomi 15 frame preview](.agents/skills/codoop-xiaomi-store-assets/assets/xiaomi-frame.html).

## From app screenshots to Apple App Store artwork

This example uses **Fieldnotes**, a fictional focus app. The images show the workflow and what the artwork can look like for one product.

| Source screenshot | Portrait artwork |
| :---: | :---: |
| <img src="docs/images/app.webp" width="235" alt="Fieldnotes app screen with a focus timer and task list"> | <img src="docs/images/portrait.webp" width="280" alt="Portrait store artwork with a headline and the Fieldnotes screenshot inside an iPhone frame"> |

Provide your app screenshots and any brand assets. The skill plans the artwork around the features visible in your screenshots and places iPhone screenshots inside the [reusable device frame](.agents/skills/codoop-app-store-assets/assets/iphone-frame.html).

The local HTML review shows the artwork together and lets you filter, zoom, and open each canvas at full size. After you approve the design, the skill exports those canvases as PNGs.

![HTML review showing the portrait, Header, and Search Results canvases with filters and zoom controls](docs/images/review.webp)

### Landscape examples

Header and Search Results each support **one to three screenshots**. You can choose which screenshots to use, or let the skill select a set based on what each placement needs to show. These examples use one screenshot per placement to keep the focus timer prominent.

**Product Page Header**

![Wide Fieldnotes header with a large headline and angled iPhone showing the focus timer](docs/images/header.webp)

**Search Results**

![Fieldnotes Search Results artwork with short headline and a large upright iPhone](docs/images/search.webp)

The images above are resized for this README. The skill checks current Apple requirements for the target placement before export.

## Install with the Skills CLI

Run the command for your target store from your app project.

```sh
# Apple App Store
npx skills add https://github.com/Codoop/codoop-app-pages --skill codoop-app-store-assets

# Xiaomi App Store
npx skills add https://github.com/Codoop/codoop-app-pages --skill codoop-xiaomi-store-assets
```

The remote commands install from GitHub. To use changes from your checkout, install from a local path as shown below. The CLI prompts for supported agents and installs to the current project by default. Node.js 22.20 or newer is required by the current CLI. Use `-a codex` to select Codex, or `-g` for a user-wide installation. Inspect available skills first with `npx skills add https://github.com/Codoop/codoop-app-pages --list`. See the [Skills CLI](https://github.com/vercel-labs/skills) for current agent support and options.

For local development, `npx skills add /path/to/codoop-app-pages --skill codoop-xiaomi-store-assets` installs from this checkout. Public search visibility on skills.sh depends on that service's indexing and is not guaranteed by adding this command.

## Install and use

Copy the **entire directory** for the chosen skill, including its templates, frame stylesheet, and any reference files. The destinations below are relative to your app project root.

| Client | Project skill destination | Notes |
| --- | --- | --- |
| Codex | `.agents/skills/<skill-name>/` | Use `$codoop-app-store-assets` / `$codoop-xiaomi-store-assets` or ask by name. |
| Claude Code | `.claude/skills/<skill-name>/` | Ask by name or use the skill command. This repository's Claude link points to the canonical copy; copy the directory on systems without symlink support. |
| Qwen Code | `.agents/skills/<skill-name>/` or `.qwen/skills/<skill-name>/` | Use `/<skill-name>` or ask by name; check `/skills`. |
| Google Antigravity App, CLI or IDE | `.agents/skills/<skill-name>/` | Ask by name; the App and CLI also document slash invocation. |
| DeepSeek through Codex | `.agents/skills/<skill-name>/` | DeepSeek is the model provider; use the host client's installation method. Other DeepSeek clients can use a different directory. |
| WorkBuddy | See the WorkBuddy note below. | Open Platform marketplace packaging has additional metadata requirements. |

For example, after downloading this repository, copy the package to a project for Codex, Qwen Code or Antigravity (macOS/Linux):

```sh
mkdir -p /path/to/your-project/.agents/skills
cp -R /path/to/codoop-app-pages/.agents/skills/codoop-xiaomi-store-assets /path/to/your-project/.agents/skills/
```

Open the target project in your agent, refresh or restart it if needed, and check its available skills. Invoke the skill for your target store, providing real screenshots, brand materials, target devices and preferences. If your client does not discover skills automatically but can read workspace files, explicitly ask it to read the copied `SKILL.md` and its accompanying template. This fallback is not automatic Skill integration.

**WorkBuddy:** its [Open Platform documentation](https://open.workbuddy.cn/en/docs/skill) specifies a `SKILL.md` package and additional required marketplace fields including display names, descriptions, version and author. The portable package in this repository has not been packaged or validated for that marketplace. Local installation and marketplace support depend on the WorkBuddy edition; follow its current import instructions rather than assuming CodeBuddy's project path applies.

These paths follow the clients' documentation, including [Qwen Code](https://github.com/QwenLM/qwen-code/blob/main/docs/users/features/skills.md), [Antigravity](https://prod-20251121t222213-dot-gweb-jetski.appspot.com/docs/skills?tab=ide), and [DeepSeek's Codex integration](https://api-docs.deepseek.com/quick_start/agent_integrations/codex/). They describe documented compatibility, not a claim that every client or version has been tested. The workflow also requires access to project files, images, current web specifications and a browser or equivalent visual inspection; report unavailable capabilities and do not claim checks were performed.

The agent should verify current requirements for the target store, prepare a browser review, and wait for explicit design approval before exporting. Approval does not authorize uploading or publishing.

The template demonstrates review interactions and one illustrative visual direction, not a required layout. The agent first examines the project's brand, interface, assets and user preferences, then designs compositions around that product and each placement. It can replace the example's canvas markup, layouts, palette, typography and device treatments while retaining the review capabilities. Its copy and dimensions are placeholders; Placement eligibility and device cropping must be verified for the specific app.

## License

This project is licensed under the [MIT License](LICENSE).
