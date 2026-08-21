# Meta Ads (Facebook & Instagram)

### Meta Ads (Facebook & Instagram) para Claude, ChatGPT e agentes de IA

Leitura e gestão de campanhas Meta Ads, ad sets, ads, audiências, páginas e Business Manager. Você fornece um long-lived access_token e o Facebook App ID (FB_API_ID).

- 📊 **38 ferramentas**
- ✏️ **Leitura e escrita**
- 💬 **Funciona com qualquer cliente MCP**: Claude Desktop, Cursor, VS Code, Cline, Continue
- 🔑 **Login via magic-link (sem senha)**

[English version](README.en.md) · [Documentação completa](docs/) · [Skill pra agentes](skills/)

---

## Instalar em 1 clique

### Claude (Web e Desktop)

A Anthropic unificou a instalação de MCPs em `claude.ai/customize/connectors`. **O mesmo link serve pra Claude Web e Claude Desktop** (basta estar logado):

[➕ Abrir no Claude e conectar](https://claude.ai/new?modal=add-custom-connector#settings/customize-connectors)

**Manual** (se o deeplink não abrir): [claude.ai/customize/connectors](https://claude.ai/customize/connectors?surface=cowork) → **+** → **Adicionar conector personalizado** → cole **Nome** `Meta Ads (Facebook & Instagram)` e **URL** `https://api.mcp.ai/p_meta_ads`.

### Cursor

[➕ Instalar Meta Ads (Facebook & Instagram) no Cursor](cursor://anysphere.cursor-deeplink/mcp/install?name=meta_ads&config=eyJ1cmwiOiJodHRwczovL2FwaS5tY3AuYWkvcF9tZXRhX2FkcyJ9)

### VS Code (Copilot Chat)

[➕ Instalar Meta Ads (Facebook & Instagram) no VS Code](vscode:mcp/install?name=meta_ads&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fapi.mcp.ai%2Fp_meta_ads%22%7D)

### ChatGPT, Manus, OpenClaw e mais 40+ clientes

Funciona em qualquer cliente MCP que suporte **MCP over HTTP**. A URL do servidor é sempre:

```
https://api.mcp.ai/p_meta_ads
```

Detalhes por cliente: [INSTALL.md](INSTALL.md).

---

## Exemplos de uso

```
Liste minhas contas de anúncio do Meta Ads
Quanto gastei hoje no Facebook Ads e qual o ROAS?
Mostre as campanhas ativas e o orçamento diário
```

---

## 38 ferramentas disponíveis

| Tool | Descrição |
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

Detalhe de cada tool: [docs/ferramentas.md](docs/ferramentas.md)

---

## Preços

Grátis.

---

## Privacidade & LGPD

- **Sub-processadores**: o LLM host que você escolher (Claude, ChatGPT, Cursor, agente próprio). Lista completa em [docs/privacidade-lgpd.md](docs/privacidade-lgpd.md).
- Os dados retornados pelas tools são enviados ao **LLM host que você escolher**, sub-processador fora do nosso controle. Recomendamos planos com opt-out de treinamento.

---

## Perguntas frequentes

**O servidor é open source?**
O servidor é proprietário (hosted). Este repositório é o wrapper público com manifestos, docs e skills — tudo MIT.

**Posso usar com agente próprio (não Claude/Cursor)?**
Sim — qualquer cliente que suporte MCP over HTTP. URL: `https://api.mcp.ai/p_meta_ads`.


---

## Suporte

- 📧 [meta_ads@mcp.ai](mailto:meta_ads@mcp.ai)
- 🐛 [GitHub Issues](https://github.com/mcp-dir/meta_ads-mcp/issues)
- 📄 [docs/](docs/)

---

## Licença

MIT — veja [LICENSE](LICENSE). O servidor MCP em `api.mcp.ai/p_meta_ads` é proprietário (hosted); este repositório (manifestos, docs, skills) é MIT.
