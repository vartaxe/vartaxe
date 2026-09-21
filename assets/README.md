# Profile artwork

The profile and both ConfigMgr OSD projects share a blue and teal visual identity.
All artwork is stored in this repository. Only the CI status badges are loaded from GitHub Actions.

## Theme and layout

- Blue: `#155799`. Teal: `#117865`.
- Dark gradients: `#0d2e4c` and `#103d38`; dark page background: `#0d1520`.
- Light text is white; dark-page links use `#9dcbff` and headings use `#70dec5`.
- Text: Segoe UI, with Arial and sans-serif fallbacks.
- Wide banners: 1280 x 320. Compact banners: 720 x 260, selected at 600 CSS pixels and below.
- Technology labels: 32 pixels high, with 16-pixel icons and 14-pixel text.

Keep the light, dark, and compact banners in sync when changing the name or tagline.
Use native Markdown headings, links, alerts, and details for content rather than putting it in images.
The heading image has a text alternative; the introduction and project descriptions remain selectable text.

Responsive Markdown pictures keep their width attributes but omit fixed HTML
heights on both sources and images. GitHub constrains image widths without resetting
an explicit height, which otherwise leaves excess vertical space. Intrinsic width,
height, and viewBox remain in each SVG; standalone technology icons retain both
HTML dimensions.

CI badges report push runs on `main`, not deployment certification.
The [funding configuration](../.github/FUNDING.yml) points to the existing GitHub Sponsors account.
The repository's Sponsor button requires this file on the default branch and sponsorships enabled in its settings.

## GitHub Pages

[The website](https://vartaxe.github.io/vartaxe/) uses `jekyll-theme-cayman`.
GitHub Pages publishes from the root of `main`; no `gh-pages` branch is needed.
`_config.yml` supplies the project base URL, navigation, and useful action links.
`index.md` is the website landing page; `README.md` remains the native GitHub profile.
A Jekyll theme cannot change GitHub's profile or repository interface.

The original layout in `_layouts/default.html`, stylesheet in `assets/css/style.scss`,
and `assets/favicon.svg` are shared with both OSD repositories. Keep those files
identical when making a cross-project design change. The layout retains a visible
keyboard focus state, a skip link, semantic navigation, responsive content, and
device-driven light and dark styles. Generated code blocks and tables are
keyboard-focusable for scrolling; code colors use the same contrast-tested palette
as the rest of the site. The stylesheet URL includes the build revision so a new
deployment does not keep an older cached theme. It uses system fonts and no JavaScript.

The supported `jekyll-relative-links` and `jekyll-optional-front-matter` plugins
let the OSD projects use the same Markdown guides on GitHub and GitHub Pages.
Keep repository-specific titles, links, and exclusions in each `_config.yml`,
not in the common layout.

## Icon attribution

The technology labels embed these icons from [GitHub Octicons](https://github.com/primer/octicons):

- `powershell.svg`: [terminal-16](https://github.com/primer/octicons/blob/main/icons/terminal-16.svg)
- `configmgr.svg`: [workflow-16](https://github.com/primer/octicons/blob/main/icons/workflow-16.svg)
- `active-directory.svg`: [organization-16](https://github.com/primer/octicons/blob/main/icons/organization-16.svg)
- `windows.svg`: [device-desktop-16](https://github.com/primer/octicons/blob/main/icons/device-desktop-16.svg)

These are interface icons, not Microsoft product logos.
The upstream [MIT license](octicons-LICENSE.txt) is included with the assets.

The project headings use two icons from
[Microsoft Fluent System Icons](https://github.com/microsoft/fluentui-system-icons):

- `people-team.svg`: [People Team, 24 regular](https://github.com/microsoft/fluentui-system-icons/blob/9cf8af0f95a555918a60b8147a2f33a6a1248442/assets/People%20Team/SVG/ic_fluent_people_team_24_regular.svg).
- `folder-arrow-right.svg`: [Folder Arrow Right, 24 regular](https://github.com/microsoft/fluentui-system-icons/blob/9cf8af0f95a555918a60b8147a2f33a6a1248442/assets/Folder%20Arrow%20Right/SVG/ic_fluent_folder_arrow_right_24_regular.svg).

The path geometry is unchanged from that pinned upstream revision. The wrappers add
accessible titles/descriptions and the shared light/dark colors. Decorative uses
next to an equivalent text heading have an empty image alternative.
The full [Microsoft MIT notice](fluentui-LICENSE.txt) is retained. These interface
symbols do not imply Microsoft affiliation, certification, or endorsement.
