![WinUI hero image](docs/images/header.png)

<h1 align="center" style="border:0">
  File-New-Project Labs: WinUI 3
</h1>

<div align="center">
  Experimental WinUI 3 builds with nightly snapshots, community PRs, and custom features.
</div>

## Build Channels

**Nightly** - `FileNewProject.Labs.WinUI.Nightly`
- Automated daily builds from [microsoft/microsoft-ui-xaml:winui3/main](https://github.com/microsoft/microsoft-ui-xaml/tree/winui3/main)
- Unmodified upstream code
- Version format: `0.0.0-nightly.yyyyMMddHHmmss.sha`

**NightlyCommunity** - `FileNewProject.Labs.WinUI.NightlyCommunity`
- Nightly builds + curated community PRs
- Faster access to bug fixes waiting for official merge
- Version format: `0.0.0-nightlycommunity.yyyyMMddHHmmss.sha`

**Custom** - `FileNewProject.Labs.WinUI.Custom` (coming later)
- NightlyCommunity + other experiments
- Custom modifications and features
- Version format: `0.0.0-custom.N`

## Build Schedule

All builds run automatically on a daily schedule:

| Time | Event | Description |
|------|----------|-------------|
| 12:00 PM (04:00 AM PST) | **Sync with upstream** | Syncs `main` with `microsoft/microsoft-ui-xaml:winui3/main` |
| 1:00 PM (05:00 AM PST)| **Rebase nightlycommunity** | Rebases `nightly-community` onto updated `main` |
| 3:00 PM (07:00 AM PST) | **Build world** | Builds `Nightly` and `NightlyCommunity` packages |

## Getting Started

1. Create or edit `nuget.config` in your project:

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <configuration>
      <packageSources>
        <add key="FileNewProject.Labs" value="https://nuget.pkg.github.com/File-New-Project/index.json" />
      </packageSources>
      <packageSourceCredentials>
        <FileNewProject.Labs>
          <add key="Username" value="YOUR_GITHUB_USERNAME" />
          <add key="ClearTextPassword" value="YOUR_GITHUB_PAT" />
        </FileNewProject.Labs>
      </packageSourceCredentials>
    </configuration>
    ```

   Note: Your GitHub Personal Access Token (PAT) must have `read:packages` scope.

2. Install a package:

```pwsh
dotnet add package FileNewProject.Labs.WinUI.Nightly --prerelease
# or
dotnet add package FileNewProject.Labs.WinUI.NightlyCommunity --prerelease
```

## Nightly Community Included Fixes

The NightlyCommunity channel includes carefully selected community PRs that address critical bugs:

**CueStyler Fixes:**
- CueStyler: Fix TimedTextPadding being applied incorrectly
  - https://github.com/microsoft/microsoft-ui-xaml/pull/9248

- CueStyler: Fix outline rendering of TimedTextCue elements
  - https://github.com/microsoft/microsoft-ui-xaml/pull/9224

**TreeView Fixes:**
- RemoveAtEnd on TreeViewNodeVector broken
  - https://github.com/microsoft/microsoft-ui-xaml/pull/10239

## Disclaimers and Warnings

- **Unofficial and unsupported** - This is not an official Microsoft project
- **No guarantees** - Packages may be unstable, break, or be deleted
- **Use at your own risk** - Test thoroughly before using in production

## License

This project maintains the same MIT license as the upstream [microsoft/microsoft-ui-xaml](https://github.com/microsoft/microsoft-ui-xaml) repository.