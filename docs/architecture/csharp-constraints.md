# C# Constraints

!!! danger "Critical — do not ignore"
    Unity 6 compiles `Overlooted-Core` with **C# 10 maximum**.  
    The package targets `netstandard2.1` + `LangVersion:10` to match exactly.

## Forbidden in Overlooted-Core

| C# 11+ feature | Use instead |
|---|---|
| `[]` collection expressions | `Array.Empty<T>()` or `new List<T>()` |
| `required` members | Constructor parameters or init-only properties |
| Raw string literals `"""` | Regular string with `\n` escapes |
| Generic attributes | Non-generic attribute base classes |
| List patterns `[a, b, ..]` | Manual index checks |

## Applies To

Only `../Overlooted-Core/src/Overlooted.Core/**`. The Unity-side adapter scripts (in `Assets/Scripts/`) use Unity's own C# version which is less constrained.

## Catching Issues Early

VS Code will flag these before Unity if the `csc.rsp` and `Overlooted.Core.csproj` settings are kept in sync. Run `dotnet build` in the Core repo to catch errors without opening Unity.
