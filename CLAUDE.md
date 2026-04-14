# Kaavio HubSpot Theme

Customized fork of HubSpot's Elevate theme (developer project, not Design Manager theme).

## Setup

- Fork: `KaavioAI/cms-elevate-theme-public`
- HubSpot account ID: 45990723
- Project name in HubSpot: `ElevateThemePublic`
- Deploy: `pnpm run build && pnpm exec hs project upload` (from this dir)

## Key Decisions

- Header/footer partials are hardcoded HTML (no DnD areas) so template changes propagate to all pages immediately
- Blog pages and landing pages use separate partial sets: `header.hubl.html`/`footer.hubl.html` (site-wide) vs `lp-header.hubl.html`/`lp-footer.hubl.html` (landing pages)
- General Sans font loaded from Fontshare CDN via CSS @import, with Inter (Google) as fallback
- `getServerSideProps` removed from BlogListing and RecentBlogPosts modules (requires Content Hub Pro tier)
- HuBL `now()` and `today()` functions don't work in hardcoded partials outside DnD modules; copyright year is hardcoded

## Brand Colors

| Token | Value | Notes |
|-------|-------|-------|
| Primary blue | `#304dd8` | Was purple `#4F38E0` |
| Hover blue | `#2a3fb5` | Was `#6854E8` |
| Light accent | `#E8EEFF` | Was `#F4F2FF` |
| Medium accent | `#9bb2f0` | Was `#D2CAFF` |

## CLI Quirks

- `hs project upload` frequently loses connection polling build status (ECONNRESET) but builds usually succeed
- Check with `hs project deploy --build N` to verify; "already deployed" means it worked
- Rate limiting can cause upload failures; wait 15-30s between rapid deploys
