## BlendMAS: A BLockchain-ENabled Decentralized Microservices Architecture for Smart Public Safety
### 1. 引言部分
关键词：smart public safety(SPS) system, Microservices Architecture 

- SPS系统提供公共安全保障服务，这种服务是基于IoT才得到实现。
- IoT已经可以采用SOA(service-oriented architecture)架构。
- 但是SOA仅仅是单一的架构，在这个单一框架的基础上，为分布式的IoT提供可延展、可扩展的服务是非常难的（这个分布式IoT基于SPS System）。
- 所以，该论文提出利用Microservices Architecture，在这个架构的基础上（同样基于IoT），将安全性的一些服务拆分成不同的containerized microservices，且这些microservices是基于智能合约然后可以被部署在[edge computing](https://en.wikipedia.org/wiki/Edge_computing)节点和[fog computing](https://en.wikipedia.org/wiki/Fog_computing)节点上。
- 最后这个BlendMAS可以提供上述所有服务（包括去中心的、可延展的和安全的数据共享和访问控制，且这些东西都针对分布式、基于IoT的SPS system）。

P.S. 大概来说edge computing 节点和fog computing节点具有的功能都是从就近的节点处带来computation和storage，具体可进上述链接查看

### 2. 介绍部分
- SPS systems可以在边缘（at the edge）加工监控视频流并且运用智能感应器。
- 但是，如果是基于中心化的架构（会运用到云计算，例子：上述SOA架构），会增加很多不确定的等待时间以及更多的工作量。
- 虽然说光运用上述edge computing platform(举个实习里例子，阿里云服务。阿里云服务就是总节点在一个地方，但是有很多分节点，其实就是cdn，然后你离哪近，你的东西就存在哪个分节点上。大概是这么个意思，可以提高效率)可以满足要求，但这仅仅是提高了时间上的效率，还是不能解决许多分布式系统的问题诸如可延展性、多样性和互通性。
- 所以最终，还是需要这么一个微服务架构，这个微服务架构实质是一个新颖的SOA，传统SOA是将系统作为一个单一unit部署，而这个微服务架构则是单一应用分成若干微服务，且相互之间独立，每一个部分完成特定的子任务且需要与系统其他部分轻量级交流。
- 微服务架构还有很多吸引人之处：低耦合，好的延展性，合适的粒度，较低的维护成本。
- 由于微服务架构运用分布式的数据共享和数据获取接口，它的安全性（vulnerabilities in security，意译应该差不多安全性的意思）也是很高的。
- 智能合约和区块链的一些优点（去中心化，不需要第三方，安全等）。
- 这篇论文主要就是提出，在公共安全系统中使用BlendMAS可以保障在不同服务提供商之间数据获取的安全性
- 运用divide-and-conquer。 principle（分而治之原则）来将SPS和安全性功能分成不同的containerized微服务，并且这些服务are computationally affordable to each individual computing platform。
- SPS的安全机制是以分散的为服务的形式实现，且基于智能合约。
- hash of the frame features 和 the corresponding decision 被放在区块数据里面，链接在区块链网络中，为了防止数据篡改。
- identity authentication 和 access control strategy能够保证只有授权过的个体才能在SPS system中访问服务以及数据。
- 该论文主要贡献主要贡献
  - 介绍一个完整的架构：microservice-based SPS plat- form，which is implemented in a hierarchi- cal edge-fog-cloud computing paradigm
  - 一个功能完善的permissioned blockchain network以微服务的方式实现，并且部署在物理网络上
  - 在一个permissioned blockchain network上设计并测试了一个智能合约的原型，这个原型提供了数据共享和访问控制的机制
  - 广泛的、全面的实验比较BlendMAS和monolithic（单一的） SOA framework

### 3.背景知识和相关work

#### A.Smart Public Safety
- 传统上的监控中，安全监控是需要人来参与，人来分辨一些行为是否是违法的等。
- 现在由于人工智能的发展，可以通过机器学习等方法，自动识别这些违法行为等，但都是将这些东西上传到云端，统一处理，这样开销很大，运算负担也很大。
- 最近，可以依赖一种去中心化的监控frameworks，implemented based on the edge-fog-cloud hierarchy architecture.
- input frame that is streamed out of the surveillance camera is given to an edge unit，在这个edge unit里面low-level processing is performed. 
- The intermediate-level is fog nodes（有点像我之前提到的阿里云以及cdn那一块）, where multiple tasks are performed based on the processing power and resources available.
- 最终，云端专注于 historical profile building, algorithm fine tuning, and global statistical analysis, which depends on the type of decisions the system is going to make.

#### B.Microservices in IoT
- 传统SOA不同功能之间关系实在是太紧密了，以至于有新需求无法适应，比如可延展性，服务的可延展性，数据私有化以及跨平台的可操作性。
- 微服务是SOA的一种延展形式。
- 允许功能单元独立工作，低耦合，高内聚。
- 每一个微服务与其他微服务交流通过轻量级机制，比如 HTTP RESTful API 或者 message bus asynchronously。
- 多种去中心化的个人微服务与其他相互之间合作来完成一个系统的复杂功能。
- 微服务架构的两个重要特点
  - fine granularity：大致意思就是每一个微服务都可以在不同的框架中进行开发，并且可以用最少的开发资源。
  - low coupling（低耦合）：微服务部件的功能在部署和开发过程中是相互独立的
- 一个思想：The IoT systems are advancing from “things”-oriented ecosystems to a widely and finely distributed microservices- oriented ecosystems

#### C.Blockchain and Smart Contract
- 区块链最初是为了促进一种加密货币，这种加密货币可以实现商业之间的转账不通过一个中心平台，比如银行或者政府机构。
- 这些交易被miners确认同意然后记录在time-stamped的 区块里面，这些区块可以被cryptographic hash识别认证，并且链接在前继区块上，以一个时间顺序。
- 在区块链网络中，一种consensus mechanism被强制使用在了大量的分布式节点上，这些节点叫做miners，以此来保证存在区块中的数据的sanctity（神圣性）
- 智能合约让用户通过区块链网络达成协议，among parties
- 通过食用加密和安全机制，智能合约将协议（protocols）和用户接口结合起来，使标准化、使安全化计算机网络之间的关系
- 智能合约包括已经定义好的instructions和data集合，这些insturctions和data已经被存在区块的特定地址上，以 Merkle hash tree，这是一种从下到上的二叉树结构。
- 通过暴露公有函数或者应用二进制接口，智能合约与用户交互，提供已经定义好的business logic 或者 contract agreement
- 区块链和智能合约一起可以保证提供一哥solution，使去中心化的SPS systems之间能够安全的数据共享和获取权限

### 4. BlendMAS的体系结构设计
- BlendMAS system是一个完全的去中心化的solution，该系统的不同的功能部分被不同的团队开发，并且hosted by 不同的硬件平台。
- Docker contanier被微服务体系结构采用
- 多层的BlendMAS 平台是通过edge-fog-cloud computing paradigm实现。
- 两种containers
  - 负责安全政策服务，它可以控制数据获取以及认证，来避免未授权的服务请求以及数据泄漏。
  - 另一种是视频流加工微服务，这种微服务是提取frames的特点
- 得益于更强大的计算能力和存储资源能力，特点的融合、行为分析以及mining microservices在fog layer 或者 cloud layer上运行

#### A.BlendMAS的体系结构

- figure1阐释了一个这样的体系结构中，运用了微服务提供的自由区块链网络来保证视频流服务的安全，并且提供安全的数据共享。这个系统由一下三个服务构成：
  - Smart Surveillance Application Services：这些服务提供了一些功能来支持只能监视，比如视频流加工，物体侦测追踪以及移动特点的提取。Real-time视频流是通过摄像头获取的，然后传送到edge微服务来实现特点提取。这些特点是lower level的，然后会被转移到fog nodes进行数据整理然后higher level的分析服务，比如图像识别，行为分析或者反常事件的侦测
  - A Permissioned Blockchain Network：这是一个安全性的微服务，它不仅提供了网络交流频道，还提供了私有的区块链网络基础设施（infrastructure），这些基础设施运行在去中心化的p2p网络。所有的这些网络交流哦读通过TCP/IP协议。身份认证、权限控制，都以DApp的形式开发（也就是去中心化应用）这些应用又是以智能合约为基础，部署在区块链网络中
  - Blockchain-enabled Security Services：这个也是一个安全性的服务，可被分为两个集群
    - mining services（维护区块链网络的核心功能）：运行一致性（之前提到的consensus）算法来认证交易（trasactions）以及形成新的区块。miners是封装好的微服务，这些微服务运行在一个或者多个host机器上，来独立的实现mining task。
    - security policy services：所有的安全政策和模型，比如身份认证以及权限管理，都被编码成不同的微服务，而这些微服务以一种security policy services cluster的形式一起工作。通过实现每一个安全性模型和政策（每个都是以单一的微服务的形式），这个security policy services cluster可以在基于物联网的智能监视系统实现延展性和多样性，而这些都是通过提供了更灵活，更可在不同平台操作性以及更轻量级的安全手段。
- 在SPS系统中，特征数据是通过边缘计算而提取的（edge computing，也就是之前提到的一些camera之类的东西，可以理解为底层），这些特征数据呢，又要在fog layer节点（可以理解为中层）上与contextual data（字面理解就是上下文环境的一些指标数据等）合并，这是为了high level tasks，比如situation awareness。
- 所以，安全机制是有必要的。它可以保护这些在功能服务节点之间传输的数据，并且规定了一个权限控制政策。
- 为了保证SPS系统的去中心化性，可延展性以及fine-grained安全性，BlendMAS主要关注两件事，the permissioned blockchain management and security mechanism enforcement

#### B.Identity-based Permissioned Blockchain

- 所有在permissioned blockchain  network上的个体都以容器的方式实现，也就是说他们进行区块链服务都是独立的在host machines上。
- Figure 2阐释了通过身份认证过程是如何创建一个新的节点。
- oracle，扮演了区块链网络的管理者。维护了全局节点（global nodes）的注册和认证政策。要加入一个permissioned blockchain network，参与者首先发出joining requests给oracle，这个请求是为了得到身份确认。
- 然后oracle确认新的加入请求，这是通过操作identification policies（上面说的认证政策）
- 等这个oracle同意了这个加入请求后，这个新节点的信息就被加到了全局静态节点记录中（global static node record)
- 然后oracle就发送更新之后的static nodes record给所有已经认证过的（certificated）参与者，都在区块链网络中，accordingly
- 刚刚说的是加入，而这样一个memebship的撤销（总之是join的反义词了），是一个个体明确的提出leaving request或者说oracle 明确的清除掉一个misbehaved node。然后oracle又像刚刚那样更新static node record，当然，还是针对每个参与者，accordingly
- 正如fig2中所示，所有的containerized miners相互之间都合作，共同维护一个一致性法则，其他的叫做non-mining containers，其功能就是服务提供者提供区块链交互服务，比如发送交易。

#### C.Blockchain-enabled Security Microservices
安全性功能被分散到多种微服务中，并且部署在分布式计算设备上，这些微服务包括了：

- Registration Service：在BlendMAS系统中，所有个体都必须发送注册请求到该服务中。个体注册过程是通过这个服务再加上每个个体的一个独一无二的区块链账户地址以及一个Virtual ID（VID）。所有的注册信息都通过VID建立索引，并且记录在一个profile database中，这个database又被在fog node中的这种服务维护。P.S. 上述所只这种服务都是Registration Service
- Identity Authentication：每一个区块链账户都是通过它独一无二的地址建立索引，而这些地址又是该用户自己的public key，所以说账户地址是一个理想的东西进行身份认证。这个Identity Authentication 微服务通过暴露一些RESTful API供其他的microservices-enabled providers 查看身份认证结果。一旦一个这种服务请求被收到（received，仅仅是传达到，并不是真正同意接受）了，身份授权决定过程（the identity authentication decision making process）会向registration service询问这个请求者的identity profile，然后根据之前定义的一些政策返回这个身份确认结果
- Security Management：在security services cluster中扮演了数据核安全服务的管理者，它部署the smart contracts encapsulating hashed index authentication 以及 the access control policies。
- Hashed Index Authentication：为了成功的保存生成的hashed index record到区块链里面去，这个微服务最开始会发送一个access request到安全管理（上述）服务中去获得一个批准，有了这个批准就可以executing the hashed index record generation application binary interfaces (ABI) functions of a smart contract。负责记录微服务的index会抽到security management microservices的认可，with 一个智能合约的地址以及ABI函数，这个函数是用来记录hashed index data。形成hashed index records之后，the hashed index recording microser- vices simply interact with the authorized ABI function to save the hashed index data to the blockchain.In hashed index authentication process, microservice queries a hashed key- value index by interacting with smart contract and compares it with calculated hash values of the record index table. Finally, the authentication results are sent back to service requester.
- Access Control：也是针对安全性的一个服务，其实就是访问权限的控制。原文如下：（实在是不好用中文描述）To successfully access services or re- sources at SPS service providers, an entity initially sends an access right request to the access control microservices to get a capability token. Given a reference of the entitys profile, which is the authenticated identity information maintained by the registration microservices, a decision making policy module running on the access control microservices evaluates the access request by enforcing the authorization policies. If the access request is granted, the access control microservice issues the capability token encoding authorized access right, and then launches a transaction to update the token data in the smart contract. Once the transaction has been approved and recorded in a new block, the access control microservice responds to the requester by providing a smart contract address for the querying token data. Otherwise, the access right request is rejected and a denied acknowledgement is returned. Autho- rization validation process is triggered when when a smart surveillance service provider receives a service request from users. Given the validation result that demonstrates the access right policies and conditional constraints are satisfied, the service provider grants the access request and offers services to the requester. Otherwise, the service request is denied.

### 5.实验分析
实验分析主要是它模拟了用他这套方法做的一个SPS system，然后看交互效率等等。没说怎么做，实用性不高

### 6.总结
主要就是原先有个东西，叫做SPS，Smart Public Safety。比如：一些监控设备（其实就是所谓边缘设备了）看一个人的行为是否违章，可以通过AI智能识别。这些是基于SOA架构的，但是这是中心化的，不利于扩展性，也不利于重新部署到一台新的机器上等等等等，而且效率也很低。现在这个论文就讲的是一套全新的基于微服务的体系结构（SOA的延伸产品吧）来实现这个SPS，且基于了区块链（因为这个微服务体系结构和区块链有很多共同之处，也需要区块链为其提供安全保障服务）。然后主要分了三层，最高层就是cloud端，负责最难的那一层AI操作（上面具体有说明的），中层有个类似阿里云的那个cdn那个东西，叫做fog，负责一个稍微简单一点的AI操作，底层就是所谓的边缘设备也就是edge，只是提供了movement feature的获取等很简单的AI操作，其之间交互就是基于区块链安全保障。