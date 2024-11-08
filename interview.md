# 面试总结
### 一般游戏中使用的状态同步方式？
> ARPG游戏通常使用多种同步方式来确保玩家之间的游戏状态保持一致。具体来说，它们可能结合了客户端/服务器（C/S）同步方式和帧同步方式。(状态同步和帧同步)
1. 在C/S同步方式中，服务器负责实现整套游戏逻辑，客户端则主要负责用户输入和渲染。这种方式具有较高的安全性，因为所有的计算都在服务器上完成，客户端的逻辑运算压力相对较低。同时，客户端可以进行一些预处理内容，从而提高游戏的即时性。
2. 而帧同步方式则依赖于一个用于同步的服务器（如FrameServer），它负责收集各个客户端上报的输入，并在同步帧到来时进行结算。这种方式可以确保所有客户端在同一时间看到相同的游戏状态，从而实现更精确的游戏同步。

需要注意的是，ARPG游戏在选择同步方式时，会根据游戏类型、技术条件以及具体需求进行权衡。有时候，为了保证游戏的一致性和流畅性，可能会采用多种同步方式的结合。
***
### 如果让你写一个 MMORPG 类型的游戏你会怎么做？
***
### 游戏中发版本有没有了解具体流程？
老康的回答：其实就是把代码压缩混淆，带上版本号，资源压缩带上版本号，提交cdn，后续就是前后端同步版本号
然后再在那个微信小程序工具上上传代码资源
***
### 工作中遇到的一些问题，或者说一说工作中完成了什么事情让你觉得很有成就感？
1. 在资源加载这一块，因为引擎内部没有关于资源加载优先级的这种做法，但是游戏中有一个这种的需求  需要进去游戏后先看到某一部分资源后看到某一部分资源。所以对这个问题  的解决方案是自己封装了一套关于资源加载优先级的工具。
2. 发现游戏中定时器的准确度问题。发现在游戏中嵌套的层数过多会导致有误差。
了解发现：
- 计算机没有原子钟，无法精准计时。
- 操作系统的计时函数本身就是有误差的，由于js本身就是调用的系统的计时函数，所以就携带了一定的误差。
- 按照w3c的标准，浏览器实现计时器的时候，如果嵌套层数超过了5层，则会带有四秒钟的最少时间的误差。所以在计时少于4毫秒的时候也会带有误差。
- 受事件循环的影响，计时器的回调函数会在主线程空闲的时候才会执行。因此也会带有一定的误差。
***
### socket 二进制编码
***
### 设计模式有哪些
>创建型模式：

- 工厂模式（Factory Pattern）
- 抽象工厂模式（Abstract Factory Pattern）
- 单例模式（Singleton Pattern）
- 建造者模式（Builder Pattern）
- 原型模式（Prototype Pattern）
>结构型模式：

- 适配器模式（Adapter Pattern）
- 桥接模式（Bridge Pattern）
- 组合模式（Composite Pattern）
- 装饰器模式（Decorator Pattern）
- 外观模式（Facade Pattern）
- 享元模式（Flyweight Pattern）
- 代理模式（Proxy Pattern）
> 行为型模式：

- 责任链模式（Chain of Responsibility Pattern）
- 命令模式（Command Pattern）
- 解释器模式（Interpreter Pattern）
- 迭代器模式（Iterator Pattern）
- 中介者模式（Mediator Pattern）
- 备忘录模式（Memento Pattern）
- 观察者模式（Observer Pattern）
- 状态模式（State Pattern）
- 策略模式（Strategy Pattern）
- 模板方法模式（Template Method Pattern）
- 访问者模式（Visitor Pattern）
>并发模式：

- 信号量模式（Semaphore Pattern）
- 线程池模式（Thread Pool Pattern）
- 读写锁模式（Read-Write Lock Pattern）
- 并行流模式（Parallel Stream Pattern）
***

### 什么是行为树?

[行为树文档](http://www.aisharing.com/archives/90)

[官方文档](https://www.behaviortree.dev/docs/learn-the-basics/bt_basics/)



行为树（Behavior Tree）是一种用于描述和管理行为的树形结构，常用于编程人工智能（AI）和游戏开发中。它提供了一种直观、灵活且可扩展的方式来描述复杂的行为逻辑，并且易于理解和调试。

行为树由节点组成，节点分为两种类型：行为节点和控制节点。

1. 行为节点：执行实际的动作或任务。这些节点通常是树的叶子节点，它们执行具体的行为，比如移动、攻击、寻找目标等。

2. 控制节点：用于组织和控制行为节点的执行顺序和条件。这些节点通常是树的非叶子节点，它们决定了行为节点的执行方式，比如顺序执行、并行执行、选择执行等。

行为树的构建过程通常包括以下步骤：

1. 定义目标：确定要实现的行为逻辑和目标。

2. 设计树结构：根据目标设计行为树的结构，包括确定树的根节点以及各个子节点之间的关系。

3. 选择节点类型：根据行为的性质选择合适的行为节点和控制节点。

4. 实现节点逻辑：编写每个节点的具体逻辑，包括行为节点的具体行为和控制节点的控制逻辑。

5. 组装树：将所有节点按照设计的结构组装成完整的行为树。

6. 执行行为：启动行为树的执行过程，根据外部环境和条件触发节点的执行。

行为树提供了一种灵活的方式来描述复杂的行为逻辑，使得设计者可以通过简单的组合和调整节点来实现不同的行为策略。它也易于扩展和修改，使得在开发过程中可以快速地进行迭代和调试。因此，行为树在游戏开发、机器人控制等领域得到了广泛的应用。
***
### 一个扇形与矩形碰撞检测
碰撞检测是游戏开发中的一个基本问题，其中扇形与矩形的碰撞检测可以通过几何计算来实现。下面是一个简单的方法来实现这种碰撞检测：

1. 确定扇形与矩形的位置和边界：首先，确定扇形的位置、半径和方向；确定矩形的位置、宽度和高度。

2. 计算扇形的扇形区域：根据扇形的位置、半径和方向，计算扇形的顶点坐标。

3. 检测矩形的碰撞：遍历矩形的四条边，检测扇形的顶点是否在矩形的边界内。如果有任何一个顶点在矩形内，则表示发生了碰撞。
```python
import math

# 碰撞检测函数
def collide_with_rectangle(cx, cy, radius, direction, rect_x, rect_y, rect_width, rect_height):
    # 计算扇形的顶点坐标
    sector_vertices = []
    for angle in range(direction - 45, direction + 46):
        x = cx + radius * math.cos(math.radians(angle))
        y = cy + radius * math.sin(math.radians(angle))
        sector_vertices.append((x, y))

    # 检测扇形的顶点是否在矩形内
    for vertex in sector_vertices:
        if rect_x <= vertex[0] <= rect_x + rect_width and rect_y <= vertex[1] <= rect_y + rect_height:
            return True

    # 如果扇形的中心点在矩形内，则也认为发生了碰撞
    if rect_x <= cx <= rect_x + rect_width and rect_y <= cy <= rect_y + rect_height:
        return True

    return False

# 测试碰撞检测函数
cx = 100
cy = 100
radius = 50
direction = 45
rect_x = 50
rect_y = 50
rect_width = 100
rect_height = 100

result = collide_with_rectangle(cx, cy, radius, direction, rect_x, rect_y, rect_width, rect_height)
print("是否发生碰撞：", result)

```
***
### 游戏中导表工具的压缩方式，如何优化？
在游戏开发中，导表工具通常用于将游戏中的配置数据（如地图、道具、角色属性等）从表格文件（如 Excel、CSV 等）导入到游戏中。这些表格数据可能会占用大量的存储空间，因此压缩是一种常见的优化方式，可以减少游戏资源的体积，并加快游戏加载速度。以下是一些常见的导表工具压缩方式和优化方法：

- **文本压缩**：对于文本型数据（如 CSV 文件），可以使用通用的文本压缩算法（如 gzip、zlib 等）来压缩数据文件。这些算法通常能够显著减少文件大小，但加载时需要解压缩，可能会增加一些额外的运行时开销。

- **二进制格式**：将表格数据转换为二进制格式，可以进一步减少数据文件的大小。二进制格式可以根据具体的数据结构进行设计，可以更加紧凑和高效地存储数据。加载时无需解析文本，可以提高加载速度。

- **数据压缩策略**：对于游戏中的各种数据类型，可以根据特点采用不同的压缩策略。例如，对于稀疏性较高的数据，可以采用稀疏矩阵压缩技术；对于重复性较高的数据，可以采用字典编码等压缩方法。

- **压缩算法选择***：根据数据类型和压缩效果的需求选择合适的压缩算法。不同的压缩算法有不同的压缩率和解压缩速度，需要根据具体情况进行权衡。

- **增量更新**：在游戏更新时，只更新发生变化的部分数据，而不是整个数据文件。这样可以减少下载量和更新时间。

- **资源合并**：将多个表格文件合并为一个文件，然后进行压缩。这样可以减少文件数量和加载时间。

- **数据预处理**：在导表前对数据进行预处理，如去除冗余数据、优化数据结构等，可以减少最终数据文件的大小。

- **分包加载**：将数据文件分成多个小包，并在需要时按需加载，可以减少单次加载的数据量，降低加载时间和内存占用。

综合考虑以上方法，可以根据具体情况选择合适的压缩方式和优化方法，以提高游戏的性能和用户体验。
***
### 如何优化WebSocket的性能
优化WebSocket的性能可以从多个方面入手，包括网络层面、协议层面以及应用层面。以下是一些建议来优化WebSocket的性能：
>网络层面优化
1. **选择合适的传输协议**：确保WebSocket连接使用的是TCP协议，因为TCP提供了可靠的、面向连接的字节流服务。对于需要实时性较高的应用，可以考虑使用UDP作为底层传输协议，但需要注意UDP不保证数据的可靠传输。
2. **减少连接建立时间**：WebSocket连接建立涉及到HTTP请求和响应的交换。为了减少连接建立时间，可以考虑使用HTTP/2协议，它支持多路复用和头部压缩，能够更快地建立连接。
保持连接稳定：避免频繁地建立和关闭WebSocket连接，因为每次建立连接都需要进行握手过程，会消耗额外的资源和时间。尽量保持连接的稳定，只在必要时进行关闭和重新建立。
选择适当的心跳机制：心跳机制用于检测连接的活跃性。选择合适的心跳间隔和超时时间，以避免因心跳过于频繁而导致的网络拥堵或心跳间隔过长而导致的连接断开。
>协议层面优化
1. **压缩数据**：对发送的数据进行压缩，可以减少网络传输的数据量，从而提高性能。可以使用如gzip或Brotli等压缩算法对数据进行压缩。
使用二进制帧：如果可能的话，尽量使用二进制帧而不是文本帧。二进制帧能够直接传输原始数据，避免了文本编码和解码的开销。
分帧发送大数据：对于较大的数据块，可以考虑将其拆分成多个较小的帧进行发送。这样可以避免一次性发送大量数据导致的网络拥堵或延迟。
2. **优化消息格式**：设计简洁、高效的消息格式，减少消息头部的开销。避免在消息中包含不必要的冗余信息。
>应用层面优化
1. **合并和批量处理消息**：将多个小消息合并成一个较大的消息进行发送，可以减少网络传输的次数和开销。同时，对接收到的消息进行批量处理，也可以提高处理效率。
异步处理：使用异步编程模型来处理WebSocket消息，可以避免阻塞主线程，提高应用的响应性能。
2. **缓存和预加载**：对于需要频繁访问的数据或资源，可以考虑使用缓存机制进行存储和快速访问。同时，对于可以预知的需求，可以提前进行预加载，以减少后续请求的延迟。
限流和防抖：对于高频次发送消息的场景，可以使用限流和防抖机制来限制发送的频率，避免对服务器造成过大的压力。
综上所述，优化WebSocket的性能需要从多个方面综合考虑，包括网络层面的优化、协议层面的优化以及应用层面的优化。根据具体的应用场景和需求，选择适合的优化策略来提高WebSocket的性能。

***
### 字体渲染优化drawcall 
在游戏开发中，字体渲染的优化对于保持流畅的游戏性能和良好的用户体验至关重要。下面是一些优化字体渲染的常见方法：

- **使用合适的字体**：选择适合游戏风格和主题的字体，并确保字体文件的大小合理。较大的字体文件会增加加载时间和内存消耗。

- **字体缓存**：将已经渲染的字体存储在缓存中，以便在需要时直接使用，避免重复渲染相同的文本。这可以减少渲染开销，并提高渲染效率。

- **字体图集**：将字体字符集合并到一个纹理图集中，以减少批处理次数和纹理切换次数。这样可以降低渲染开销和内存占用，并提高渲染性能。

- **距离场景相机**：根据游戏场景中的相机位置和视角，动态地计算字体渲染的优先级和可见性，只渲染可见区域内的字体，避免不必要的渲染。

- **使用位图字体**：对于较小的字体大小和固定的字符集，可以考虑使用位图字体（Bitmap Font），它们通常比矢量字体渲染速度更快。

- **字体预烘焙**：在游戏运行时预先生成字体渲染结果，并将其存储为纹理或图像，然后在游戏中直接使用。这可以减少运行时的渲染开销，但会增加预处理时间和存储空间。

- **使用 GPU 加速**：利用现代图形硬件的 GPU 加速功能来加快字体渲染速度。例如，使用着色器程序（Shader）来实现高效的字体渲染算法，或者使用字体渲染 API（如 DirectWrite、FreeType）的 GPU 加速功能。

- **异步渲染**：将字体渲染任务放到后台线程或异步任务中进行处理，避免阻塞主线程，提高游戏的流畅度和响应性。

综合利用以上优化方法，可以有效提高字体渲染的性能和效率，从而改善游戏的用户体验。但需要根据具体游戏的需求和平台的特性选择合适的优化策略。
***
### 纹理压缩
纹理压缩技术是游戏开发中常用的一种优化手段，用于减少纹理资源的存储空间，加快纹理加载速度，并降低图形处理的带宽和内存消耗。以下是一些常见的纹理压缩技术：

1. **基于颜色的压缩**：

-  DXT 系列压缩算法：如 DXT1、DXT5 等，通过颜色量化和压缩算法来降低纹理的存储空间，常用于游戏开发中。
- ETC（Ericsson Texture Compression）：适用于移动平台的纹理压缩格式，提供了多种压缩模式，如 ETC1、ETC2 等。
- PVRTC（PowerVR Texture Compression）：适用于 PowerVR GPU 的纹理压缩格式，包括 PVRTC1、PVRTC2 等。
2. **基于波形的压缩**：

- ASTC（Adaptive Scalable Texture Compression）：一种适用于各种纹理类型和分辨率的自适应纹理压缩格式，支持灵活的压缩率和压缩质量设置。
- BC7：一种高质量的压缩格式，支持更高的压缩率和更好的图像质量，适用于需要较高图像质量的场景。
3. **基于矢量的压缩**：

- SVG（Scalable Vector Graphics）：一种基于矢量图形的压缩格式，适用于一些需要动态缩放的图像场景，如 UI 元素等。
4. **混合压缩技术**：

- 通过结合不同的压缩算法和策略，如使用多通道压缩、渐进式压缩等方法，可以进一步提高压缩率和图像质量。
5. **压缩预处理**：
- 在纹理压缩前对纹理数据进行预处理，如去除不必要的细节、优化颜色分布等，可以提高压缩效率和质量。
6. **动态压缩**：

- 在运行时根据需要动态地选择合适的压缩格式和质量级别，以适应不同平台和设备的性能和存储需求。

这些纹理压缩技术各有特点，适用于不同的游戏平台和开发需求。开发者需要根据实际情况选择合适的压缩技术，并根据游戏的需求和目标权衡压缩率和图像质量。

***
### 如何优化场景中的drawcall？
在游戏场景中优化 draw call（绘制调用）是非常重要的，因为 draw call 的数量直接影响到游戏的性能。以下是一些优化游戏场景中 draw call 的常见方法：

1. **合批处理（Batching）**：

- 将多个游戏对象的绘制操作合并成一个 draw call，减少绘制次数。例如，将相邻的静态物体合并到一个网格中，或者将使用相同材质的物体合并到一个批次中。
使用 Unity 等游戏引擎提供的静态合并工具（Static Batching）和动态合并工具（Dynamic Batching）来自动合并游戏对象，或者手动将多个对象合并为一个预制件。
2. **纹理集合并（Texture Atlasing）**：

- 将多个小纹理合并成一个大纹理集（Texture Atlas），减少纹理切换和材质切换的开销。
对于使用相同纹理的游戏对象，尽量将它们放在同一张纹理上，以减少 draw call 的数量。
3. **LOD（Level of Detail）**：

- 使用不同层次的细节模型（LOD）来降低远处物体的细节级别，减少远处物体的绘制次数。
在远处使用更简化的模型和材质，减少细节，提高性能。
4. **遮挡剔除（Occlusion Culling）**：

- 使用遮挡剔除技术来识别和剔除不可见的物体，减少不必要的绘制操作。
通过静态遮挡剔除（Static Occlusion Culling）和动态遮挡剔除（Dynamic Occlusion Culling）来提高场景的渲染效率。
5. **GPU Instancing**：

- 使用 GPU 实例化（GPU Instancing）来实现对相同网格和材质的多个实例的批处理渲染，减少绘制调用次数。
在 Unity 中，可以通过将物体设置为 GPU Instancing 来利用这个功能。
6. **使用批处理和 Mesh Combine**：

- 在代码层面上，使用批处理技术和 Mesh Combine 等工具来手动合并网格和材质，以减少 draw call 的数量。
7. **减少透明物体**：

- 透明物体会增加渲染顺序的复杂度，因此尽量减少透明物体的使用，或者将它们分组渲染以减少排序开销。
8. **减少 UI 渲染**：

- 对 UI 元素进行合批处理，将多个 UI 元素合并成一个 draw call。

通过综合运用以上方法，可以有效地优化游戏场景中的 draw call，提高游戏的性能和流畅度。

***
### 内存优化：

[内存优化](https://www.layaair.com/3.x/doc/2D/performanceOptimization/readme.html)



### laya 的动态合批

LayaAir 引擎提供了动态合批（Dynamic Batching）功能，可以将多个相似的游戏对象动态地合并为一个批次，从而减少 draw call 的数量，提高游戏性能。以下是使用 LayaAir 引擎实现动态合批的基本步骤：

1. 启用动态合批：在 LayaAir 引擎中，默认情况下动态合批是关闭的，需要手动启用。可以通过设置 laya.d3.core.RenderableSprite3D 类的 enableBatching 属性来启用动态合批功能。例如：
``` javascript
Copy code
// 启用动态合批
laya.d3.core.RenderableSprite3D.enableBatching = true;
```

2. 创建游戏对象：创建多个相似的游戏对象，例如使用相同的网格和材质。

3. 添加到场景中：将这些游戏对象添加到场景中。

4. 自动合并：当启用了动态合批功能后，LayaAir 引擎会自动将相似的游戏对象合并为一个批次，从而减少 draw call 的数量。

需要注意的是，动态合批功能是基于渲染器的材质和网格进行合并的，因此要确保需要合并的游戏对象使用了相同的材质和网格。此外，动态合批功能对于每一帧的渲染开销是较高的，因此不适用于所有场景。在实际使用中，可以根据游戏场景的具体情况进行合适的调整和优化。

总的来说，LayaAir 引擎的动态合批功能可以帮助开发者有效地减少 draw call 的数量，提高游戏性能，但需要根据实际情况进行合适的配置和调整。

***
### 如何判断游戏物体是否在摄像机视线范围内？
在游戏中，判断物体是否已经在摄像机视线之外通常涉及摄像机的视野范围与物体的位置关系。这可以通过以下几种方法来实现：
1. **视锥体检测**：
摄像机的视野可以看作是一个视锥体。当物体的位置不在这个视锥体内时，我们就可以认为它在摄像机的视线之外。这通常涉及到计算物体与摄像机之间的距离，以及物体相对于摄像机视锥体的角度。
2. **边界盒检测**：
对于每一个物体，我们可以使用一个边界盒（如AABB，Axis-Aligned Bounding Box）来代表它的空间位置。然后，我们检查这个边界盒是否完全在摄像机的视锥体之外。如果边界盒的任何部分在视锥体内部，那么物体就可能在摄像机的视线内。
3. **射线检测**：
对于更精细的控制，我们可以使用射线检测。从摄像机的位置出发，向物体的中心发射一条射线。如果这条射线与任何物体的边界相交，那么物体就在视线内。否则，它可能在视线之外。
4. **渲染状态检查**：
在某些情况下，我们可以通过检查物体的渲染状态来判断它是否在视线内。例如，如果物体没有被渲染（可能是因为它在视锥体之外），那么我们可以认为它在视线之外。然而，这种方法可能不如直接的空间检测准确，并且它依赖于渲染系统的具体实现。
5. **使用游戏引擎的内置功能**：
许多游戏引擎（如Unity、Unreal Engine等）都提供了内置的函数或组件来检查物体是否在摄像机的视线内。这些功能通常基于上述原理之一，但进行了优化和封装，使得开发者可以更方便地使用。
6. **自定义脚本或算法**：
根据游戏的具体需求和优化目标，开发者还可以编写自定义的脚本或算法来判断物体是否在视线内。这可能涉及到更复杂的数学计算和物理模拟。

需要注意的是，判断物体是否在视线内是一个相对的概念。
***

## 广州暗星科技有限公司
### ES6的新特性
ES6特性过多，这里直接贴链接[ES6新特性知乎](https://zhuanlan.zhihu.com/p/235025429)
### A\*寻路算法
[A星寻路算法介绍](https://www.cnblogs.com/zhoug2020/p/3468167.html)
### 常用的场景优化算法
### 游戏使用的同步方式
### 上家公司(邦邦)项目战斗系统实现方式
### 如何自己组装Draw Call的数据结构实现自定义合批

## 广州匠心科技有限公司
### 谈谈为什么使用Neovim和如何实现代码提示，诊断和补全
### 粗略讲讲渲染管线
https://github.com/Lafree317/Unity-InterviewQuestion/blob/master/图形学.md

1. ‌**顶点着色器**‌：处理模型数据，进行坐标转换和光照计算。
2. ‌**几何处理**‌：对图元进行操作，包括顶点着色器和曲面细分着色器。
3. ‌**裁剪**‌：确保只有相机可视范围内的物体进入下一阶段。
4. ‌**屏幕映射**‌：根据视口大小将点映射到屏幕上。
5. **光栅化**‌：生成像素并应用片元着色器。
6. **逐片元操作**‌：决定可见性和颜色合并。

### Protocol协议压缩原理
Protobuf 在将数据转换成二进制时，会对字段和类型重新编码，减少空间占用。它采用 TLV 格式来存储编码后的数据。TLV 也是就是 Tag-Length-Value ，是一种常见的编码方式，因为数据其实都是键值对形式，所以在 TAG 中会存储对应的字段和类型信息，Length 存储内容的长度，Value 存储具体的内容。

那么类型信息呢？比如 int32 怎么标记，因为类型个数有限，所以 Protobuf 规定了每个类型对应的二进制编码，比如 int32 对应二进制 000，string 对应二进制 010，这样就可以只用三个比特位存储类型信息。

其次，Protobuf 还会采用一种变长编码的方式来存储数据。这种编码方式能够保证数据占用的空间最小化，从而减少了数据传输和存储的开销。具体来说，Protobuf 会将整数和浮点数等类型变换成一个或多个字节的形式，其中每个字节都包含了一部分数据信息和一部分标识符信息。这种编码方式可以在数据值比较小的情况下，只使用一个字节来存储数据，以此来提高编码效率。最后，Protobuf 还可以通过采用压缩算法来减少数据传输的大小。比如 GZIP 算法能够将原始数据压缩成更小的二进制格式，从而在网络传输中能够节省带宽和传输时间。Protobuf 还提供了一些可选的压缩算法，如 zlib 和 snappy，这些算法在不同的场景下能够适应不同的压缩需求。

[官方文档](https://protobuf.dev/programming-guides/encoding/)

1、**二进制编码**：ProtoBuf使用二进制格式来序列化数据，相比于文本格式（如JSON）它可以更高效地表示数据。二进制编码消耗的空间通常比文本表示法更少，因为它不包含任何冗余元数据或可读性信息。



2、**变长编码**：在对数字数据进行编码时，ProtoBuf采用了一种变长编码方式，将数据变换为可变长度的字节数，例如0-127之间的小数字，用一个字节表示，128-16383之间的中等数字，用两个字节表示。这种编码方式在表示较小的数字时使用更少的字节数，从而节省了空间。



3、**字段标识**：每个字段在编码时都会包含一个字段标识，用于唯一标识该字段的类型和顺序。这样的设计使得解析器能够准确地识别字段，避免了歧义，同时也有助于节约空间。



4、**省略字段名**：ProtoBuf在实际的编码过程中不会包含字段名，而只包含字段号。因为在解析时，程序会根据字段号来确定如何解析数据。这一点与JSON等文本格式不同，避免了重复传输字段名称，减小了数据包的体积。



5、**压缩重复数据**：当有重复的数据出现时，ProtoBuf会使用引用来避免重复编码相同的数据。相同的数据只会被编码一次，重复的地方会引用前面已经编码过的数据，这样节省了空间。



### 有无看过对应引擎源码，并根据业务进行过自定义修改
### 概述剧情系统实现，有无结合场景表现的剧情
