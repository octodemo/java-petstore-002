# Work Routing

How to decide who handles what.

## Routing Table

| Work Type | Route To | Examples |
|-----------|----------|----------|
| Entity models and validation | `domain-model` | JPA entities, relationships, converters, validation annotations, `src/main/resources/META-INF/persistence.xml` |
| Business services and persistence behavior | `service-layer` | Catalog, inventory, customer, order, shipping, pricing, CDI/EJB services under `src/main/java/.../service` |
| REST and API contracts | `rest-api` | JAX-RS endpoints, `RestApplication`, Swagger generation and `src/main/webapp/swagger.json` |
| JSF application and presentation | `web-ui` | View beans, admin and shopping pages, templates, CSS, localization, and `src/main/webapp` |
| Build, packaging, and test execution | `build-and-test` | `pom.xml`, Maven profiles, Arquillian configuration, WildFly setup, test and build documentation |

Preset installation adds concrete routes for the configured team. Add or edit rows
here only when their agent names also exist in the casting registry.

## Issue Routing

| Label | Action | Who |
|-------|--------|-----|
| `squad` | Triage: analyze issue, assign `squad:{member}` label | Lead |
| `squad:{name}` | Pick up issue and complete the work | Named member |

### How Issue Assignment Works

1. When a GitHub issue gets the `squad` label, the **Lead** triages it — analyzing content, assigning the right `squad:{member}` label, and commenting with triage notes.
2. When a `squad:{member}` label is applied, that member picks up the issue in their next session.
3. Members can reassign by removing their label and adding another member's label.
4. The `squad` label is the "inbox" — untriaged issues waiting for Lead review.

## Rules

1. **Eager by default** — spawn all agents who could usefully start work, including anticipatory downstream work.
2. **Scribe always runs** after substantial work, always as `mode: "background"`. Never blocks.
3. **Quick facts → coordinator answers directly.** Don't spawn an agent for "what port does the server run on?"
4. **When two agents could handle it**, pick the one whose domain is the primary concern.
5. **"Team, ..." → fan-out.** Spawn all relevant agents in parallel as `mode: "background"`.
6. **Anticipate downstream work.** If a feature is being built, spawn the tester to write test cases from requirements simultaneously.
7. **Issue-labeled work** — when a `squad:{member}` label is applied to an issue, route to that member. The Lead handles all `squad` (base label) triage.

## Work Type → Agent

| Work Type | Primary | Secondary |
|-----------|---------|----------|
| Own Java EE entity models, validation constraints, persistence mappings, and model-focused tests under src/main/java/org/agoncal/application/petstore/model, src/main/java/org/agoncal/application/petstore/constraints, src/main/resources/META-INF, and matching src/test/java tests. | Domain Model | — |
| Own CDI/EJB services, ordering, catalog, inventory, shipping, pricing, and service integration tests under src/main/java/org/agoncal/application/petstore/service and related test packages. | Service Layer | — |
| Own JAX-RS endpoints, REST application wiring, Swagger contract, API behavior, and endpoint integration tests under src/main/java/org/agoncal/application/petstore/rest, src/main/webapp/swagger.json, and matching src/test/java tests. | REST API | — |
| Own JSF view beans, shopping and admin pages, templates, CSS, localization, and view integration tests under src/main/java/org/agoncal/application/petstore/view, src/main/webapp, and matching src/test/java tests. | Web UI | — |
| Own Maven build configuration, WildFly and Arquillian profiles, test execution, packaging, and build/test documentation in pom.xml, src/test/resources, src/main/docker, and README.md. | Build and Test | — |
