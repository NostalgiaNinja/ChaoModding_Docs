
# Chao World Extended API Code Template

The following code is a template to start off with CWE mods - This is the *bare minimum* of what can be used to start a mod using the CWE API. You may need to add more include statements for some mods to run properly (ie `SA2ModLoader.h` and `ModelInfo.h` for NJS and ModelInfo* objects) In every coding section of a mod using the CWE API, you will see this page come up as it is your boilerplate for starting a mod.

Copy and paste the template code below and get started!

```cpp
#include "pch.h"
#include "cwe_api.h"
#include "ModelInfo.h" //Not needed for FTNames.

extern "C"
{
	//registering data functions. - Needs to exist.
	void (*RegisterDataFunc)(void* ptr);

    //main CWE Load function -- Important stuff like adding your CWE mod goes here
	void CWELoad(CWE_REGAPI* cwe_api)
	{

	}

    //initialization function - MUST exist in order to have CWE and SA2 see your mod
	__declspec(dllexport) void Init(const char* path)
	{
		HMODULE h = GetModuleHandle(L"CWE");

		std::string pathStr = std::string(path) + "\\";

		RegisterDataFunc = (void (*)(void* ptr))GetProcAddress(h, "RegisterDataFunc");
		RegisterDataFunc(CWELoad);
	}
	__declspec(dllexport) ModInfo SA2ModInfo = { ModLoaderVer };
}
```