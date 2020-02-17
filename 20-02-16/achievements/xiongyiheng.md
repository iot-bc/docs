## 1. 物联网与区块链结合基本思想
- 物联网络中每一个设备分配地址，给该地址所关联一个账户，用户 通过向账户中支付费用可以租借设备，以执行相关动作，从而达到租借物联网的应用。
- 区块链自身分布式和抗攻击的特点可以很好地融合到这一场景中。
## 2. 加密操作
- Hash加密。将密码通过hash加密（网上很多现成的算法）后的串存在数据库中，登陆的时候用同样的算法得出用户输入的密码的hash串，然后进行比对。P.S. 这是我在实习公司所做的，仅供参考，优点就是通过hash串回到原字符串基本不可能
- 对称加密算法（网上摘抄）

DES（Data Encryption Standard）：经典的分组加密算法，最早是 1977 年美国联邦信 息处理标准（FIPS）采用 FIPS-46-3，将 64 位明文加密为 64 位的密文。其密钥长度为 64 位（包括 8 位校验码），现在已经很容易被暴力破解； 

3DES：三重 DES 操作：加密 --> 解密 --> 加密，处理过程和加密强度优于 DES，但现 在也被认为不够安全； 

AES（Advanced Encryption Standard）：由美国国家标准研究所（NIST）采用，取代 DES 成为对称加密实现的标准，1997~2000 年 NIST 从 15 个候选算法中评选 Rijndael 算法（由比利时密码学家 Joan Daemon 和 Vincent Rijmen 发明）作为 AES，标准为FIPS-197。AES也是分组算法，分组长度为 128、192、256 位三种。AES 的优势在于处理速度快，整个过程可以数学化描述，目前尚未有有效的破解手段； 

IDEA（International Data Encryption Algorithm）：1991 年由密码学家 James Massey 与来学嘉共同提出。设计类似于 3DES，密钥长度增加到 128 位，具有更好的加密强度。

### P.S. 简单列举几个，到时候用的时候再详细筛选。

## 3.配置超级账本+fabric等可参考blockchain_guide.pdf

## 4.下一步计划
- 阅读完[blockchain_guide.pdf](https://github.com/iot-bc/docs/blob/master/_resources/hyperledger-fabric/blockchain_guide.pdf)
- 阅读完[hyperledger-fabric对应文档](https://hyperledger-fabric-cn.readthedocs.io/zh/release-1.4/)
- 配置超级账本+fabric（尽量）
