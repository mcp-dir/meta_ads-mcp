# Ferramentas

Meta Ads (Facebook & Instagram) expõe 38 ferramentas.

### 1. `meta_ads_list_accounts`
**Input**: `auth_account` (opcional)

List Meta (Facebook) connections AND the ad accounts inside each — returns `connections[]` (OAuth logins) and `ad_accounts[]` with id (act_XXX), name, currency, timezone, status.

### 2. `meta_ads_status`
**Input**: `auth_account` (opcional)

Validate Facebook token, check expiry date, list connected ad accounts and scopes.

### 3. `meta_ads_campaigns`
**Input**: `account` (opcional), `include_paused` (opcional), `auth_account` (opcional)

List Meta Ads campaigns. Returns: id, name, status, objective, budget, dates. Set include_paused=true to also show paused campaigns.

### 4. `meta_ads_today`
**Input**: `account` (opcional), `include_zero` (opcional), `auth_account` (opcional)

Today's ad performance dashboard.

### 5. `meta_ads_roas`
**Input**: `account` (opcional), `since` (opcional), `until` (opcional), `level` (opcional), `auth_account` (opcional)

ROAS (Return on Ad Spend) for a date range using Meta's /insights endpoint — includes spend from ads in ANY status (ACTIVE/PAUSED/DISABLED/ARCHIVED).

### 6. `meta_ads_ads`
**Input**: `account` (opcional), `include_paused` (opcional), `since` (opcional), `until` (opcional), `auth_account` (opcional)

List ads with creatives (image, video, copy) and performance insights.

### 7. `meta_ads_realtime`
**Input**: `account` (opcional), `auth_account` (opcional)

Hourly realtime dashboard for today.

### 8. `meta_ads_adset_detail`
**Input**: `account` (opcional), `include_paused` (opcional), `auth_account` (opcional)

Get detailed ad set info: targeting, budget, schedule, billing, optimization goal, delivery status.

### 9. `meta_ads_pages_list`
**Input**: `page_id` (opcional), `post_id` (opcional), `period` (opcional), `auth_account` (opcional), `page_ids` (opcional), `post_ids` (opcional)

Read Facebook Pages data. Actions: list — all pages the user manages (name, fan_count, followers) insights — page engagement metrics (follows, views) for a specific page posts — recent posts with likes, comments, shar…

### 10. `meta_ads_pages_insights`
**Input**: `page_id` (opcional), `post_id` (opcional), `period` (opcional), `auth_account` (opcional), `page_ids` (opcional), `post_ids` (opcional)

Read Facebook Pages data. Actions: list — all pages the user manages (name, fan_count, followers) insights — page engagement metrics (follows, views) for a specific page posts — recent posts with likes, comments, shar…

### 11. `meta_ads_pages_posts`
**Input**: `page_id` (opcional), `post_id` (opcional), `period` (opcional), `auth_account` (opcional), `page_ids` (opcional), `post_ids` (opcional)

Read Facebook Pages data. Actions: list — all pages the user manages (name, fan_count, followers) insights — page engagement metrics (follows, views) for a specific page posts — recent posts with likes, comments, shar…

### 12. `meta_ads_pages_post_insights`
**Input**: `page_id` (opcional), `post_id` (opcional), `period` (opcional), `auth_account` (opcional), `page_ids` (opcional), `post_ids` (opcional)

Read Facebook Pages data. Actions: list — all pages the user manages (name, fan_count, followers) insights — page engagement metrics (follows, views) for a specific page posts — recent posts with likes, comments, shar…

### 13. `meta_ads_business_list`
**Input**: `business_id` (opcional), `auth_account` (opcional), `business_ids` (opcional)

Read Facebook Business Manager data.

### 14. `meta_ads_business_accounts`
**Input**: `business_id` (opcional), `auth_account` (opcional), `business_ids` (opcional)

Read Facebook Business Manager data.

### 15. `meta_ads_business_pages`
**Input**: `business_id` (opcional), `auth_account` (opcional), `business_ids` (opcional)

Read Facebook Business Manager data.

### 16. `meta_ads_business_users`
**Input**: `business_id` (opcional), `auth_account` (opcional), `business_ids` (opcional)

Read Facebook Business Manager data.

### 17. `meta_ads_business_pixels`
**Input**: `business_id` (opcional), `auth_account` (opcional), `business_ids` (opcional)

Read Facebook Business Manager data.

### 18. `meta_ads_media_list_images`
**Input**: `account` (opcional), `auth_account` (opcional)

List uploaded media in the ad account.

### 19. `meta_ads_media_list_videos`
**Input**: `account` (opcional), `auth_account` (opcional)

List uploaded media in the ad account.

### 20. `meta_ads_audience`
**Input**: `account` (opcional), `auth_account` (opcional)

List Custom Audiences in the ad account.

### 21. `meta_ads_campaign_write_create`
**Input**: `account` (opcional), `campaign_id` (opcional), `name` (opcional), `objective` (opcional), `daily_budget` (opcional), `lifetime_budget` (opcional), `bid_strategy` (opcional), `status` (opcional), `special_ad_categories` (opcional), `auth_account` (opcional), `campaign_ids` (opcional)

Create, update, pause or activate Meta Ads campaigns.

### 22. `meta_ads_campaign_write_update`
**Input**: `account` (opcional), `campaign_id` (opcional), `name` (opcional), `objective` (opcional), `daily_budget` (opcional), `lifetime_budget` (opcional), `bid_strategy` (opcional), `status` (opcional), `special_ad_categories` (opcional), `auth_account` (opcional), `campaign_ids` (opcional)

Create, update, pause or activate Meta Ads campaigns.

### 23. `meta_ads_campaign_write_pause`
**Input**: `account` (opcional), `campaign_id` (opcional), `name` (opcional), `objective` (opcional), `daily_budget` (opcional), `lifetime_budget` (opcional), `bid_strategy` (opcional), `status` (opcional), `special_ad_categories` (opcional), `auth_account` (opcional), `campaign_ids` (opcional)

Create, update, pause or activate Meta Ads campaigns.

### 24. `meta_ads_campaign_write_activate`
**Input**: `account` (opcional), `campaign_id` (opcional), `name` (opcional), `objective` (opcional), `daily_budget` (opcional), `lifetime_budget` (opcional), `bid_strategy` (opcional), `status` (opcional), `special_ad_categories` (opcional), `auth_account` (opcional), `campaign_ids` (opcional)

Create, update, pause or activate Meta Ads campaigns.

### 25. `meta_ads_campaign_delete`
**Input**: `campaign_id`, `auth_account` (opcional), `campaign_ids` (opcional)

Permanently delete a Meta Ads campaign.

### 26. `meta_ads_adset_write_create`
**Input**: `account` (opcional), `adset_id` (opcional), `campaign_id` (opcional), `name` (opcional), `daily_budget` (opcional), `lifetime_budget` (opcional), `billing_event` (opcional), `optimization_goal` (opcional), `targeting` (opcional), `destination_type` (opcional), `promoted_object` (opcional), `bid_amount` (opcional), `bid_strategy` (opcional), `start_time` (opcional), `end_time` (opcional), `status` (opcional), `auth_account` (opcional), `adset_ids` (opcional), `campaign_ids` (opcional)

Create or update Meta Ads ad sets.

### 27. `meta_ads_adset_write_update`
**Input**: `account` (opcional), `adset_id` (opcional), `campaign_id` (opcional), `name` (opcional), `daily_budget` (opcional), `lifetime_budget` (opcional), `billing_event` (opcional), `optimization_goal` (opcional), `targeting` (opcional), `destination_type` (opcional), `promoted_object` (opcional), `bid_amount` (opcional), `bid_strategy` (opcional), `start_time` (opcional), `end_time` (opcional), `status` (opcional), `auth_account` (opcional), `adset_ids` (opcional), `campaign_ids` (opcional)

Create or update Meta Ads ad sets.

### 28. `meta_ads_adset_delete`
**Input**: `adset_id`, `auth_account` (opcional), `adset_ids` (opcional)

Permanently delete a Meta Ads ad set.

### 29. `meta_ads_creative_write_create_creative`
**Input**: `account` (opcional), `name` (opcional), `page_id` (opcional), `message` (opcional), `link` (opcional), `image_hash` (opcional), `video_id` (opcional), `call_to_action_type` (opcional), `adset_id` (opcional), `creative_id` (opcional), `ad_id` (opcional), `status` (opcional), `auth_account` (opcional), `page_ids` (opcional), `video_ids` (opcional), `adset_ids` (opcional), `creative_ids` (opcional), `ad_ids` (opcional)

Create ad creatives and ads (final step to launch).

### 30. `meta_ads_creative_write_create_ad`
**Input**: `account` (opcional), `name` (opcional), `page_id` (opcional), `message` (opcional), `link` (opcional), `image_hash` (opcional), `video_id` (opcional), `call_to_action_type` (opcional), `adset_id` (opcional), `creative_id` (opcional), `ad_id` (opcional), `status` (opcional), `auth_account` (opcional), `page_ids` (opcional), `video_ids` (opcional), `adset_ids` (opcional), `creative_ids` (opcional), `ad_ids` (opcional)

Create ad creatives and ads (final step to launch).

### 31. `meta_ads_creative_write_update_ad`
**Input**: `account` (opcional), `name` (opcional), `page_id` (opcional), `message` (opcional), `link` (opcional), `image_hash` (opcional), `video_id` (opcional), `call_to_action_type` (opcional), `adset_id` (opcional), `creative_id` (opcional), `ad_id` (opcional), `status` (opcional), `auth_account` (opcional), `page_ids` (opcional), `video_ids` (opcional), `adset_ids` (opcional), `creative_ids` (opcional), `ad_ids` (opcional)

Create ad creatives and ads (final step to launch).

### 32. `meta_ads_creative_delete`
**Input**: `ad_id`, `auth_account` (opcional), `ad_ids` (opcional)

Permanently delete a Meta Ads ad.

### 33. `meta_ads_media_write_upload_image`
**Input**: `account` (opcional), `image_url` (opcional), `video_url` (opcional), `title` (opcional), `file_path` (opcional), `auth_account` (opcional)

Upload images and videos to Meta Ads account.

### 34. `meta_ads_media_write_upload_video`
**Input**: `account` (opcional), `image_url` (opcional), `video_url` (opcional), `title` (opcional), `file_path` (opcional), `auth_account` (opcional)

Upload images and videos to Meta Ads account.

### 35. `meta_ads_media_write_get_upload_command`
**Input**: `account` (opcional), `image_url` (opcional), `video_url` (opcional), `title` (opcional), `file_path` (opcional), `auth_account` (opcional)

Upload images and videos to Meta Ads account.

### 36. `meta_ads_audience_write_create`
**Input**: `account` (opcional), `audience_id` (opcional), `name` (opcional), `description` (opcional), `users` (opcional), `auth_account` (opcional), `audience_ids` (opcional)

Manage Custom Audiences for targeting.

### 37. `meta_ads_audience_write_add_users`
**Input**: `account` (opcional), `audience_id` (opcional), `name` (opcional), `description` (opcional), `users` (opcional), `auth_account` (opcional), `audience_ids` (opcional)

Manage Custom Audiences for targeting.

### 38. `meta_ads_audience_delete`
**Input**: `audience_id`, `auth_account` (opcional), `audience_ids` (opcional)

Permanently delete a Custom Audience.

## Prompts de exemplo

```
Liste minhas contas de anúncio do Meta Ads
Quanto gastei hoje no Facebook Ads e qual o ROAS?
Mostre as campanhas ativas e o orçamento diário
```
