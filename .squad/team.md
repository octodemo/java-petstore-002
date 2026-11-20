# Squad Team

> java-petstore-002

## Coordinator

| Name | Role | Notes |
|------|------|-------|
| Squad | Coordinator | Routes work, enforces handoffs and reviewer gates. |

## Members

| Name | Role | Charter | Status |
|------|------|---------|--------|
| Domain Model | Own Java EE entity models, validation constraints, persistence mappings, and model-focused tests under src/main/java/org/agoncal/application/petstore/model, src/main/java/org/agoncal/application/petstore/constraints, src/main/resources/META-INF, and matching src/test/java tests. | `.squad/agents/domain-model/charter.md` | ✅ Active |
| Service Layer | Own CDI/EJB services, ordering, catalog, inventory, shipping, pricing, and service integration tests under src/main/java/org/agoncal/application/petstore/service and related test packages. | `.squad/agents/service-layer/charter.md` | ✅ Active |
| REST API | Own JAX-RS endpoints, REST application wiring, Swagger contract, API behavior, and endpoint integration tests under src/main/java/org/agoncal/application/petstore/rest, src/main/webapp/swagger.json, and matching src/test/java tests. | `.squad/agents/rest-api/charter.md` | ✅ Active |
| Web UI | Own JSF view beans, shopping and admin pages, templates, CSS, localization, and view integration tests under src/main/java/org/agoncal/application/petstore/view, src/main/webapp, and matching src/test/java tests. | `.squad/agents/web-ui/charter.md` | ✅ Active |
| Build and Test | Own Maven build configuration, WildFly and Arquillian profiles, test execution, packaging, and build/test documentation in pom.xml, src/test/resources, src/main/docker, and README.md. | `.squad/agents/build-and-test/charter.md` | ✅ Active |

## Built-in Support Agents

| Name | Role | Charter | Status |
|------|------|---------|--------|
| Scribe | Decision Merger | `.squad/agents/scribe/charter.md` | 📋 Silent |
| Ralph | Work Monitor | `.squad/agents/ralph/charter.md` | 🔄 Monitor |
| Rai | RAI Reviewer | `.squad/agents/rai/charter.md` | 🛡️ RAI |
| Fact Checker | Devil's Advocate & Verification Agent | `.squad/agents/fact-checker/charter.md` | 🔍 Verifier |

## Project Context

- **Project:** java-petstore-002
- **Created:** 2026-11-19
- **Stack:** Java EE 7 web application packaged as a WAR, targeting WildFly 10-26. It uses JPA, CDI, EJB Lite, Bean Validation, JSF, JAX-RS, PrimeFaces, Bootstrap, and Arquillian.
- **Build:** Maven commands are documented in `README.md`; use `mvn clean compile -Dmaven.test.skip=true` or `mvn clean package -Dmaven.test.skip=true` for a no-test build.
- **Tests:** Unit tests run with `mvn clean test`. Arquillian integration tests require WildFly and use the `arquillian-wildfly-remote` or `arquillian-wildfly-managed` Maven profile.
- **Code layout:** Production Java is under `src/main/java/org/agoncal/application/petstore`, web resources under `src/main/webapp`, configuration and seed data under `src/main/resources`, and tests under `src/test`.
- **Conventions:** Preserve Java EE 7/`javax.*` APIs, existing package boundaries, Maven profiles, localized message bundles, and the repository's existing test style. Do not assume a running WildFly or database for ordinary unit-test work.
