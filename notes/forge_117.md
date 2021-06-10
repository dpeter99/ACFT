For anyone asking for 1.17 forge here is the rundown of the process that goes into updating it.

> [!WARNING]
> Currently step 1 is being worked on. This can take a few days.

- [x] step 0: have vanilla decompiling and compiling again without forge on top. This is needed because the decompiling is not perfect.
- [currently] step 1: have forge compiling, this means that all the code modifications that forge adds still produce a compiling code. This process often requires disabling patches/features temporarily
- [ ] step 2: once forge compiles and the initial set of patches can be produced, then forge can start to be properly developed, until it's in an usable state enough to actually use. In this phase we make sure that none of the forge extra code parts break the original functionality.
- [ ] step 3: fix all the missing features (that make sense to fix), cleanup, add new hooks, etc. This is the longest part as people have to figure out what mojang did and how to expose it to the modders in a safe way-- this will take some weeks, and result in the recommended build

Most of this takes a long time and people are doing it in their free time so be patient and don't ask them.
If everything goesright the first forge version will hopefully not take longer than a few weeks. But this doesn't mean that mods will be updated as well. Mods (just as forge) are made by people in their free time for free, and real life should and always will be the priority.