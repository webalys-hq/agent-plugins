# Streamline design knowledge base

Read this before recommending a Family or choosing Sets for interface states, and when the user names another icon library.

## Contents

1. Open-source libraries hosted on Streamline
2. Other libraries ↔ Streamline Families
3. Which Set for which role

---

## 1. Open-source libraries hosted on Streamline

Streamline hosts the most popular open-source icon and emoji libraries as first-class Families. They are searchable and downloadable through the same MCP tools as Streamline's own families.

Consequences for recommendations:

- An open-source, free or "no budget" ask can be answered from the catalog: recommend Streamline's own free Sets or the hosted open-source Family, and show it with `show_families_preview`.
- When the user wants one of these libraries' icons as files, the Family below has them, searchable and downloadable with the same tools. When the project installs the library as a package, such as `lucide-react`, keep using the package.
- When the user wants to use a hosted library ("find the Lucide upload icon", "download Heroicons arrows"), treat it like any other Family: search with its `familySlug` and download normally.

Hosted open-source icon Families (name → Family slug):

| Library                | Family slug            | Notes                                        |
| ---------------------- | ---------------------- | -------------------------------------------- |
| Lucide                 | `lucide`               | Line only                                    |
| Feather                | `feather`              | Line only, small set                         |
| Font Awesome           | `font-awesome`         | Regular and Solid sets                       |
| Heroicons              | `heroicons`            | Outline and Solid sets                       |
| Phosphor               | `phosphor`             | Thin, Light, Regular, Bold, Fill, Duotone    |
| Tabler                 | `tabler`               | Line and Filled sets                         |
| Google Material        | `material-symbols`     | Outlined, Rounded, Sharp × Line and Fill     |
| Fluent UI              | `fluentui`             | Microsoft                                    |
| Carbon                 | `carbon`               | IBM                                          |
| IBM                    | `ibm`                  | IBM Design icons                             |
| Bootstrap              | `bootstrap`            |                                              |
| Remix                  | `remix`                | Line and Fill sets                           |
| Iconoir                | `iconoir`              | Regular and Solid sets                       |
| Radix                  | `radix`                |                                              |
| Solar                  | `solar`                |                                              |
| Majesticons            | `majesticons`          |                                              |
| Ionic Icons            | `ionicons`             |                                              |
| Mynaui                 | `mynaui`               |                                              |
| MingCute               | `mingcute`             |                                              |
| Atlas                  | `atlas`                |                                              |
| Unicons                | `unicons`              |                                              |
| Flagpack               | `flagpack-icons`       | Country flags                                |
| SimpleIcons            | `simpleicons`          | Brand logos                                  |
| SVG Logos              | `svg-logos-icons`      | Brand logos                                  |
| Brand Logos            | `brand-logos`          | Brand logos                                  |
| Cryptocurrency Icons   | `cryptocurrency-icons` |                                              |
| Fluent Emoji           | `fluent-emoji`         | Microsoft emoji                              |
| Noto Emoji             | `noto-emoji`           | Google emoji                                 |
| Twemoji                | `twemoji-emoji`        | Twitter/X emoji                              |
| OpenMoji               | `openmoji-emoji`       |                                              |
| EmojiTwo               | `emoji-two`            |                                              |
| Opensource Illustrations | `opensource-illustrations` | Illustrations                          |

Slugs were checked against `get_all_families` on 2026-11-10. If a call rejects one, resolve it again with `get_all_families` rather than guessing.

Streamline's own Families also ship free Sets under CC BY 4.0, which requires attribution, such as Core Line - Free, Flex Line - Free, Plump Line - Free, Micro Line - Free and the Streamline Material Free Sets. Offer these first when the user wants Streamline's own style at no cost, and say that they need attribution. A free Set has fewer icons than its premium Set, so search it for the concepts the user needs before recommending it.

## 2. Other libraries ↔ Streamline Families

This table pairs each library with the Streamline Families closest to it in geometry, stroke and corner language. Read it both ways:

- **Library → Streamline**: when the user uses a library ("we use Lucide", "something like Heroicons") and wants more icons in a similar style, or a style that goes with it, recommend the Streamline Families in its row. For "the same brand but warmer", stay in the row's corner language and move toward rounder, softer Families such as Flex or Plump.
- **Streamline → library**: when the user asks for an open-source or free alternative to a Streamline Family, recommend that Family's own free Sets first, then the hosted library from the first row that names it.

Where a Family appears in several rows, the first row is the closest match.

| Open-source library | Streamline direction  |
| ------------------- | --------------------- |
| Lucide              | Core / Streamline 3.0 |
| Feather             | Core Line             |
| Font Awesome        | Core / Ultimate       |
| Heroicons           | Sharp / Ultimate      |
| SF Symbols          | Ultimate / Nova       |
| Phosphor            | Flex / Nova           |
| Material Symbols    | Streamline Material   |
| Carbon              | Sharp / Cyber         |
| Tabler              | Streamline 3.0        |

SF Symbols is the one library in this table that Streamline doesn't host: map it to Streamline Families only.

Example reverse lookups:

- Core Line → Core Line - Free, then Feather, then Lucide
- Core → Core free sets, then Lucide, then Font Awesome
- Ultimate → Font Awesome, then Heroicons
- Sharp → Sharp free sets, then Heroicons, then Carbon
- Nova → Phosphor
- Streamline Material → Streamline Material Free sets, then Google Material

## 3. Which Set for which role

These follow how Streamline describes its Set styles:

- **Line**: default and inactive icons, and most interface icons.
- **Solid, Bold or Fill**: active and selected states, and small sizes or dark backgrounds where a line looks too light. Pair it with the Line Set of the same Family.
- **Duo or Duotone**: two colours to tell actions apart, or to highlight features and onboarding steps.
- **Flat, Colors, Pop and Gradient**: illustrative, colourful Sets that work best at larger sizes, such as feature sections, empty states and marketing pages, and Gradient on dark backgrounds; not for dense controls.
- **Neon**: two line colours for quick recognition and hierarchy in busy interfaces, such as dashboards.
- **Remix**: line and solid mixed in one Set. Use it alone, not alongside the same Family's Line or Solid Set.
- **Light, Regular and Bold weights** (Ultimate): match the weight of the interface's text.
- Keep one corner language on a page: rounded Families (Flex, Plump) don't mix with sharp ones (Sharp, Cyber).
