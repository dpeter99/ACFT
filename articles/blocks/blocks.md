# Blocks
The base of what the game is made out of. So we might want to add out own. Let's see how!

## Making the actual block class

To make the actual class for a block all you need to do is make a new class (is is best practice to place it under a ``blocks`` folder) and make it inherit from ``Block``
So the first line would look something like this:
```java
public class OurNewBlock extends Block {
```
With this the editor will tell you that you have errors. We need to make a constructor as well:
```java
public OurNewBlock() {
    super(Properties.create(Material.IRON)
    .notSolid());
}
```

Now we are almost there just need to set the registry name for it. The registry name is what MC uses to internally identify anything. It is a string that must be unique in the type group but not globally. So we can have ``grass`` as an item and ``grass`` as a block.

Now the registry name can be set in 2 places and some will tell you to set it at one place and others to use the other....

Both of these are fully valid I think.

### Option 1
In this case we set it in the class constructor.
```java
public OurNewBlock() {
    super(Properties.create(Material.IRON)
    .notSolid());

    setRegistryName("our_block");
}
```

### Option 2
In this case we set it on the master copy just before putting it in the registry see the Registry part below.
```java
@SubscribeEvent
public static void onBlocksRegistry(final RegistryEvent.Register<Block> blockRegistryEvent) {
    // register a new block here
    LOGGER.info("HELLO from Register Block");

    IForgeRegistry<Block> reg = blockRegistryEvent.getRegistry();

    reg.register(new OurNewBlock().setRegistryName("our_block"));
}
```

## Registering
To register a block you need to use the registry event for them. It is one of the simplest ones so let's see it:
```java
@SubscribeEvent
public static void onBlocksRegistry(final RegistryEvent.Register<Block> blockRegistryEvent) {
    // register a new block here
    LOGGER.info("HELLO from Register Block");

    IForgeRegistry<Block> reg = blockRegistryEvent.getRegistry();

    reg.register(new OurNewBlock());
}
```

You can see that we have a function, with the ``@SubscribeEvent`` annotation as with all the registry events. We specify that we want to register Blocks by giving the function a ``RegistryEvent.Register<Block>`` input (we can name the parameter whatever we want).
In the function we can do what we want, here we do a little debug print. This way we can see in what order the functions get called.

Next we register the block so Mc knows about it. This is done by just getting the registry from the input variable, and calling ``register`` on it. We can just pass it a new instance of the block.
