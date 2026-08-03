# Frolfy content feed

The live content the Frolfy app fetches. One file:

- **`levels.json`** — the level packs for "The Long Round".

Served by GitHub Pages at
<https://joshuanarehood.github.io/frolfy-content/levels.json>.

## This is published, not authored, here

The source of truth is the (private) `frolfy` repo. Nothing in this repository
should be edited by hand: `./scripts/publish-levels.sh` in that repo re-certifies
every hole against the real generator, checks that no already-published pack has
had its playable content changed, and only then produces the file copied here.
Editing this file directly bypasses all of it, and the app will simply reject
whatever it cannot rebuild.

## It is a separate repo on purpose

The privacy policy is published from `frolfy-privacy` and is a legal and App
Review dependency — external TestFlight will not proceed if that URL stops
resolving. GitHub Pages builds a whole site per push, so a broken content push
would take the policy down with it. The policy changes roughly never; content
changes often. They do not belong in the same blast radius.

## Everything here is public

Including packs marked `"status": "draft"`. Draft hides a pack from *players* —
the app drops it at load — but it does not hide it from anyone who fetches this
URL. Do not put a story here that is meant to stay unread; iterate on unreleased
content locally instead, with `-levelsFeedURL file:///path/to/levels.json`.
