# Frontend practices

- Mobile first: the owner uses an iPhone and several computers. Touch targets are at least 44 px on phones.
- Spanish text only through `es.ts`.
- Icon-only buttons need an accessible name (`aria-label`) and a tooltip. Tooltips also show on keyboard focus because phones have no hover.
- Search boxes are debounced and keep the previous results while loading (no flicker).
- Long lists use a searchable dropdown (combobox) that queries the server.
- Do not add a UI library for one component; write the small component.
- `npm run check` (types, lint, format, tests) must pass before any push.
