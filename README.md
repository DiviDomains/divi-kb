# Divi knowledge base

The public part of the knowledge base behind the Divi assistant: the Telegram bot
[@divi_assistant_bot](https://t.me/divi_assistant_bot) and the chat widget on the divi.domains sites.

Every file in `knowledge/` is one category. The bot syncs with this repo about once a minute, so a
change merged into `main` reaches its answers within a minute or two.

| File | Category |
|---|---|
| `core-facts.json` | Core facts about Divi, always given to the bot |
| `rpc-methods.json` | The Divi RPC commands |
| `lottery-odds.json` | Lottery odds and prizes |
| `supply-growth.json` | Block rewards and supply growth |
| `side-chains.json` | Side chains |
| `robert-hirsch-on-medium.json` | Robert Hirsch's articles about Divi on Medium (see Credits) |

## Editing

Edit here (the pencil icon, or a pull request), or in the bot's knowledge base app (`/kb` in
Telegram or the browser). The two stay in sync: a change merged here reaches the bot within about
a minute, and an edit made in the app is committed here by "Divi KB bot", authored by the editor.
If the same entry was changed in both places at once, this repo's version wins and the app's edit
is kept on a `bot-conflict-*` branch.

## Format

```json
{
  "label": "Side Chains",
  "description": "What the category holds",
  "public": true,
  "documents": [
    {
      "id": "unique_id",
      "type": "fact",
      "title": "Short title",
      "content": "The text the bot reads. Markdown is fine.",
      "keywords": ["words", "that", "find", "it"],
      "url": "optional link to the source",
      "citation": "optional credit: author, work, link"
    }
  ],
  "documentCount": 1
}
```

- `"public": true` must stay. A file without it, or with a malformed entry (each needs a string
  `id`, `title` and `content`, a list of string `keywords`, and ids must be unique), is ignored and
  the bot keeps its last good copy.
- `documentCount` is informational; the bot recounts it when it saves an edit.
- Keep the JSON valid: GitHub's editor doesn't check it.

## Credits

`robert-hirsch-on-medium.json` holds the Medium articles about Divi by Robert Hirsch
([shandor.medium.com](https://shandor.medium.com), @hirscrs on Telegram), published here with his
permission, given 2026-10-08. They remain his work: every entry carries a `citation` and a `url` to
its original article.

Other categories the bot uses (the diviproject.org blog, community tutorials and other docs) are
not in this repo.
