# Screens
Screens are the actual GUIs that get displayed, for blocks they get their data form the associated  [Container](../blocks/tile_entities/capabilities.md)

When the Screen is associated with a container than you should extend the ``ContainerScreen<MyContainer>`` class.

They have the following properties that help with drawing:
 - ``width`` ``height`` are the size of the canvas on witch we will draw. This is the scaled size of the full window MC is using.
In ``ContainerScreen`` we use the extra
 - ``xSize`` and ``ySize`` witch we set them to the size of the GUI we want to draw (e.g. if you have a 200x200 gui you set these to 200, 200)


For drawing the screen we use the ``blit`` function of the ``AbstractGui`` witch is in the inheritance tree of ``ContainerScreen``. The ``blit`` function has many overrides:
 - ``public void blit(int x0, int y0, int u0, int v0, int width, int height)``
    
    This is used when your texture is exactly 256x256. The first 2 inputs are the destination position on the window. The next 2 are the top left corner of the source. The last 2 are the bottom left corner.
 - ``public static void blit(int x0, int y0, int z, float u0, float v0, int width, int height, int textureHeight, int textureWidth)``

    This version is used when you have a different sized source image. The first 2 are the same as the last case. The ``z`` should be ``this.blitOffset``. The ``u0`` ``v0`` are the top left of the source coordinates. The ``width`` and ``height`` are the size of the source. And at last the size of the source image;
