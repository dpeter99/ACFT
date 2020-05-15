# Tile Entities
Tile entities are a complex topic. But at the core they are blocks witch have more complex data in them, or business logic. They are used for chest and machines.
Tile entities add to the base block, meaning for example a machine would have 2 classes a ``MyMachineBlock`` inheriting form ``Block`` and a ``MyMachineTileEntity`` inheriting from ``TileEntity``. To link the two classes together we need to make a instance of the tile entity when the block is placed.


## Step 1. Creating the class
To make a Tile Entity you need to create a class that inherits form ``TileEntity`` so something like this:
```java
public class MyMachineTileEntity extends TileEntity{
    
    public MyMachineTileEntity() {
        super(ArcaneTileEntities.witch_altar);
    }
}
```

Now we just need to register it

## Step 2. Registration
You register your block class that we will be using for this Tile Entity like usual, so for that take a look here [Block registration](../blocks.md#registering)

To register your Tile Entity class you need to use the register callback function for the tile entity registry event:
```java
@SubscribeEvent
public static void onTileRegistry(final RegistryEvent.Register<TileEntityType<?>> itemRegistryEvent){
    //Get the registry form the event data
    IForgeRegistry<TileEntityType<?>> reg = itemRegistryEvent.getRegistry();

    reg.register(TileEntityType.Builder.create(MyMachineTileEntity::new, MyBlocks.my_machine).build(null).setRegistryName("my_machine"));
}
```

Here you can see we make the usual function with the ``@SubscribeEvent`` annotation. And we get the registry out of the parameters. Than we call the register function but this time we can't just pass in a instance of the tile entity. We need to use a Type builder, it needs as input out Tile Entity, and the block it is connected to. To get our block we use an (ObjectHolder)[../../objectHolders.md] class. We also set the registry name of the tile entity, it can be the same as the blocks (and should be for ease of understanding) as they are in separate registries (Block is in the blocks list, Tile Entity is in the tile entity list).

## Step 3. Creating the tile entity when placing the block
In the block we need to create an instance of the ``MyMachineTileEntity`` and place it in the correct position so we need to add the following code:
```java
//Telling MC that we do have TE
@Override
public boolean hasTileEntity(BlockState state) {
    return true;
}

@Nullable
@Override
public TileEntity createTileEntity(BlockState state, IBlockReader world) {
    return new WitchAltarTileEntity();
}
```