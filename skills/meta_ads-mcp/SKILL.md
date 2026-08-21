---
name: meta_ads-mcp
description: Skill da REST API do Meta Ads (Facebook & Instagram) na MCP.AI: 21 endpoints em /api/meta_ads. Leitura e gestão de campanhas Meta Ads, ad sets, ads, audiências, páginas e Business Manager. Você fornece um long-lived access_token e o Facebook App ID (FB_API_ID). Autentique com workspace API key (sk_live) gerada em app.mcp.ai/settings/api-keys. Use quando o usuário pedir algo coberto pelos endpoints.
---

# Meta Ads (Facebook & Instagram) — REST API skill

Você tem acesso à **Meta Ads (Facebook & Instagram)** REST API na MCP.AI.

> Leitura e gestão de campanhas Meta Ads, ad sets, ads, audiências, páginas e Business Manager. Você fornece um long-lived access_token e o Facebook App ID (FB_API_ID).

## Base URL

```
https://api.mcp.ai/api/meta_ads
```

Todo endpoint é um **POST** na Base URL + o path abaixo. Os parâmetros vão no corpo JSON.

## Autenticação

Inclua em toda request:

```
Authorization: Bearer sk_live_...
Content-Type: application/json
```

> Gere sua chave em **https://app.mcp.ai/settings/api-keys** (workspace API key `sk_live_…`, não expira, revogável). Uma única chave serve pra todos os seus MCPs.

## Formato de resposta

```json
{ "ok": true, "tool": "<tool_id>", "result": <payload> }
```

## Exemplo cURL

```bash
curl -X POST https://api.mcp.ai/api/meta_ads/accounts \
  -H "Authorization: Bearer sk_live_..." \
  -H "Content-Type: application/json" \
  -d '{}'
```

## Reportar problemas

Se um endpoint retornar erro, vazio ou dado inesperado, reporte (não desista calado): **POST /api/meta_ads/report** com `{ "message": "...", "context"?: "...", "conversation"?: [...] }`. Isso notifica o time da MCP.AI.

## Endpoints (21)

#### `meta_ads_list_accounts`

Listar conexões Meta (logins) + ad accounts dentro de cada uma _(POST /api/meta_ads/accounts)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `auth_account` | string | Não | Login Facebook/Meta: id ou label da conexão (multi-conta). Omita se houver apenas uma. |

#### `meta_ads_status`

Validar token, expiry, ad accounts conectados e scopes _(POST /api/meta_ads/status)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `auth_account` | string | Não | Login Facebook/Meta: id ou label da conexão (multi-conta). Omita se houver apenas uma. |

#### `meta_ads_campaigns`

Listar campanhas: id, nome, status, objective, orçamento, datas _(POST /api/meta_ads/campaigns)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `auth_account` | string | Não | Login Facebook/Meta: id ou label da conexão (multi-conta). Omita se houver apenas uma. |
| `account` | string | Não | Ad account ID (act_XXX). Omita para usar o default. |
| `include_paused` | boolean | Não | Incluir campanhas pausadas (default false) |

#### `meta_ads_campaign_write`

Criar, atualizar, pausar ou ativar campanhas. _(POST /api/meta_ads/campaigns/write)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `auth_account` | string | Não | Login Facebook/Meta: id ou label da conexão (multi-conta). Omita se houver apenas uma. |
| `account` | string | Não | Ad account ID (act_XXX). Omita para usar o default. |
| `action` | string | Sim | Ação (create, update, pause, activate) |
| `campaign_id` | string | Não | Obrigatório para update/pause/activate |
| `name` | string | Não | Nome (obrigatório para create) |
| `objective` | string | Não | Objective (obrigatório em create) (OUTCOME_TRAFFIC, OUTCOME_ENGAGEMENT, OUTCOME_LEADS, OUTCOME_SALES, OUTCOME_AWARENESS, OUTCOME_APP_PROMOTION) |
| `daily_budget` | number | Não | Orçamento diário em centavos (5000 = $50). Setar liga o orçamento de campanha (os ad sets então não levam orçamento próprio) |
| `lifetime_budget` | number | Não | Orçamento total em centavos. Setar liga o orçamento de campanha (os ad sets então não levam orçamento próprio) |
| `bid_strategy` | string | Não | Exigido pelo Meta quando o orçamento está na campanha (default LOWEST_COST_WITHOUT_CAP) (LOWEST_COST_WITHOUT_CAP, LOWEST_COST_WITH_BID_CAP, COST_CAP, LOWEST_COST_WITH_MIN_ROAS) |
| `status` | string | Não | Status (ACTIVE, PAUSED) |
| `special_ad_categories` | string[] | Não | Special ad categories (ex.: ["HOUSING", "CREDIT"]) |

#### `meta_ads_campaign_delete`

Deletar campanha (irreversível) _(POST /api/meta_ads/campaigns/delete)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `auth_account` | string | Não | Login Facebook/Meta: id ou label da conexão (multi-conta). Omita se houver apenas uma. |
| `campaign_id` | string | Sim | ID da campanha |

#### `meta_ads_adset_detail`

Detalhes de ad sets: targeting, orçamento, schedule, billing, optimization _(POST /api/meta_ads/adsets)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `auth_account` | string | Não | Login Facebook/Meta: id ou label da conexão (multi-conta). Omita se houver apenas uma. |
| `account` | string | Não | Ad account ID (act_XXX). Omita para usar o default. |
| `include_paused` | boolean | Não | Incluir pausados (default false) |

#### `meta_ads_adset_write`

Criar ou atualizar ad sets. targeting como JSON string. _(POST /api/meta_ads/adsets/write)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `auth_account` | string | Não | Login Facebook/Meta: id ou label da conexão (multi-conta). Omita se houver apenas uma. |
| `account` | string | Não | Ad account ID (act_XXX). Omita para usar o default. |
| `action` | string | Sim | Ação (create, update) |
| `adset_id` | string | Não | ID (obrigatório em update) |
| `campaign_id` | string | Não | Parent campaign (obrigatório em create) |
| `name` | string | Não | Nome |
| `daily_budget` | number | Não | Orçamento diário (centavos). Obrigatório em create, a não ser que a campanha já tenha orçamento próprio |
| `lifetime_budget` | number | Não | Orçamento total (centavos). Exige end_time |
| `billing_event` | string | Não | Billing event (default IMPRESSIONS) (IMPRESSIONS, LINK_CLICKS, POST_ENGAGEMENT, THRUPLAY, PAGE_LIKES, APP_INSTALLS) |
| `optimization_goal` | string | Não | Optimization goal (default LINK_CLICKS). Precisa ser válido pro objective da campanha (LINK_CLICKS, LANDING_PAGE_VIEWS, IMPRESSIONS, REACH, POST_ENGAGEMENT, THRUPLAY, PAGE_LIKES, CONVERSATIONS, LEAD_GENERATION, QUALITY_LEAD, OFFSITE_CONVERSIONS, VALUE, APP_INSTALLS) |
| `targeting` | string | Não | Targeting JSON string (obrigatório em create) |
| `destination_type` | string | Não | Destino do clique quando NÃO é site. Omita pra tráfego de site (MESSENGER, WHATSAPP, PHONE_CALL, APP, INSTAGRAM_DIRECT, ON_AD, ON_POST, ON_VIDEO, ON_PAGE, ON_EVENT) |
| `promoted_object` | string | Não | JSON string do pixel/página que o ad set otimiza, ex.: {"pixel_id":"123","custom_event_type":"PURCHASE"} |
| `bid_amount` | number | Não | Teto de lance em centavos (exigido por LOWEST_COST_WITH_BID_CAP e COST_CAP) |
| `bid_strategy` | string | Não | Estratégia de lance (só quando o orçamento está no ad set) (LOWEST_COST_WITHOUT_CAP, LOWEST_COST_WITH_BID_CAP, COST_CAP, LOWEST_COST_WITH_MIN_ROAS) |
| `start_time` | string | Não | ISO 8601 |
| `end_time` | string | Não | ISO 8601. Obrigatório com lifetime_budget |
| `status` | string | Não | Status (ACTIVE, PAUSED) |

#### `meta_ads_adset_delete`

Deletar ad set (irreversível) _(POST /api/meta_ads/adsets/delete)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `auth_account` | string | Não | Login Facebook/Meta: id ou label da conexão (multi-conta). Omita se houver apenas uma. |
| `adset_id` | string | Sim | Ad Set ID |

#### `meta_ads_ads`

Listar ads com creatives e insights (spend, revenue, ROAS, actions) _(POST /api/meta_ads/ads)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `auth_account` | string | Não | Login Facebook/Meta: id ou label da conexão (multi-conta). Omita se houver apenas uma. |
| `account` | string | Não | Ad account ID (act_XXX). Omita para usar o default. |
| `include_paused` | boolean | Não | Incluir pausados |
| `since` | string | Não | Insights início YYYY-MM-DD |
| `until` | string | Não | Insights fim YYYY-MM-DD |

#### `meta_ads_today`

Dashboard de hoje por ad: spend, revenue, ROAS, CPA, impressões, clicks, CTR + _summary _(POST /api/meta_ads/insights/today)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `auth_account` | string | Não | Login Facebook/Meta: id ou label da conexão (multi-conta). Omita se houver apenas uma. |
| `account` | string | Não | Ad account ID (act_XXX). Omita para usar o default. |
| `include_zero` | boolean | Não | Incluir ads com spend zero |

#### `meta_ads_realtime`

Realtime hourly de hoje por ad + _summary _(POST /api/meta_ads/insights/realtime)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `auth_account` | string | Não | Login Facebook/Meta: id ou label da conexão (multi-conta). Omita se houver apenas uma. |
| `account` | string | Não | Ad account ID (act_XXX). Omita para usar o default. |

#### `meta_ads_roas`

ROAS por período via /insights (inclui ads em qualquer status). _(POST /api/meta_ads/insights/roas)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `auth_account` | string | Não | Login Facebook/Meta: id ou label da conexão (multi-conta). Omita se houver apenas uma. |
| `account` | string | Não | Ad account ID (act_XXX). Omita para usar o default. |
| `since` | string | Não | Início YYYY-MM-DD (default: 1º do mês) |
| `until` | string | Não | Fim YYYY-MM-DD (default: hoje) |
| `level` | string | Não | Nível de agregação (default ad) (ad, adset, campaign, account) |

#### `meta_ads_creative_write`

Criar creative, criar ad ou atualizar ad _(POST /api/meta_ads/creatives/write)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `auth_account` | string | Não | Login Facebook/Meta: id ou label da conexão (multi-conta). Omita se houver apenas uma. |
| `account` | string | Não | Ad account ID (act_XXX). Omita para usar o default. |
| `action` | string | Sim | Ação (create_creative, create_ad, update_ad) |
| `name` | string | Não | Nome do creative ou ad |
| `page_id` | string | Não | create_creative: Facebook Page ID |
| `message` | string | Não | create_creative: copy do anúncio |
| `link` | string | Não | create_creative: URL de destino |
| `image_hash` | string | Não | create_creative: hash do upload de imagem |
| `video_id` | string | Não | create_creative: ID do vídeo enviado |
| `call_to_action_type` | string | Não | CTA (LEARN_MORE, SHOP_NOW, etc.) |
| `adset_id` | string | Não | create_ad: ad set ID |
| `creative_id` | string | Não | create_ad: creative ID |
| `ad_id` | string | Não | update_ad: ad ID |
| `status` | string | Não | create_ad/update_ad: status (ACTIVE, PAUSED) |

#### `meta_ads_creative_delete`

Deletar ad (irreversível) _(POST /api/meta_ads/creatives/delete)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `auth_account` | string | Não | Login Facebook/Meta: id ou label da conexão (multi-conta). Omita se houver apenas uma. |
| `ad_id` | string | Sim | Ad ID |

#### `meta_ads_pages`

Pages: list / insights / posts / post_insights _(POST /api/meta_ads/pages)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `auth_account` | string | Não | Login Facebook/Meta: id ou label da conexão (multi-conta). Omita se houver apenas uma. |
| `action` | string | Sim | Ação (list, insights, posts, post_insights) |
| `page_id` | string | Não | Obrigatório para insights e posts |
| `post_id` | string | Não | Obrigatório para post_insights |
| `period` | string | Não | Aggregação de insights (default day) (day, week, days_28) |

#### `meta_ads_business`

Business Manager: list / accounts / pages / users / pixels _(POST /api/meta_ads/business)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `auth_account` | string | Não | Login Facebook/Meta: id ou label da conexão (multi-conta). Omita se houver apenas uma. |
| `action` | string | Sim | Ação (list, accounts, pages, users, pixels) |
| `business_id` | string | Não | Obrigatório para accounts, pages, users, pixels |

#### `meta_ads_media`

Listar imagens ou vídeos enviados _(POST /api/meta_ads/media)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `auth_account` | string | Não | Login Facebook/Meta: id ou label da conexão (multi-conta). Omita se houver apenas uma. |
| `account` | string | Não | Ad account ID (act_XXX). Omita para usar o default. |
| `action` | string | Sim | Ação (list_images, list_videos) |

#### `meta_ads_media_write`

Upload de imagens/vídeos ou curl command para vídeos grandes locais _(POST /api/meta_ads/media/write)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `auth_account` | string | Não | Login Facebook/Meta: id ou label da conexão (multi-conta). Omita se houver apenas uma. |
| `account` | string | Não | Ad account ID (act_XXX). Omita para usar o default. |
| `action` | string | Sim | Ação (upload_image, upload_video, get_upload_command) |
| `image_url` | string | Não | upload_image: URL pública da imagem |
| `video_url` | string | Não | upload_video: URL pública do vídeo |
| `title` | string | Não | upload_video: título |
| `file_path` | string | Não | get_upload_command: caminho local do vídeo |

#### `meta_ads_audience`

Listar Custom Audiences _(POST /api/meta_ads/audiences)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `auth_account` | string | Não | Login Facebook/Meta: id ou label da conexão (multi-conta). Omita se houver apenas uma. |
| `account` | string | Não | Ad account ID (act_XXX). Omita para usar o default. |

#### `meta_ads_audience_write`

Criar audience ou adicionar usuários (PII SHA-256 hashed automaticamente) _(POST /api/meta_ads/audiences/write)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `auth_account` | string | Não | Login Facebook/Meta: id ou label da conexão (multi-conta). Omita se houver apenas uma. |
| `account` | string | Não | Ad account ID (act_XXX). Omita para usar o default. |
| `action` | string | Sim | Ação (create, add_users) |
| `audience_id` | string | Não | Obrigatório em add_users |
| `name` | string | Não | create: nome |
| `description` | string | Não | create: descrição |
| `users` | object[] | Não | add_users: array de { email, phone?, fn?, ln? } |

#### `meta_ads_audience_delete`

Deletar Custom Audience (irreversível) _(POST /api/meta_ads/audiences/delete)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `auth_account` | string | Não | Login Facebook/Meta: id ou label da conexão (multi-conta). Omita se houver apenas uma. |
| `audience_id` | string | Sim | Audience ID |

---

Este MCP também funciona via **conexão MCP** (Claude / Cursor) em `https://api.mcp.ai/p_meta_ads` — veja o [README](../../README.md). A skill acima é pra consumir a **REST API** direto (agente próprio / código).
