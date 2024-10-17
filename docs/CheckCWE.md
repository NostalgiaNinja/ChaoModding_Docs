# Checking if CWE Exists

If you are making a mod that's dependent on CWE, you can optionally write it in code (SA Mod Manager now has the feature to ask for dependencies). Here's how:

in `init()`

```cpp
HMODULE cwe = GetModuleHandle("CWE");
if(cwe) {
  RegisterDataLoad = 
  ...
}
```

where `...` replace with any CWE-dependent code that is needed.