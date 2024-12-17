# Community.PowerToys.Run.Plugin.Dependencies

[![package](https://github.com/hlaueriksson/Community.PowerToys.Run.Plugin.Dependencies/actions/workflows/package.yml/badge.svg)](https://github.com/hlaueriksson/Community.PowerToys.Run.Plugin.Dependencies/actions/workflows/package.yml)
[![Community.PowerToys.Run.Plugin.Dependencies](https://img.shields.io/nuget/v/Community.PowerToys.Run.Plugin.Dependencies.svg?label=Community.PowerToys.Run.Plugin.Dependencies)](https://www.nuget.org/packages/Community.PowerToys.Run.Plugin.Dependencies)

This NuGet package simplifies referencing all PowerToys Run Plugin dependencies.

It contains the `ARM64` and `x64` versions of:

- `PowerToys.Common.UI.dll`
- `PowerToys.ManagedCommon.dll`
- `PowerToys.Settings.UI.Lib.dll`
- `Wox.Infrastructure.dll`
- `Wox.Plugin.dll`

## Installation

.NET CLI:

```cmd
dotnet add package Community.PowerToys.Run.Plugin.Dependencies
```

Package Manager:

```cmd
PM> NuGet\Install-Package Community.PowerToys.Run.Plugin.Dependencies
```

PackageReference:

```csproj
<PackageReference Include="Community.PowerToys.Run.Plugin.Dependencies" Version="0.86.0" />
```

## Example

Example of a `.csproj` file:

```csproj
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>net9.0-windows10.0.22621.0</TargetFramework>
    <UseWPF>true</UseWPF>
    <Platforms>x64;ARM64</Platforms>
    <PlatformTarget>$(Platform)</PlatformTarget>
  </PropertyGroup>

  <ItemGroup>
    <PackageReference Include="Community.PowerToys.Run.Plugin.Dependencies" Version="0.86.0" />
  </ItemGroup>

  <ItemGroup>
    <None Include="plugin.json">
      <CopyToOutputDirectory>PreserveNewest</CopyToOutputDirectory>
    </None>
    <None Include="Images/*.png">
      <CopyToOutputDirectory>PreserveNewest</CopyToOutputDirectory>
    </None>
  </ItemGroup>

</Project>
```

Use these properties:

```
<TargetFramework>net9.0-windows10.0.22621.0</TargetFramework>
```

- The target framework for the official plugins is defined in [Common.Dotnet.CsWinRT.props](https://github.com/microsoft/PowerToys/blob/main/src/Common.Dotnet.CsWinRT.props)

```
<UseWPF>true</UseWPF>
```

- Enable [`UseWPF`](https://learn.microsoft.com/en-us/dotnet/core/project-sdk/msbuild-props-desktop#usewpf) to include necessary WPF libraries

```
<Platforms>x64;ARM64</Platforms>
<PlatformTarget>$(Platform)</PlatformTarget>
```

- The official plugins target both the `x64` and `ARM64` platforms in [Directory.Build.props](https://github.com/microsoft/PowerToys/blob/main/Directory.Build.props)

## Disclaimer

This is not an official Microsoft PowerToys package.

The DLLs are built from [source](https://github.com/microsoft/PowerToys) and pushed to [NuGet](https://www.nuget.org/packages/Community.PowerToys.Run.Plugin.Dependencies) with a GitHub Actions [workflow](https://github.com/hlaueriksson/Community.PowerToys.Run.Plugin.Dependencies/actions/workflows/package.yml).
