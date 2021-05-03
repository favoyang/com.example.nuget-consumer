#　An example package that depends on org.nuget.system.memory and other dependencies.

`org.nuget.system.memory` is a package (with dependencies) that hosting on [UnityNuGet](https://github.com/xoofx/UnityNuGet) registry https://unitynuget-registry.azurewebsites.net/

OpenUPM uplinks to the UnityNuGet registry, so you can install it directly via OpenUPM registry.

Install via openupm-cli

```sh
$ openupm install com.example.nuget-consumer
notice manifest added com.example.nuget-consumer@1.0.1
notice please open Unity project to apply changes
```

Will added below to your `Packages/manifest.json`.

```
  "scopedRegistries": [
    {
      "name": "package.openupm.com",
      "url": "https://package.openupm.com",
      "scopes": [
        "com.example.nuget-consumer",
        "org.nuget.system.buffers",
        "org.nuget.system.memory",
        "org.nuget.system.numerics.vectors",
        "org.nuget.system.runtime.compilerservices.unsafe"
      ]
    }
```

If Unty prompts

> Assembly 'Packages/org.nuget.system.memory/System.Memory.dll' will not be loaded due to errors:
System.Memory references strong named System.Buffers Assembly references: 4.0.2.0 Found in project: 4.0.3.0.
Assembly Version Validation can be disabled in Player Settings "Assembly Version Validation"

Follow the instruction to disable Player Settings' `Assembly Version Validation`.
