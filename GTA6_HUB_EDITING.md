# Update the GTA VI hub

The app reads `gta6_hub.json` from the **main** branch of `akhileshgulia72-dotcom/gta6-news-server`.

1. Open `gta6_hub.json` on GitHub and choose **Edit**.
2. Change the content, preserving valid JSON and `"version": 1`.
3. Commit the change to **main**.
4. In the app, open **Today → GTA VI • The Leonida Files** and pull down to refresh.

GitHub's raw-file cache can delay updates briefly. The app checks whenever this screen opens and on manual refresh. It keeps the last valid downloaded version for offline use. If a new file is invalid or unavailable, the last good version remains visible. Before the first successful download, bundled starter content is shown.

## Page controls

- `enabled`: `true` shows articles; `false` shows the update/maintenance state.
- `title`: app-bar title, up to 80 characters.
- `subtitle`: large page headline, up to 200 characters.
- `announcement`: notice at the top; set to `""` to hide it.
- `sections`: categories, in display order. Each has an `id`, `title`, and `items` list.

## Article controls

Every article needs a unique `id` and nonempty `title`.

```json
{
  "id": "your-unique-article-id",
  "title": "Your article title",
  "summary": "Short description shown on the card.",
  "body": "Full article text.\n\nUse escaped newlines for paragraphs.",
  "image_url": "https://example.com/your-image.jpg",
  "link_url": "https://example.com/source",
  "spoiler": false,
  "published": true
}
```

- Remove `image_url` or `link_url` when not needed. Only HTTPS URLs are accepted. Broken images are hidden.
- Set `published` to `false` to hide an article. **This is not privacy protection: the repository and JSON are public.**
- Set `spoiler` to `true` for story/mission spoilers. These are hidden when the user's spoiler filter is on. Keep the page announcement and category labels spoiler-safe.
- Articles use plain text. HTML, scripts, executable code, arbitrary app actions, ad IDs, and purchases are not remotely configurable.
- To add categories, add another section. To remove an item, delete it or unpublish it.
- Keep the file under 1 MB. The app displays up to 200 articles, considers up to 30 categories and 100 items per category, and limits each body to 30,000 characters.

## Validation

From a local checkout, run `python -m json.tool gta6_hub.json` to check JSON syntax before committing. Do not commit passwords, tokens, or private user data. Publishing content does not require an app rebuild after users install the version containing this hub.
