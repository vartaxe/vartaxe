# Contributing

Contributions that correct profile content, links, accessibility, or project
metadata are welcome.

1. Create a branch from the current `main`.
2. Keep changes focused and preserve the existing visual and writing style.
3. Verify every changed link and check that local references resolve from both
   GitHub Markdown and the `/vartaxe/` project-site base path.
4. Do not describe automated checks as live ConfigMgr, Active Directory, WinPE,
   SMB, driver, firmware, or hardware validation.
5. Open a pull request and wait for the Pages validation workflow to pass.

Third-party icons retain their upstream licenses and attribution in
[`assets/README.md`](assets/README.md). Security reports do not belong in pull
requests; follow [SECURITY.md](SECURITY.md).

## Layout cleanup

Navigation and action buttons now share `_includes/project-url.html`, removing
duplicate URL branches while preserving the `/vartaxe/` base path, home-page
fragments, external links, and title escaping. The include uses Liquid whitespace
control so rendered `href` values contain no indentation or line breaks.
Before-and-after Liquid rendering comparisons cover home and documentation pages
and root-relative, fragment, external, and relative URLs. These comparisons are
not a full Jekyll build; the Pages workflow remains the publishing check.
