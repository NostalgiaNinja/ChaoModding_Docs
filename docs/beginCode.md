# Tips for beginners: Code

Most of the code is given in a sample format. While people can try to help you with the sample code, sometimes a little more of an experienced hand is needed.

It would be recommended you at least understand up to Pointers and References in C++ for these guides. It would eliminate as many headaches that come from asking for help.

## Tip 1: Following structs

At any time if you see a green colored word (Usually a struct or a datatype), you can ++ctrl+left-button++ click on it to follow where it takes you. Let's take an example:

```cpp
static bool ExampleChaoEvolve(ObjectMaster* tp)
```

Here, we see `ObjectMaster*` is a struct datatype. Let's ++ctrl+left-button++ click that.

Now you get taken to `SA2Structs.h` with the `ObjectMaster` struct highlighted. There's a lot of information here that can be confusing at first. Let's focus on `Data1Ptr`. ++ctrl+left-button++ click on that.

It now takes us to the `Data1Ptr` declaration. Interestingly, we see `ChaoData1`. Let's ++ctrl+left-button++ click that.

Now we're inside the Chao Data structure. Here we can see some interesting keywords like `ChaoDataBase`. Let's ++ctrl+left-button++ click that.

now we're inside ChaoDataBase. This contains everything from your pips on a level for Chao, the Type of Chao, Which garden it is, if it's in the Kindergarten, etc. Here is where you can modify your Chao in code (useful for Fruit, or requirements for evolving a Character Chao).

## Tip 2: Following the examples

If you're having trouble with creating a mod, check the example project on Github [here](examples.md). The examples are somewhat documented and give you an insight of where to place things. The example projects should give you a baseline structure of how a mod gets made.

## Tip 3: Debug your code

If you're unsure where your code lands, place a `PrintDebug()` function down where you are thinking the code will land. If it lands there, then you know that area of code executes. If not, you can diagnose what issues you are running into. You can also use Visual Studio's debugger (you'll have to set that up first) to debug what's going on with your code.

## Tip 4: Leave comments

While you're writing your code, make sure to leave comments. This helps you find something in case you're stuck for later. Simply use `//` to start a comment block. If you want a multi-line comment block, use `/*` and `*/` respectively to open and close the comment block.