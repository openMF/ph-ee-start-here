# ph-ee-bom

**`ph-ee-bom`** (`org.mifos:ph-ee-bom`) is the single Bill of Materials that pins the shared Java stack for every PH-EE connector: **Spring Boot 3.4, Apache Camel 4, Jakarta EE 10, Zeebe 8, JDK 21**.

It lives in [`ph-ee-bom/`](../ph-ee-bom/) in this repository **temporarily**, until the Payment Hub 2.0 repository structure is in place.

## Using it

Deployable connectors (leaf apps) import it with `enforcedPlatform`:

```groovy
implementation enforcedPlatform('org.mifos:ph-ee-bom:2.0.0-SNAPSHOT')
```

Shared libraries (e.g. `ph-ee-connector-common`) use `platform` instead, so they don't leak forced versions onto their own consumers:

```groovy
implementation platform('org.mifos:ph-ee-bom:2.0.0-SNAPSHOT')
```

With the BOM imported, dependencies are declared **without versions** — the BOM supplies them.

## What it manages

- Imported BOMs: Spring Boot, Apache Camel, AWS SDK v2.
- Explicit constraints for what those don't cover: Zeebe / Camunda, the Jakarta EE 10 APIs, Hibernate Validator 8, EclipseLink 4, Apache CXF 4, SpringDoc, Flyway 10, the Elasticsearch 7 legacy client, the Jackson modules, JUnit / Mockito, and more.
- A `bom-verification/` subproject resolves every declared constraint in CI, so a broken version fails before the BOM is published.

## Publishing

Published to the Mifos JFrog Artifactory (`https://mifos.jfrog.io/artifactory`, repo `phee-gradle-local` for snapshots). Consumers resolve it from there.

## Future

This BOM is an interim solution. Once the shared Mifos Gradle convention plugins (`mifos-gradle-conventions`) add a Spring Boot 3.x / JDK 21 profile, they will take over centralized dependency management and this BOM will be replaced by them.
