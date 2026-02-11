
# Chao World Extended API Code Template

The following code is a template to start off with CWE mods - This is the *bare minimum* of what can be used to start a mod using the CWE API. You may need to add more include statements for some mods to run properly (ie `SA2ModLoader.h` and `ModelInfo.h` for NJS and ModelInfo* objects) In every coding section of a mod using the CWE API, you will see this page come up as it is your boilerplate for starting a mod.

Copy and paste the template code below and get started!

```cpp
#include "pch.h"
#include "cwe_api.h"
#include "ModelInfo.h" //Not needed for FTNames.

extern "C" __declspec(dllexport) ModInfo SA2ModInfo = { ModLoaderVer };

// the new way to create CWE API mods functions
// this runs AFTER the JSONs get loaded
// there are also other exportable functions available, such as:
// 	- CWEAPI_EarlyInit (not intended for "API mods" necessarily, lets you run code before CWE initializes)
//  - CWEAPI_LateInit (same thing as EarlyInit but after CWE initializes)
//  - CWEAPI_EarlyLoad (runs before the JSONs get loaded, this is also where the legacy RegisterDataFunc stuff runs)
extern "C" __declspec(dllexport) void CWEAPI_Load(CWE_API* pAPI) {

}

/// all of the code below here is for "legacy" CWE load functions
// legacy CWE load function
void CWELoad(CWE_REGAPI_LEGACY* cwe_api) {
	....
}

// initialization function - MUST exist in order to have CWE and SA2 see your mod
extern "C" __declspec(dllexport) void Init(const char* path) {
	HMODULE h = GetModuleHandle(L"CWE");

	void (*RegisterDataFunc)(void* ptr);
	RegisterDataFunc = (void (*)(void* ptr))GetProcAddress(h, "RegisterDataFunc");
	RegisterDataFunc(CWELoad);
}
```