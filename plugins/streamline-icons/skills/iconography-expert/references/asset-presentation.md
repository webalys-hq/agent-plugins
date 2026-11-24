# Presenting search results

Open with one or two sentences on how the results show the concept: the metaphor, how clearly it reads at small sizes, and the visual tone.

Then:

- **In a chat app that shows Streamline's gallery**, the results are already on screen as cards with the preview, name, Set and free or premium status. Don't list them again, and don't restate counts, Set names or status. Refer to them as a group ("the two outline options") or by what they look like ("the box with a down arrow").
- **In a terminal or editor**, there is no gallery. List the results you recommend, up to the count you searched for, each as `[asset name](webUrl) from [Set name](Set webUrl)`, with a few words on how it differs from the others, and say which are premium.

When the user wants one icon, or asked which icon to use, recommend exactly one, named as `[asset name](webUrl) from [Set name](Set webUrl)`, and say in a sentence why.

Rules:

- Keep the order the tool returned.
- Never emit image markdown for a preview.
- Never name an asset that isn't in the results.
