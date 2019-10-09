##  [摘抄]从 SOA 到微服务，企业分布式应用架构在云原生时代如何重塑？

原文地址是：
https://mp.weixin.qq.com/s?__biz=MzIzOTU0NTQ0MA==&mid=2247491452&idx=1&sn=772ca4aac563d406274a37ebf54ce8e2&chksm=e9292273de5eab6531ddda0bcba7bf440248d122829176e4edf04aa85b8399302af3f7d260d2&scene=0&xtrack=1&key=f73120b8a2b526d1201085b9ea5f2519ff46dfbb73ccfc5f163c24a0d98b0ecacaf5350be1e2d404132f8ef448f2dbdac2615b71dfdc3a234f60ea44b687d4a7fac7f075adadaedc40b83038e86241f2&ascene=1&uin=Mjc4ODQ4NjUyMA%3D%3D&devicetype=Windows+10&version=62060833&lang=zh_CN&pass_ticket=7qCRqzJ5ElhE0kQDEIyxH52%2BilebvdAH1RtRAgufF6mFvSnbqBgikgKp2tXoSjEb


阿里妹导读：从十余年前的各种分布式系统研发到现在的容器云，从支撑原有业务到孵化各个新业务，企业的发展离不开统一的、与时俱进的技术架构。本篇文章从企业分布式应用架构层面介绍了云原生计算架构带来的变化，希望能够帮助更多企业的IT 转型，利用云计算技术推动其成为市场竞争中的敏捷力量。

进入 21 世纪以来，我们见证了企业分布式应用架构从 SOA (Service-oriented Architecture)，到微服务架构，再到云原生应用架构的演化。
为了说明企业架构演化背后的思考，我们先谈一些玄学。
  * 第一，企业 IT 系统的复杂性（熵）符合热力学第二定律。随着时间的推演，业务的变化，企业 IT 系统的复杂度会越来越高；
  * 第二，在计算机交互设计中有一个著名的复杂性守恒定律[1]。应用交互的复杂性不会消失，只会换一种方式存在。这个原理也同样适用于软件架构。引入新的软件架构，不会降低IT系统的整体复杂性。
听到这里，是否让生命不息、折腾不止的我们感到一丝凉凉？
现代软件架构的核心任务之一就是定义基础设施与应用的边界，合理切分复杂性，减少应用开发者需要面对的复杂性。换句话说，就是让开发者专注在核心价值创新上，而把一些问题交给更合适的人和系统来解决。

我们就从下面这张图开始，探究企业分布式应用架构演进背后的逻辑。
![](https://mmbiz.qpic.cn/mmbiz_png/yvBJb5IiafvkOEx6gkR9ibuVwzoFTsX1x2hKIfNcKg2geZN4P96laZibTba2mhQEqKGHkOa54vD931Wo9KXBnNlUA/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)


 **蜕变之痛： SOA** 

2004 年，IBM 建立 SOA 全球设计中心，我作为研发 TL 和架构师参与了一系列全球客户的 pilot 项目，帮助 Pepboys, Office Depot 等国际企业利用 SOA 优化企业内部和企业间的业务流程，提升业务敏捷性。
当时的大背景是：随着经济全球化逐渐深入，企业面对的竞争加剧，商业变革也开始提速。在大型企业内部的 IT系统已经经过了数十年的演化，整个的技术体系变得异常复杂，并存着诸如主机系统上的 CISC/COBOL 交易应用，小型机 AS400 中的 RPG业务系统，和 X86/Power 等分布式系统的 C/JEE/.Net 应用。
大量应用系统由三方供应商提供，一些系统甚至已经无人维护。而且随着业务迭代，一些新的业务系统被持续构建出来，由于缺乏合理的方法论指导，系统之间缺乏有机的链接，形成了若干的孤岛，持续加剧了IT架构的复杂性，无法支撑业务的发展诉求。这就仿佛各派高手为了帮助受伤的令狐冲，把异种真气输入体中，虽然短时间可以缓解伤势。可是多道真气无法融合，互相激荡，长时间下来会伤上加伤。
因此，企业 IT 所面临的首要挑战就是整合企业中大量竖桶型（silo-ed）的 IT 系统，支撑日益复杂的业务流程，进行高效的业务决策和支撑业务快速变化。

在这种背景下，IBM 等公司提出了SOA（面向服务的架构）理念，将应用系统抽象成一个个粗粒度的服务，构建松耦合服务架构，可以通过业务流程对服务进行灵活组合，提升企业 IT资产复用，提高了系统的适应性、灵活性和扩展性，解决“信息孤岛”问题。
SOA 提出了一系列构建分布式系统的原则，这些思考直到今天也依然适用：
  * 服务具备明确定义的标准化的接口。通过服务定义描述，将服务消费者（Service Consumer）和服务提供者 (Service Provider) 的实现进行解耦，并且服务应该采用 contract-first 而非 code-first 方式进行开发。服务间通信采用面向文档的消息而非特定语言 RPC 协议，一方面可以解决服务与实现语言的解耦，另一方面可以灵活选择同步或者异步的通信实现，提升系统可用性和可伸缩性；
  * 服务应该是松耦合的，服务之间不应存在时间、空间、技术、团队上的依赖；
  * 服务应该是无状态的，使得服务调用与会话上下文状态实现解耦；
  * 服务应该是自治和自包含的，服务的实现是可以独立进行部署、版本控制、自我管理和恢复；
  * 服务是可发现、可组合的。比如可以通过 Service Registry 进行服务发现，实现了服务消费者和服务提供者的动态绑定。业务流程中可以对来自不同系统的的业务服务进行编排组装。

在初始构建 SOA系统的时候，大多采用点对点的通信连接，服务调用和集成逻辑被内嵌在应用实现中。这种方式在服务数量比较少的时候，确实是一种简单和高效的开发方式。但其最大的问题是，随着服务规模的增长，服务之间通信愈发复杂，连接路径和复杂性会剧增，给服务治理带来巨大的挑战。

为了解决上述挑战，企业服务总线 (Enterprise Service Bus，ESB)开始被引入。企业服务总线提供了服务之间的连接（connection），转换（transformantion）,以及中介处理（mediation）的能力。可以将企业内部和各种服务连接到服务总线上，实现信息系统之间的松耦合架构，屏蔽了系统集成的复杂性，提高了 IT系统架构的灵活性，降低企业内部信息共享的成本。  
![](https://mmbiz.qpic.cn/mmbiz_png/Z6bicxIx5naIZeoINm70Hheic0ibhOt4UcnsvBBux0YzsXumQ9VG0BaNJPVichAhibDk1PVWYWO49PU6iaYzm1DBiaBibA/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)
SOA 方法论的目标就像易筋经可以帮助梳理、归聚不同的真气，融会贯通，为我所用。然而修炼过程却绝非易事。大量雄心勃勃的 SOA项目并未取得预期的效果，其背后的原因是什么？

&emsp;任何 IT 架构的成功，都离不开与业务目标、技术基础和组织能力的相互配合。在业务上，当时 SOA 重点解决的是企业 IT 的存量市场的问题。这使得 SOA 方法论很大程度被窄化为 Enterprise Application Integration （EAI 企业应用集成)。
&emsp;在 SOA 理念中，打通信息系统间的经络只是第一步，还需要勤修内功，持续重构迭代企业 IT 架构，这样才能保持企业 IT架构的敏捷、柔性，持续支撑业务的发展和变化。
&emsp;在组织结构上，由于当时在大部分企业的 IT 部门仍然是成本中心，是业务的附属支撑部门，大多数企业缺乏长远的 IT 战略规划，IT 团队也缺乏成长认同，SOA沦为项目制运作而没有组织化保障和持续投入。
即使当时成功的项目也会在复杂性日积月累的侵蚀下，逐渐失去活力。去年在美国生活的朋友发过来照片，15年前我们为客户构建的业务系统还在支撑其现有全国门店的业务。这是技术项目的成功，却反映了企业技术战略的缺失。
在技术上，ESB 架构虽然实现了业务逻辑与服务集成的解耦，可以更好地进行中央化的服务治理，也暴露出一些严肃问题：
  * 由于过度强调业务系统的可复用性，而不是对企业 IT 架构的治理和重构。大量服务集成的实现逻辑被下沉到 ESB 内部（如上图最右侧所示），这些逻辑非常难以维护，难以移植和扩展，成为 ESB 不可承受之重。我们必须在合适的地点合理地处理复杂性，而非将其简单转移；
  * ESB 基于一个中心化的消息处理系统，但随着互联网的高速发展，ESB 已经无法应对企业IT规模化成长的挑战；
  * ESB 这样的 Smart Pipes, Dumb endpoints 的系统架构是一个无法适应快速变化和大众创新的一个架构。

类比一下，电信运营商曾经希望将视频通信，电话会议等复杂功能纳入电信基础设施，只需一个 Dummy电话终端就可以享受丰富的通信服务。然而随着智能电话的普及，微信和钉钉这样的分布式协同工具创新彻底颠覆了人们沟通交流的方式，而电信网络重回管道的宿命。


 **羽化之美： 微服务**  
随着互联网的发展，尤其是移动互联时代的到来，整个世界的经济形态发生了巨大的变化改变。企业 IT 的重点从传统的 System of Record（交易系统，如 ERP、SCM 等）演化到 System of Engagement（互动系统，如全渠道营销）。这些系统需要能够应对互联网规模的快速增长，并且能够快速迭代，低成本试错。企业 IT 已经成为创新驱动的引擎之一，技术拓展商业边界的理想也帮助 IT团队更有使命感，进一步加速推动了企业 IT 的进化。

以 Netflix、阿里为首的一系列互联网公司主导了企业架构新的变革 - 微服务架构。Apache Dubbo, Spring Cloud等微服务框架得到了广泛应用。
微服务的核心思想便是应用功能拆分与解耦，降低业务系统实现复杂性。微服务强调将应用功能拆解为一组松耦合服务，每个服务遵守单一责任原则（Single Responsibility Principle）。微服务架构解决了传统单体式架构存在的几个固有问题：每个服务可以独立部署和交付，大大提升了业务敏捷性；每个服务可以独立横向扩展/收缩，应对互联网规模的挑战。
![](https://mmbiz.qpic.cn/mmbiz_png/yvBJb5IiafvkOEx6gkR9ibuVwzoFTsX1x2PhF0IciaibXQGaphLQRyWWt4OK5KcMr1RB2enIFGibTmc3XCkE5TtavJQ/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)


当然，将大型的单体应用拆解为多个微服务，也一定会增加 IT 系统研发协同、交付、运维的复杂性。这时候微服务架构与 DevOps和容器自然走到了一起，构成了云原生应用架构的雏形。微服务架构继承了 SOA 的架构原则，但是在实现层面，它倾向于通过构造智能端点和哑管道的去中心化分布式架构风格来替代 ESB。
微服务架构首先要面对分布式架构的内生复杂性，请参考分布式计算的误区[4]。微服务框架需要能够解决服务通信和服务治理的复杂性，比如**服务发现、熔断、限流、全链路追踪**等挑战。
微服务框架，如 HSF/Dubbo 或 Spring Cloud 以代码库的方式来封装这些能力。这些代码库被构建在应用程序本身中，随着应用一起发布和维护。
![](https://mmbiz.qpic.cn/mmbiz_png/yvBJb5IiafvkOEx6gkR9ibuVwzoFTsX1x2AKZJIgJAOScBdNQIrIk7KqE9xBVrZXlEiaNYxEWOicTjlRicmV4ECVpEw/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)  
服务通信和治理本质是横向的系统级关注，是与业务逻辑正交的。但在微服务架构中，其实现方式和生命周期与业务逻辑耦合在一起的。
微服务框架的升级会导致整个服务应用的重新构建和部署。此外由于代码库通常与特定语言所绑定，难以支持企业应用的多语言（polyglot）实现。


 **进化之光： 云原生**    
SOA采用中心化的服务总线架构，解耦了业务逻辑和服务治理逻辑；微服务架构回归了去中心化的点对点调用方式，在提升敏捷性和可伸缩性的同时，也牺牲了业务逻辑和服务治理逻辑解耦所带来的灵活性。  
为了解决上述挑战，社区提出了 Service Mesh（服务网格）架构。它重新将服务治理能力下沉到基础设施，在服务的消费者和提供者两侧以独立进程的方式部署。
这样既达到了去中心化的目的，保障了系统的可伸缩性；也实现了服务治理和业务逻辑的解耦，二者可以独立演进不相互干扰，提升了整体架构演进的灵活性。同时服务网格架构减少了对业务逻辑的侵入性，降低了多语言支持的复杂性。
![](https://mmbiz.qpic.cn/mmbiz_png/yvBJb5IiafvkOEx6gkR9ibuVwzoFTsX1x2wlgt02xLqTVicRcxf5WMc6avJNRW757wJNlics7XhPYEqHbh4wfVxJkA/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)  
Google, IBM，Lyft 主导发起的 Istio 项目就是服务网格架构的一个典型的实现，也成为了新的现象级“网红”项目。
![](https://mmbiz.qpic.cn/mmbiz_png/yvBJb5IiafvkOEx6gkR9ibuVwzoFTsX1x2ib9IHVPdmW3jtdic6InbOhwDZ3WpPv69H3JdhsO8EnQCoxaJicSQSYR1w/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)  
上图是 Istio 的架构，逻辑上分为数据平面和控制平面：
  * 数据平面由一组以 sidecar 方式部署的智能代理组成，负责截获应用网络流量，收集遥测数据并且执行服务治理策略；
  * 控制平面中，Galley 负责配置管理，Pilot 负责下发配置，Mixer 负责策略检查和遥测数据聚合，Citadel 负责通信中安全证书管理。
Istio
提供了一系列高阶的服务治理能力，比如：服务发现和负载均衡，渐进式交付(灰度发布)，混沌注入与分析，全链路追踪，零信任网络安全等，可以供上层业务系统将其编排到自己的
IT 架构和发布系统之中。
但是 Service Mesh 不是银弹，其架构选择是通过增加部署复杂性（sidecar）和损失性能（增加两跳），来换取架构的灵活性和系统的可演化性。
为了解决部署复杂性的挑战，社区和云服务商都在共同进行努力：
  * 一方面简化服务网格自动化运维水平（比如阿里云通过 operator 大大简化了 Istio的升级运维和跨 K8s 集群部署的复杂度）；
  * 另一方面提供托管的服务网格服务，帮助用户关注在业务层面的服务治理而非基础架构实现。  

关于性能问题：
  * 一方面 Service Mesh 需要降低自身控制平面和服务平面的性能开销，比如尽可能 offload mixer 负载，将治理策略执行下沉到数据平面完成；
  * 另一方面还需要重新思考整个通信栈中应用与网络基础设施的边界。

为了实现容器应用之间的互联互通，Kubernetes 社区提出 CNI 网络模型，将容器网络连通性与底层网络实现进行解耦，同时 K8s 提供了Service, Ingress, Network policy 等基本元语来支持应用层的服务通信和访问控制。但是这些能力远不能满足应用对服务治理的需求。
服务网格在 L4/L7 增加了流量管理、全链路可观测性、安全互联等新功能，这些是通过引入运行在用户空间的 Envoy代理实现的，在提升灵活性的同时也不可避免地增加了性能开销。
为了系统化解决这个问题，社区在进行有趣的探索。比如在 Cillium 容器网络中，可以利用 eBPF/XDP等操作系统和底层网络能力，将应用层的服务控制能力（如 Kube-Proxy 提供的 service, network policy）下沉到操作系统内核和网络层解决，并优化了 Service Mesh 数据链路，减少上下文切换和数据拷贝，有效地减少了性能开销。
![](https://mmbiz.qpic.cn/mmbiz_png/yvBJb5IiafvkOEx6gkR9ibuVwzoFTsX1x2rnUIZia4tick5yZjXdUmcA6aCCl36icXUQAMSZuUB91iaETia4Z7tgs5I5g/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)
![](https://mmbiz.qpic.cn/mmbiz_png/Z6bicxIx5naKakibCksmuOsokdrYHu2aynIsKzx14yPqIWU1ibSgPwBjIjHLdXqRrfibbDrAe3IOHdJhibCicRKzic9icw/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

目前 Service Mesh 技术还处在技术成熟度曲线的初期，除了在 L4/L7 层提供灵活的服务通信功能，社区也在探索通过网络 Service
Mesh[6] 实现灵活的 L2/L3 组网能力。我们相信其会成为未来企业分布式应用通信基础设施。
在这个过程中会有一些新的理念和项目被持续创造出来，我们需要能够理性地分析其业务价值和技术局限性。我们要避免将 Service Mesh
作为万灵药，不要将应用集成、应用侧安全等业务逻辑下沉到服务网格中，避免我们重蹈复杂性覆辙。可以参考 Application Safety and Correctness Cannot Be Offloaded to Istio or Any Service Mesh[7]。  
 **回望历史**  
天下大势，分久必合，合久必分。企业分布式应用架构也走过一条分分合合的进化道路。在新技术迭起的今天，我们既要拥抱新技术带来的架构变化，更加要关注其背后的演进逻辑和核心价值，系统化地控制复杂性。  
相关链接：  
[1] https://en.wikipedia.org/wiki/Law_of_conservation_of_complexity
[2] https://twitter.com/bibryam/status/1026429379587567616  
[3] https://martinfowler.com/articles/microservices.html  
[4] https://en.wikipedia.org/wiki/Fallacies_of_distributed_computing
[5] https://philcalcado.com/2017/08/03/pattern_service_mesh.html  
[6] https://networkservicemesh.io/
[7] https://blog.christianposta.com/microservices/application-safety-and-
correctness-cannot-be-offloaded-to-istio-or-any-service-mesh/