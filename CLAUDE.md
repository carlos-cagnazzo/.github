# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this repository is

This is the special `.github` repository for the `carlos-cagnazzo` GitHub account (remote: `git@github.com:carlos-cagnazzo/.github.git`). It contains no code, so there is nothing to build, lint, or test.

- `profile/README.md` is rendered by GitHub as the public profile page for the organization. It presents the work under the name "Rutas" (subtitle: "Mapping and helping secure the Internet's inter-domain routing system"), links to the tooling (`internet-topology-ris`) and dataset (`internet-topology-datasets`) repos, and lists talks and publications. Most content changes belong here.
- `papers/` holds public PDFs of published papers, which the profile README links to. Their LaTeX sources live in private repos, so only the PDFs are copied here. Link them with absolute `https://github.com/carlos-cagnazzo/.github/blob/main/...` URLs, because relative links don't reliably resolve on the organization's profile page.
- `README.md` at the root only describes the repo itself and is not shown on the profile page.

GitHub also uses a `.github` repository for organization-wide default community health files, such as `CONTRIBUTING.md`, `SECURITY.md`, `CODE_OF_CONDUCT.md`, and issue/PR templates. Files like these placed here apply to every repo in the account that lacks its own copy.

## Working in this repo

- Changes go live on the profile page as soon as they are pushed to `main`. Check the Markdown with GitHub's renderer in mind: GitHub-flavored Markdown, with HTML allowed but sanitized (no scripts or styles).
- Do not add Claude (or any AI tool) to commit messages, PR descriptions, or other attribution: no `Co-Authored-By` trailers and no "Generated with" footers.
