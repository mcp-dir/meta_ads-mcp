# Meta Ads (Facebook & Instagram)

### Meta Ads (Facebook & Instagram) for Claude, ChatGPT and AI agents

Read and manage Meta Ads campaigns, ad sets, ads, audiences, pages and Business Manager. You provide a long-lived access_token and the Facebook App ID (FB_API_ID).

- 📊 **38 tools**
- ✏️ **Read and write**
- 💬 **Works with any MCP client**: Claude Desktop, Cursor, VS Code, Cline, Continue
- 🔑 **Magic-link login (no password)**

[Portuguese version](README.md) · [Full docs (PT-BR)](docs/)

---

## One-click install

### Claude (Web and Desktop)

[➕ Open in Claude and connect](https://claude.ai/new?modal=add-custom-connector#settings/customize-connectors)

Manual: [claude.ai/customize/connectors](https://claude.ai/customize/connectors?surface=cowork) → **+** → **Add custom connector** → name `Meta Ads (Facebook & Instagram)`, URL `https://api.mcp.ai/p_meta_ads`.

### Cursor

[➕ Install in Cursor](cursor://anysphere.cursor-deeplink/mcp/install?name=meta_ads&config=eyJ1cmwiOiJodHRwczovL2FwaS5tY3AuYWkvcF9tZXRhX2FkcyJ9)

### VS Code (Copilot Chat)

[➕ Install in VS Code](vscode:mcp/install?name=meta_ads&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fapi.mcp.ai%2Fp_meta_ads%22%7D)

### Any other MCP-over-HTTP client

```
https://api.mcp.ai/p_meta_ads
```

---

## 38 tools

| Tool | Description |
|---|---|
| `meta_ads_list_accounts` | List Meta (Facebook) connections AND the ad accounts inside each — returns `connections[]` (OAuth logins) and `ad_accounts[]` with id (act_XXX), name, currency, timezone, status. |
| `meta_ads_status` | Validate Facebook token, check expiry date, list connected ad accounts and scopes. |
| `meta_ads_campaigns` | List Meta Ads campaigns. Returns: id, name, status, objective, budget, dates. Set include_paused=true to also show paused campaigns. |
| `meta_ads_today` | Today's ad performance dashboard. |
| `meta_ads_roas` | ROAS (Return on Ad Spend) for a date range using Meta's /insights endpoint — includes spend from ads in ANY status (ACTIVE/PAUSED/DISABLED/ARCHIVED). |
| `meta_ads_ads` | List ads with creatives (image, video, copy) and performance insights. |
| `meta_ads_realtime` | Hourly realtime dashboard for today. |
| `meta_ads_adset_detail` | Get detailed ad set info: targeting, budget, schedule, billing, optimization goal, delivery status. |
| `meta_ads_pages_list` | Read Facebook Pages data. Actions: list — all pages the user manages (name, fan_count, followers) insights — page engagement metrics (follows, views) for a specific page posts — recent posts with likes, comments, shar… |
| `meta_ads_pages_insights` | Read Facebook Pages data. Actions: list — all pages the user manages (name, fan_count, followers) insights — page engagement metrics (follows, views) for a specific page posts — recent posts with likes, comments, shar… |
| `meta_ads_pages_posts` | Read Facebook Pages data. Actions: list — all pages the user manages (name, fan_count, followers) insights — page engagement metrics (follows, views) for a specific page posts — recent posts with likes, comments, shar… |
| `meta_ads_pages_post_insights` | Read Facebook Pages data. Actions: list — all pages the user manages (name, fan_count, followers) insights — page engagement metrics (follows, views) for a specific page posts — recent posts with likes, comments, shar… |
| `meta_ads_business_list` | Read Facebook Business Manager data. |
| `meta_ads_business_accounts` | Read Facebook Business Manager data. |
| `meta_ads_business_pages` | Read Facebook Business Manager data. |
| `meta_ads_business_users` | Read Facebook Business Manager data. |
| `meta_ads_business_pixels` | Read Facebook Business Manager data. |
| `meta_ads_media_list_images` | List uploaded media in the ad account. |
| `meta_ads_media_list_videos` | List uploaded media in the ad account. |
| `meta_ads_audience` | List Custom Audiences in the ad account. |
| `meta_ads_campaign_write_create` | Create, update, pause or activate Meta Ads campaigns. |
| `meta_ads_campaign_write_update` | Create, update, pause or activate Meta Ads campaigns. |
| `meta_ads_campaign_write_pause` | Create, update, pause or activate Meta Ads campaigns. |
| `meta_ads_campaign_write_activate` | Create, update, pause or activate Meta Ads campaigns. |
| `meta_ads_campaign_delete` | Permanently delete a Meta Ads campaign. |
| `meta_ads_adset_write_create` | Create or update Meta Ads ad sets. |
| `meta_ads_adset_write_update` | Create or update Meta Ads ad sets. |
| `meta_ads_adset_delete` | Permanently delete a Meta Ads ad set. |
| `meta_ads_creative_write_create_creative` | Create ad creatives and ads (final step to launch). |
| `meta_ads_creative_write_create_ad` | Create ad creatives and ads (final step to launch). |
| `meta_ads_creative_write_update_ad` | Create ad creatives and ads (final step to launch). |
| `meta_ads_creative_delete` | Permanently delete a Meta Ads ad. |
| `meta_ads_media_write_upload_image` | Upload images and videos to Meta Ads account. |
| `meta_ads_media_write_upload_video` | Upload images and videos to Meta Ads account. |
| `meta_ads_media_write_get_upload_command` | Upload images and videos to Meta Ads account. |
| `meta_ads_audience_write_create` | Manage Custom Audiences for targeting. |
| `meta_ads_audience_write_add_users` | Manage Custom Audiences for targeting. |
| `meta_ads_audience_delete` | Permanently delete a Custom Audience. |

---

## Pricing

Free.

---

## License

MIT — see [LICENSE](LICENSE). The MCP server at `api.mcp.ai/p_meta_ads` is proprietary (hosted); this repo (manifests, docs, skills) is MIT.
