# psyche-assets

Public asset host for the Psyche platform. Holds files that external services (Buffer, social platforms, open-graph consumers) need to fetch over HTTP.

Buffer's GraphQL `ImageAssetInput.url` is a required string and Buffer's API has no upload mutation — images must be fetchable over HTTP when Buffer publishes the scheduled post. This repo provides that hosting layer with zero infra cost, indefinite URL stability, and full git history.

This is platform infrastructure, not brand-specific content. Multiple brands and artifact types coexist under top-level directories; none of them get their own repo.

Structure:

    <brand>/<artifact-type>/<slug>/<files>

Initial usage:

    feral-architecture/carousels/<draft-slug>/slide-1.jpg
    feral-architecture/carousels/<draft-slug>/slide-2.jpg
    ...

URL pattern: `https://raw.githubusercontent.com/<owner>/psyche-assets/main/feral-architecture/carousels/<slug>/slide-N.jpg`

Managed by the `publish_carousel_assets` MCP tool in psyche-media. Do not hand-edit.

Privacy note: this repo is public. Do not commit any asset whose content is not already intended for public publication. The publisher enforces a pre-commit keyword scrub (`confidential`, `private`, `draft-only`, `wip`) as a safety net — but the primary guarantee is the intentionality of the caller.
