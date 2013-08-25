Ltc.MSBuild.UpdateVersion.targets
=================================
This is a msbuild file which will update `AssemblyInfo.cs` in your ***TFS connected VS project*** automatically on `Release` build.


How this works?
===============
It queries the history from TFS, get latest **changeset id** and **modified date**, then modify the existing `AssemblyVersion` and `AssemblyFileVersion` accordingly.

The version is formatted as `$(MajorVersion).$(MinorVersion).$(ChangesetId).$(Mdd)` where

* $(MajorVersion): Default is 1
* $(MinorVersion): Default is 0
* $(ChangesetId): Latest changeset id of project history queried from TFS
* $(Mdd): Latest changeset modified date in `Mdd` format

> To prevent assembly referencing issue (strong name, version conflict, etc.), only `AssemblyFileVersion` will change all parts of revision number, `AssemblyVersion` changes only if the `MajorVersion` or `MinorVersion` have been changed.

How to install?
===============
1. Run `Install-Package Ltc.MSBuild.UpdateVersion.targets` command in the [Package Manager Console](http://docs.nuget.org/docs/start-here/using-the-package-manager-console).
2. Done, that's all you have to do.


What's changed by the nuget package
===================================
* Add `Build\UpdateVersion.targets` and `Build\VersionInfo.targets` files to your project.
* Add `<Import />` to your project file (`.csproj`).
