### 简要介绍
- 原仓库为[这个](https://github.com/j-shelfwood/voxy-neoforge)，为voxy的Neoforge 1.21.1非官方移植版，我只是将其构建成了.jar
- 目前游戏内运行`/voxy import world "xxx"`会类似报错：
  > [me.cx.vy.cl.is.WorldImporter]: Exception importing world chunk: java.lang.NullPointerException: Cannot invoke "com.mojang.serialization.Codec.parse(com.mojang.serialization.DynamicOps, Object)" because "this.blockStateCodec" is null
  
  ，原因为（WorldImporter.java）:
  ```
    // MC 1.21.1: PalettedContainerFactory removed - need to find correct codec creation API
    // TODO: Fix codec creation for PalettedContainer in MC 1.21.1
    this.biomeCodec = null; // Placeholder
    this.blockStateCodec = null; // Placeholder
  ```