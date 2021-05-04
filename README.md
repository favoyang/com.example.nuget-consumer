# Demo UnityNuGet Registry Uplinks

`org.nuget.system.memory` is a package (with dependencies) that hosting on [UnityNuGet](https://github.com/xoofx/UnityNuGet) registry https://unitynuget-registry.azurewebsites.net/

`com.example.nuget-consumer` is an example package that depends on `org.nuget.system.memory`.

OpenUPM uplinks to the UnityNuGet registry, so you can install all `org.nuget` dependencies directly via OpenUPM registry.

Install `com.example.nuget-consumer` via openupm-cli

```sh
$ openupm install com.example.nuget-consumer
notice manifest added com.example.nuget-consumer@1.0.1
notice please open Unity project to apply changes
```

`Packages/manifest.json` changes:

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

Notice that `org.nuget.system.memory` was added to scopes along with its dependencies, to help Unity finds all dependencies.

If Unty prompts

```
Assembly 'Packages/org.nuget.system.memory/System.Memory.dll' will not be loaded due to errors:
System.Memory references strong named System.Buffers Assembly references: 4.0.2.0 Found in project: 4.0.3.0.
Assembly Version Validation can be disabled in Player Settings "Assembly Version Validation"
```

Follow the instruction to disable Player Settings' `Assembly Version Validation`.

![image](https://user-images.githubusercontent.com/125390/116957989-d1047180-accb-11eb-954c-b6a7b452067c.png)

For some uplink integration limitations the `org.nuget.system.memory` will be invisible in PacMan's "My Registries" section, but visible in the "In Project" section.

![image](https://user-images.githubusercontent.com/125390/116958295-aebf2380-accc-11eb-8bf2-0dde300c97e7.png)

![image](https://user-images.githubusercontent.com/125390/116958350-dd3cfe80-accc-11eb-88a9-7868113cde9b.png)
