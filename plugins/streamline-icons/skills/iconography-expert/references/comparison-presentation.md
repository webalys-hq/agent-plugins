# Presenting a comparison

Use this when the user asks to compare Families or Sets, or asks "X or Y".

Write one entry per compared item, in the order the user named them:

```markdown
**[Family or Set name](webUrl)** (<icon count> icons): best for <use>. Trade-off: <limitation>.
```

Then end with a verdict: which one you'd pick for their product, and the one condition that would change it. A comparison without a winner hands the choice back to the user.

Rules:

- Compare what the user will see: corner radius, stroke weight, terminals, fills and detail.
- Names are links to the `webUrl` a tool returned; plain text when it's missing.
- Where `show_families_preview` is displayed, the compared Families are already on screen, drawn with the same icons: keep the entries to a line each, or replace them with your verdict.
- Icon counts come from `iconCount` in `search_families`'s `sampleSets`, free or premium status from `isFree`, both unchanged.
