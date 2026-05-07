# iocontext-release-assets

Public release-binary host for `iocontext-cli` npm `postinstall`.

## Purpose

This repository publishes prebuilt binaries to GitHub Releases so end users can run:

```bash
npm install -g iocontext-cli@latest
```

without falling back to local `cargo build`.

## Expected Asset Names

Assets must match:

- `iocontext-<target-triple>-iocontext[.exe]`
- `iocontext-<target-triple>-iocontext-mcp[.exe]`
- `*.sha256` checksum for each binary

Example (Windows x64):

- `iocontext-x86_64-pc-windows-msvc-iocontext.exe`
- `iocontext-x86_64-pc-windows-msvc-iocontext.exe.sha256`
- `iocontext-x86_64-pc-windows-msvc-iocontext-mcp.exe`
- `iocontext-x86_64-pc-windows-msvc-iocontext-mcp.exe.sha256`

## Release Flow

1. Go to **Actions** in this repo.
2. Run workflow **Build and Publish Assets**.
3. Input:
   - `version_tag`: for example `v0.1.4`
   - `source_ref`: source repo ref to build from (for example `v0.1.4` or `main`)
4. Wait for workflow completion.
5. Verify release `vX.Y.Z` has all platform assets.

## Required Secret

If source repo `iocontext/iocontext-cli` is private, add this secret in this repo:

- `SOURCE_REPO_TOKEN`: PAT with read access to the source repository.
