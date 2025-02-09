---
slug: /leaves/configuration
toc_max_heading_level: 4
keywords:
  - leaves.yml
  - leaves.yml settings
---

# Leaves配置

所有Leaves配置都存于 `leaves.yml` 文件内。

:::tip

部分配置可能覆盖上游服务端的配置（比如paper.yml）。

:::

## settings

:::tip

此节点下的配置会作用于所有世界或更改服务器本身的功能。

:::

### misc

#### extra-yggdrasil-service.enable

- **默认值**: `false`
- **简介**: 是否启用非官方的 [外置登录](https://github.com/yushijinhun/authlib-injector) 支持。
 
:::caution

这是一个测试功能且为非官方实现，使用此功能可能会导致未知的错误。

:::
 
#### extra-yggdrasil-service.urls

- **默认值**: 
	- 'https://url.with.authlib-injector-yggdrasil'
- **简介**: 外置登录服务器的连接，链接最后应不加 `/` 。

#### no-chat-sign

- **默认值**: `true`
- **简介**: 是否删除玩家聊天内的签名来保护玩家聊天。如果开启此选项，服务器也会向安装了NoChatReport的玩家发送此服务器安全的信息。

#### disable-method-profiler

- **默认值**: `true`
- **简介**: 是否禁用方法检查器。这可能会对测试造成一定影响，但不影响生产环境的使用并可以获得一定的性能提升。

### modify

#### return-nether-portal-fix

- **默认值**: `false`
- **简介**: 可以修复玩家从地狱返回主世界时串门的问题。

:::caution

此功能是一个实验性功能，它不一定可以正常工作。

:::

#### snowball-and-egg-can-knockback-player

- **默认值**: `true`
- **简介**: 雪球和鸡蛋是否可以击退玩家。

#### mc-technical-survival-mode

- **默认值**: `true`
- **简介**: 是否启用生电模式。此模式下，以下配置会被强制覆盖来修复各种被影响的生电机制。
    - paper-global.yml unsupported-settings.allow-headless-pistons: true
    - paper-global.yml unsupported-settings.allow-grindstone-overstacking: true
    - paper-global.yml allow-permanent-block-break-exploits: true
    - paper-global.yml allow-piston-duplication: true
    - paper-global.yml packet-limiter.all-packets.max-packet-rate: 5000.0
    - paper-global.yml packet-limiter.overrides: Empty
    - paper-world.yml entities.spawning.count-all-mobs-for-spawning: true
    - paper-world.yml unsupported-settings.fix-invulnerable-end-crystal-exploit: false
    - paper-world.yml fixes.fix-curing-zombie-villager-discount-exploit: false
    - spigot.yml world-settings.max-tnt-per-tick: 2000

:::note

如果你发现了更多需要被覆盖的配置，欢迎提出issue。

:::

#### instant-block-updater-reintroduced

- **默认值**: `false`
- **简介**: 是否重新引入1.19前的瞬时方块更新机制，这会让更新抑制重新可用。

#### flatten-triangular-distribution

- **默认值**: `false`
- **简介**: 是否将Minecraft中的随机数发生器从三角分布改为平均分布，这会使得边缘事件更可能发生。

#### redstone-shears-wrench

- **默认值**: `true`
- **简介**: 剪刀是否可以右键来旋转部分红石元件。（如果你需要旋转更多红石元件，请发issue提出）

#### player-operation-limiter

- **默认值**: `false`
- **简介**: 每gt每个玩家只能秒破1个或放置2个方块，这可以对抗自动破基岩mod并且不会影响正常的破基岩。

#### use-vanilla-random

- **默认值**: `false`
- **简介**: 是否使用原版的随机数，这可能会丢失一些性能，但会让RNG控制可以在服务器内使用。

#### no-feather-falling-trample

- **默认值**: `false`
- **简介**: 靴子上附魔“摔落缓冲”时在耕地上跳跃不会导致耕地退化。

#### renewable-elytra

- **默认值**: `-1.0`
- **简介**: 当潜影贝杀死幻翼时掉落破损的鞘翅的概率，如值为负则禁用此功能。

#### shears-in-dispenser-can-zero-amount

- **默认值**: `false`
- **简介**: 剪刀在发射器内是否可以被使用到负耐久并且不会损坏。

:::note

这是一个老版本Minecraft的bug。

:::

#### fix-update-suppression-crash

- **默认值**: `true`
- **简介**: 是否修复更新抑制造成的崩溃。

#### disable-distance-check-for-use-item

- **默认值**: `false`
- **简介**: 是否禁用对方块使用物品的距离检测，如果你无法破基岩，开启此选项可能有一定帮助。

#### spectator-dont-get-advancement

- **默认值**: `false`
- **简介**: 观察者模式的玩家是否不会获得进度。

#### budding-amethyst-can-push-by-piston

- **默认值**: `false`
- **简介**: 活塞是否可以**推动**紫水晶母岩。

#### stick-change-armorstand-arm-status

- **默认值**: `true`
- **简介**: 玩家是否在下蹲时可以使用木棍右键盔甲架来改变盔甲架手臂的显示状态。

#### stackable-shulker-boxes

- **默认值**: `'false'`
- **简介**: 是否启用空潜影盒堆叠功能。此项值必须为一个字符串并为 `true` / `false` 或一个64及以下的整数。
 如值为一个整数，则为空潜影盒的可堆叠数量，如为 `true` 则视为 `2`，如为 `false` 则视为1。

:::note

空潜影盒会在地上和被玩家捡起时自动堆叠，如果玩家安装了支持的mod则也可以在背包内手动堆叠。
但为了不破坏机器，空潜影盒不会在漏斗内被堆叠，并且堆叠的空潜影盒会在漏斗运行时被分开。

:::

#### shared-villager-discounts

- **默认值**: `false`
- **简介**: 玩家是否共享在同一个村民的折扣。

#### bedrock-break-list

- **默认值**: `false`
- **简介**: 是否启用破基岩榜，此功能的行为和此 [mod](https://gitee.com/harvey-husky/YH-BBL) 一致。

#### fakeplayer.enable

- **默认值**: `true`
- **简介**: 是否启用假人功能和 `/bot` 指令。

#### fakeplayer.unable-fakeplayer-names

- **默认值**:
	- player-name
- **简介**: 假人禁止使用的名称列表。

#### fakeplayer.limit

- **默认值**: `10`
- **简介**: 假人的数量限制。（假人同时会计算到玩家数量中）

#### fakeplayer.always-send-data

- **默认值**: `true`
- **简介**: 是否无视距离始终向同世界的玩家发送假人数据。
 
#### fakeplayer.resident-fakeplayer

- **默认值**: `false`
- **简介**: 是否在关闭服务器后保存假人数据并在开启服务器后自动重新生成假人。
 
:::caution

这是一个实验性功能，并且假人的动作暂时不会被保存。

:::

#### fakeplayer.open-fakeplayer-inventory

- **默认值**: `false`
- **简介**: 是否可以空手右键假人来打开假人背包。

#### fakeplayer.skip-sleep-check

- **默认值**: `false`
- **简介**: 是否让假人不计入睡眠计数。

#### redstone-wire-dont-connect-if-on-trapdoor

- **默认值**: `false`
- **简介**: 是否让红石粉不再连接到活板门上，这可以恢复1.20前的简易更新抑制。

#### disable-check-out-of-order-command

- **默认值**: `false`
- **简介**: 是否禁用聊天信息顺序检查，这可以修复使用Velocity作为上游代理时粘贴原理图失败的问题。

#### despawn-enderman-with-block

- **默认值**: `false`
- **简介**: 是否让手中有方块的末影人会被刷新，这可以消除服务器里一堆刷不掉的末影人。

#### creative-no-clip

- **默认值**: `false`
- **简介**: 是否让玩家在创造飞行时没有碰撞箱。

:::note

此功能需要启用leaves-carpet-support并且需要玩家安装carpet才可正常使用。

:::

#### mending-compatibility-infinity

- **默认值**: `false`
- **简介**: 使得经验修补和无限可以重叠。

#### shave-snow-layers

- **默认值**: `true`
- **简介**: 使得雪片可以被铲子一层层铲。

#### ignore-lc

- **默认值**: `false`
- **简介**: 使生物生成无视lc值进行。

:::caution

此功能是一个实验性功能，它不一定可以正常工作。

:::

#### elytra-aeronautics.no-chunk-load

- **默认值**: `false`
- **简介**: 使玩家在一定高度和一定速度时鞘翅飞行不加载区块也不进行世界生成，以此减少服务器负荷。

:::caution

此功能是一个实验性功能，它不一定可以正常工作。

:::

#### elytra-aeronautics.no-chunk-height

- **默认值**: `500.0`
- **简介**: 玩家进入不加载区块状态时飞行需要的高度。

#### elytra-aeronautics.no-chunk-speed

- **默认值**: `-1.0`
- **简介**: 玩家进入不加载区块状态时飞行需要的速度。

#### elytra-aeronautics.message

- **默认值**: `true`
- **简介**: 是否在玩家进入和退出不加载区块状态时进行提示。

#### elytra-aeronautics.message-start

- **默认值**: `Flight enter cruise mode`
- **简介**: 玩家进入不加载区块状态时的提升。

#### elytra-aeronautics.message-end

- **默认值**: `Flight exit cruise mode`
- **简介**: 玩家退出不加载区块状态时的提升。。

### performance

#### cache-climb-check

- **默认值**: `true`
- **简介**: 将缓存攀爬检查结果。

#### entity-target-find-optimization

- **默认值**: `true`
- **简介**: 在实体寻找目标时，如果找不到目标则直接停止寻找，可以减少一些冗余运算。

#### check-spooky-season-once-an-hour

- **默认值**: `true`
- **简介**: 每小时检测一次万圣节（检测那么频繁干什么）。

#### reduce-chuck-load-and-lookup

- **默认值**: `true`
- **简介**: 减少了没有必要的区块查找和加载。

#### optimize-chunk-ticking

- **默认值**: `true`
- **简介**: 优化了以下的区块刻，可以提高5%到10%的性能。
	- 闪电
	- 冰和雪的生成

#### remove.tick-guard-lambda

- **默认值**: `true`
- **简介**: 删除lambda表达式来提高性能。

#### remove.get-nearby-players-streams

- **默认值**: `true`
- **简介**: 删除流来提高性能。

#### remove.inventory-contains-iterators

- **默认值**: `true`
- **简介**: 删除选择器来提高性能。

#### remove.range-check-streams-and-iterators

- **默认值**: `true`
- **简介**: 删除流和选择器来提高性能。

#### reduce-entity-fluid-lookup

- **默认值**: `true`
- **简介**: 如果实体附近根本没有流体，则禁用低效率的流体查找。

#### enable-suffocation-optimization

- **默认值**: `true`
- **简介**: 每隔20tick才检查一次窒息，玩家很难（但不是不可能）注意到这一变化。

#### strip-raytracing-for-entity

- **默认值**: `true`
- **简介**: 旧rayTrace方法十分浪费性能的在不需要流体碰撞计算的时候依然计算，我们修复了这个问题。

#### inactive-goal-selector-disable

- **默认值**: `false`
- **简介**: 在非活动的实体上限制实体目标查找器的运行。这可以提高一些性能并对游戏影响较小。

#### improve-fluid-direction-caching

- **默认值**: `true`
- **简介**: 重新实现了FluidTypeFlowing的缓存系统，并使其性能更高。

#### fix.fix-paper-6045

- **默认值**: `true`
- **简介**: 修复了一个Paper的bug。

#### dont-send-useless-entity-packets

- **默认值**: `true`
- **简介**: 减少根本没用的一些实体包的发送。（这可能会破坏一些利用这些无用实体包的mod）

#### optimize-entity-coordinate-key

- **默认值**: `true`
- **简介**: 当为实体（热路径）执行getCoordinateKey时，JVM需要重复将double转换为long。
 这对性能的影响取决于CPU架构，但通常在FPU和ALU之间切换会导致严重的性能损失。
 blockPosition结构中已提供了已转换/舍入的数据，因此我们使用该数据而不是重新进行转换。

#### use-more-thread-unsafe-random

- **默认值**: `true`
- **简介**: 使用更多线程不安全的随机数发生器，它们虽然不安全，但是运行快。

#### skip-poi-find-in-vehicle

- **默认值**: `true`
- **简介**: 跳过在载具内村民的poi计算，这对密集的村民交易大厅的优化十分明显。

#### simpler-vanilla-shapeless-recipes

- **默认值**: `true`
- **简介**: 替换掉过于复杂的无序配方系统。

#### reduce-entity-allocations

- **默认值**: `true`
- **简介**: 减少对实体的分配。

#### biome-temperatures-use-aging-cache

- **默认值**: `true`
- **简介**: 使用了更好的生态群落温度缓存。

#### async-pathfinding

:::danger

此功能暂时不可用。

:::

- **默认值**: `false`
- **简介**: 异步化的实体寻路。

#### async-entity-tracker

:::danger

此功能暂时不可用。

:::

- **默认值**: `false`
- **简介**: 异步化的实体追踪。

#### async-mob-spawning

:::danger

此功能暂时不可用。

:::

- **默认值**: `false`
- **简介**: 它的目的是通过将尽可能多的工作卸载到其他线程来减少实体生成对主线程的影响。
可能会出现生成不一致的情况，但当问题发生时并不会出现错误，只会造成在任何特定的时间点产生的实体或多或少的问题。

:::caution

如果不想干扰任何生成机制，则可禁用此功能。但是此功能在拥有上千实体的服务器上可以带来足足15%的性能提升。
在我看来，为了这些性能提升而承担较小的实体生成不一致的风险是非常值得的。

:::

#### optimized-dragon-respawn

- **默认值**: `false`
- **简介**: 是否对龙战进行优化。

:::caution

此功能和原版表现不完全一致。

:::

### protocol

#### carpet-alternative-block-placement

- **默认值**: `false`
- **简介**: 是否是否支持carpet的精确放置协议。

:::tip

如果想在投影模组的轻松放置功能上使用精确放置协议，你需要手动调整投影模组使用的协议类型为 `V2` 而不能使用 `Auto` 模式。

:::

#### pca-sync-protocol

- **默认值**: `false`
- **简介**: 是否支持 [pca数据同步协议](https://github.com/plusls/plusls-carpet-addition)。

#### syncmatica.enable

- **默认值**: `false`
- **简介**: 是否开启对 [Syncmatica](https://github.com/End-Tech/syncmatica) 的支持来共享原理图。
 
#### syncmatica.quota

- **默认值**: `false`
- **简介**: 是否限制玩家可上传原理图的最大大小。

#### syncmatica.quota-limit

- **默认值**: `40000000`
- **简介**: 玩家可上传原理图的最大大小，单位为byte。

#### jade-protocol

- **默认值**: `false`
- **简介**: 是否开启对 [Jade](https://github.com/Snownee/Jade) 的支持，开启后Jade可以显示更多信息。

#### bbor-protocol

- **默认值**: `false`
- **简介**: 是否开启对 [BBOR](https://github.com/irtimaled/BoundingBoxOutlineReloaded) 的支持。

#### pca-sync-player-entity

- **默认值**: `OPS`
- **简介**: 控制pca同步协议可以同步的玩家。
    - `NOBODY`: 任何玩家数据都不能被同步。
    - `BOT`: 假人的数据可以被同步。
    - `OPS`: 假人的数据可以被同步，OP可以同步所有玩家的数据。
    - `OPS_AND_SELF`: 假人的数据可以被同步，OP可以同步所有玩家的数据，同时玩家可以同步自己的数据。
    - `EVERYONE`: 所有玩家数据都可以被同步。

#### appleskin-protocol

- **默认值**: `false`
- **简介**: 是否开启对 [AppleSkin](https://github.com/squeek502/AppleSkin) 的支持来显示饥饿值和饱和度。

#### xaero-map-protocol
 
- **默认值**: `false`
- **简介**: 是否开启对 [Xaero's World Map](https://minecraft.curseforge.com/projects/xaeros-world-map) 和
 [Xaero's Minimap](https://www.curseforge.com/minecraft/mc-mods/xaeros-minimap) 的支持来自动在服务器间切换地图。

#### leaves-carpet-support

 - **默认值**: `false`
 - **简介**: 是否启用由Leaves实现的carpet协议，这可以让客户端认为自己进入了一个带有carpet的服务器并提供一些客户端支持。
