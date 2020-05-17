# Capabilities
capabilities are basically that, things that a block (or other) can do. For example a blocks inventory is one such thing. 
To add one of these to your block you need to override the method ``getCapability``. And return the capability it asks for. 

Here is an example of an item handler:
```java
private LazyOptional<IItemHandler> handler = LazyOptional.of(this::createHandler);

private IItemHandler createHandler() {
    return new ItemStackHandler(5){
        @Override
        public boolean isItemValid(int slot, @Nonnull ItemStack stack) {
            return true;// stack.getItem() == Items.DIAMOND;
        }

        @Override
        protected void onContentsChanged(int slot)
        {
            super.onContentsChanged(slot);
            markDirty();
            needRefreshRecipe = true;
        }
    };
}

@Nonnull
@Override
public <T> LazyOptional<T> getCapability(@Nonnull Capability<T> cap, @Nullable Direction side) {
    if (cap == CapabilityItemHandler.ITEM_HANDLER_CAPABILITY) {
        return handler.cast();
    }
    return super.getCapability(cap, side);
}
```

