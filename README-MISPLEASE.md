# Floodgate-misplease

Temporary public fork of [GeyserMC/Floodgate](https://github.com/GeyserMC/Floodgate)
for misplease Velocity 4.3.

## Why

Official `floodgate-sqlite-database.jar` uses `javax.inject` on `dataDirectory`.
Velocity 4 / Guice 7 does not inject those fields → NPE and own-linking never loads.

Upstream: [PR #645](https://github.com/GeyserMC/Floodgate/pull/645) (open since 2026-02).

## Patch

`database/sqlite/.../SqliteDatabase.java`: use `com.google.inject.Inject` /
`com.google.inject.name.Named` to match `CommonModule`'s `@Provides @Named("dataDirectory")`.

## Consume

GitHub release asset `floodgate-sqlite-database.jar`, pinned from misplease
`infra/velocity/plugins.yml` (`source: github`).
