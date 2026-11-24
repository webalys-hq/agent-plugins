# Presenting a Family recommendation

Where `show_families_preview` is displayed, the preview is the recommendation: reply in one or two sentences with your pick and the next step, and skip the block below. Where no preview is displayed, such as a terminal or editor, write it.

Open with one sentence tying the choice to the user's product, audience and tone. Then:

```markdown
## Best recommendation

**[Family name](webUrl)**, [Set name](Set webUrl) for <role, such as "navigation and actions">

2–4 sentences on why it fits: the shapes the user will see (corners, stroke weight, fills, detail), how they suit the audience and tone, and how the Set works in the interface.

<icon count> icons. <Premium, or free under CC BY 4.0, from the Set's data. On the free plan, name the Family's free Set when the recommended one is premium.>
```

Then, only if it helps:

```markdown
## If you want <the condition, such as "something warmer">

**[Family name](webUrl)**: 1–2 sentences on how it differs and when it's the better pick.
```

Rules:

- One recommended Family, and at most one alternative, which is clearly secondary and in the same corner language (rounded or sharp).
- Family and Set names are links to the `webUrl` a tool returned. When a `webUrl` is missing, write the name as plain text.
- Name a second Set of the same Family only for a distinct role, such as Solid for active states.
- Where the preview is displayed, the Families and their sample icons are already on screen: don't list them again. Where none is, name only the Sets you recommend, as links.
- Icon counts come from `iconCount` in `search_families`'s `sampleSets`, free or premium status from `isFree`, both unchanged.
