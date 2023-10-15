---
aliases:
  - chengEfficientECCBasedCPABE2021
tags:
  - ECC
  - CP-ABE
  - power-IoT
rating: ⭐⭐
share: false
ptype: article
---

# An Efficient ECC-Based CP-ABE Scheme for Power IoT
<cite>* Authors: [[Rui Cheng]], [[Kehe Wu]], [[Yuling Su]], [[Wei Li]], [[Wenchao Cui]], [[Jie Tong]]</cite>
* DOI: [10.3390/pr9071176](https://doi.org/10.3390/pr9071176)
* PDF Attachments
	- [2021-An Efficient ECC-Based CP-ABE Scheme for Power IoT.pdf](zotero://open-pdf/library/items/TP94QG9Y)
* Publication Title: [[Processes]]


[Open it in zotero](zotero://select/items/@chengEfficientECCBasedCPABE2021)

***

## Abstract

The rapid development of the power Internet of Things (IoT) has greatly enhanced the level of security, quality and efficiency in energy production, energy consumption, and related fields. However, it also puts forward higher requirements for the security and privacy of data. Ciphertext-policy attribute-based encryption (CP-ABE) is considered a suitable method to solve this issue and can implement fine-grained access control. However, its internal bilinear pairing operation is too expensive, which is not suitable for power IoT with limited computing resources. Hence, in this paper, a novel CP-ABE scheme based on elliptic curve cryptography (ECC) is proposed, which replaces the bilinear pairing operation with simple scalar multiplication and outsources most of the decryption work to edge devices. In addition, time and location attributes are combined in the proposed scheme, allowing the data users to access only within the range of time and locations set by the data owners to achieve a more fine-grained access control function. Simultaneously, the scheme uses multiple authorities to manage attributes, thereby solving the performance bottleneck of having a single authority. A performance analysis demonstrates that the proposed scheme is effective and suitable for power IoT.

* Tags: #CP-ABE, #edge-computing, #elliptic-curve, #multiple-authorities, #outsourcing, #pairing-free, #power-IoT, #time-and-location
## 阅读批注

>[!tip]
>点击pdf文件通过zotero直接跳转的小绿鲸进行阅读

#### 一、未了解的知识点

#### 二、论文创新点
1. 在**电力物联网**中提出了一种有效的基于ECC的CP-ABE方案
2. 系统结构：![](https://cdn.jsdelivr.net/gh/mariosight/image/picture/Pasted%20image%2020231011191655.png)
3. 体系结构方面：采用[LSSS访问结构](../../10-MyNote/LSSS访问结构.md)
4. 安全性方面：
	1. 提出的方案采用多个权威机构对属性进行管理，避免了单权威方案中的**密钥托管**问题，提高了系统的安全性
	2. 通过将**时间和位置域信息**作为动态属性结合到方案中，数据用户只能在有效的时间和位置范围内访问相关的密文，从而提高了电力数据的安全性。具体是通过在生成密钥时同时生成时间密钥和位置密钥，如果密文的访问时间和位置有限，DU需要在有效的时间和位置范围内向相应的AAi请求时间和位置的私钥
	3. 考虑了[前向安全（Forward Security）](../../06-Cards/密码学/前向安全（Forward%20Security）.md)，与2018年的论文中的写法基本一致
	4. 其中[23]指的是18年的论文![](https://cdn.jsdelivr.net/gh/mariosight/image/picture/Pasted%20image%2020231012162443.png)
5. 性能方面：
	1. 计算成本：其中采用的变量基本与2018年的论文一致，不过把矩阵A换了一个字母，因为采用了边缘外包加密，所以出现了预加密的时间开销，但是本地解密的时间开销大大减少，关于加密时间：就加密执行时间而言，方案[23]优于我们的方案，因为我们**考虑了时间和位置属性**，使访问控制更细粒度。因为时间和位置属性的加密需要进行一些标量乘法操作![](../../08-Assets/Pasted%20image%2020231013163256.png)
	2. 通信成本：通信开销主要取决于密文、公钥和私钥的大小，在2018年使用的变量的基础上比较了这些论文的通信开销![](https://cdn.jsdelivr.net/gh/mariosight/image/picture/Pasted%20image%2020231012162837.png)
6. 不足之处：
	1. 无属性可撤销
	2. 密文和密钥的计算与属性的数量成线性关系，即密文和密钥的长度会随着用户和访问结构的属性数量的增加而增加，导致系统效率较低
#### 三、论文疑问
提到了环境是在边缘和云上的，利用边缘计算技术实现了外包加解密，这里的环境指的是什么环境
#### 四、待解决问题
