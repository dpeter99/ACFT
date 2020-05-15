# Object Holders
Object holders are special java classes that hold references to registry entries. They help with finding references to your (or other) mods blocks, items etc.

To make one just create a class the usual way and add the annotations like this:
```java
@ObjectHolder("our_mod")
public class MyBlocks {

    //the propery has to have the same name as the registry entry
    public static final Block our_block = null;

    public static final Block my_machine = null;

}
```
Here we store a reference to two blocks ``our_block`` and ``my_machine``. We can use these anytime after they are registered.
```java
MyBlocks.our_block
```