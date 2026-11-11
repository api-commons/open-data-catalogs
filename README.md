# Open Data Catalogs

The common open-data vocabulary -- the datasets a portal publishes, the distributions (files and APIs) each dataset offers and the publishers responsible for them -- distilled from the APIs that already exist. CKAN's Action API, the most widely installed portal interface, is profiled as a standard of its own in api-commons/open-data; here the dataset is measured across every kind of portal. Part of [Schema Commons](https://github.com/api-commons/schema-commons),
published by the [API Commons](https://apicommons.org).

Built from the providers tagged Open Data, Data Catalog, Government Data, DCAT, CKAN, Open Government, Data Portal in [APIs.io](https://apis.io) that
publish their own OpenAPI. Only harvested contracts count -- nothing API Evangelist
generated. Every number below is a count of providers.

## What the market already agrees on

<!-- commons:summary -->
| Concept | Expose it | Readable schema | Core properties (share) | Collection named |
| --- | ---: | ---: | --- | --- |
| dataset | 33 | 29 | id 72% | datasets 22, dataset 7, package_search 6, package_show 6 |

Cohort: 276 providers with harvested OpenAPI, 33 crosswalks. Of the providers exposing a dataset: 18% create, 82% list, 73% fetch, 9% update, 18% delete. Generated 2026-11-11 by build.py.
<!-- /commons:summary -->

Shares are of the providers with a readable resource schema for that concept. The
extended tier and the long tail of every concept are in [profile.yml](profile.yml).

## What the measurement shows

- A dataset agrees only on an id across 33 portals; its name (48%) and description (41%) fall just short. CKAN portals wrap every response in an untyped result, and portals built on other platforms serve datasets as views, so the dataset that every open-data standard describes is rarely published as a typed resource.
- Measured against DCAT-US 1.1, the standard defines the dataset core and eleven more fields -- keywords, publisher, contact point, access level, temporal and spatial coverage -- that no portal in the cohort publishes as a property of the dataset resource.

## Measured against the standard

The census reads what providers publish. Where the domain has a standard, the standard's own
definition is read as one more voice: how much of the measured core it defines, and what it
defines that no provider in the cohort publishes. Crosswalks are in [standards/](standards).

| Standard | Concept | Core defined by the standard | Fields only the standard has |
| --- | --- | ---: | ---: |
| [dcat-us-1.1](https://github.com/project-open-data/project-open-data.github.io/tree/master/v1.1/schema) | `dataset` | 100% | 11 |
| [dcat-us-1.1](https://github.com/project-open-data/project-open-data.github.io/tree/master/v1.1/schema) | `distribution` *(not published by the market)* | -- | 9 |

## Artifacts

- [openapi.yml](openapi.yml) -- OpenAPI 3.1 of the shared operations. No one serves it; it
  is the shape to map to. Lints clean against the
  [naming ruleset](https://github.com/api-commons/schema-commons/blob/main/ruleset/schema-commons-naming.yaml).
- [schema/](schema) -- JSON Schema 2020-12 per concept; each property carries
  `x-commons-tier`, `x-commons-share`, `x-commons-providers` and the spellings seen.
- [crosswalk/](crosswalk) -- one per provider, common name -> their name, with the harvested
  spec and operations each mapping was read from.
- [adopters.yml](adopters.yml) -- who exposes which concept, linked to their APIs.io page.
- [concepts.yml](concepts.yml) -- the only hand-written input: concepts, path segments and
  their qualifiers, aliases, reviewed exclusions, merged duplicates, and the decisions below.
- [census/](census) -- the cohort and the raw census the profile is built from.

## Decisions

These are calls, not measurements, recorded so they can be revisited as the method matures.

- CKAN's Action API is profiled as its own standard in api-commons/open-data; this context measures the dataset across every kind of portal, CKAN action paths included.
- Packages, package_show and views beneath a data API are datasets.
- Distributions and publishers were measured and dropped; DCAT-US's distribution is recorded as the shape the standard defines.
- Duplicates merged: BLS, CDC, NESO, Powershop.

## Rebuild

```bash
../schema-commons/scripts/run.sh .
```

## License

Artifacts CC BY-NC-SA 4.0 ([LICENSE](LICENSE)); code Apache 2.0 ([LICENSE-CODE](LICENSE-CODE)).
