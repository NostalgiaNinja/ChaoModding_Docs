# Character Chao using Custom Accessories

This code was given to us by Exant and RAYTRAC3R for using accessories to evolve Character Chao:

```cpp

    static bool ScarabEvolve(ObjectMaster* tp)
    {
        Uint16* accessories = (Uint16*)((int)(tp->Data1.Chao->ChaoDataBase_ptr) + 0x614);
        Uint8 eye_color = *(Uint8*)((int)(tp->Data1.Chao->ChaoDataBase_ptr) + 0x59A);

        if (eye_color == 7 && accessories[Face] == (ScarabMaskID + 1))
        {
            //PrintDebug("Chao evolving into Scarab");
            return true;
        }
        else
            return false;
    }

```

Let's break it down:

`Uint16* accessories = (Uint16*)((int)(tp->Data1.Chao->ChaoDataBase_ptr) + 0x614);` - This points to the list of Accessory IDs. 

`Uint8 eye_color = *(Uint8*)((int)(tp->Data1.Chao->ChaoDataBase_ptr) + 0x59A);` - This points to the eye color list.

How do we use it in context of an accessory?

Simple. We check for what type and add 1 to the number (the index is offset by 1)

Let's make our own example:

```cpp

static bool ExampleEvolve(ObjectMaster* tp)
{
        Uint16* accessories = (Uint16*)((int)(tp->Data1.Chao->ChaoDataBase_ptr) + 0x614);

        if (accessories[Generic1] == ExampleAccessoryID + 1)
        {
            return true;
        }
}
```

as you can tell, we can utilize `Head`, `Face`, `Generic1` and `Generic2` inside the `accessories` variable we created, and we can find our accessory ID that way, too. We just have to add 1 to the index list otherwise we won't get wht we're looking for.