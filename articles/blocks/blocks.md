# Blocks
The base of what the game is made out of. So we might want to add out own. Let's see how!

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

You can see that we have a function, with the ``@SubscribeEvent`` anotation as with all the registry events. We specify that we want to register Blocks by giving the function a ``RegistryEvent.Register<Block>`` input (we can name the parameter whatever we want).
In the function we can do what we want, here we do a little debug print. This way we can see in what order the functions get called.

Next we register the block so Mc knows about it. This is done by just getting the registry from the input variable, and calling ``register`` on it. We can just pass it a new instance of the block.

## Making the actual block class