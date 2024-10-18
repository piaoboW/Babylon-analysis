# <b>Babylon: an extremely appealing protocol scaling Bitcoin to secure PoS chains</b>  


## 1. 背景
&emsp;&emsp;根据DefiLlama的数据显示，截止9月21日，加密货币的总共锁仓量(Total Value Locked)约为$86 Billion。其中Bitcoin超过$10 Billion。这反应出了市场多加密货币质押的强烈需求。根据coingecko.com提供的数据，当前Bitcoin的总市值约为$1200 Billion(2100万X6.2万 USD/枚)，流通供应量为19,757,462枚，约为总供应量的9.4%。此外，根据Coinshares去年3月的数据显示，25%的比特币流通量闲置超5年，67%的流通量闲置超1年，超过66%的流通供应量处于现在状态。大量的比特币的闲置，不仅是资产的浪费，而且没有发挥比特币强大的安全性和去中心化的优势，也不利于区块链生态的发展。通过将比特币出借或质押是一种可以盘活资产的方法，如加密借贷、比特币桥接等。对比特币资产进行盘活的过程中，首要解决的是安全性问题，其次为灵活性和收益。

&emsp;&emsp;区块链世界发展至今，除了比特币，最有价值的公链还有以太坊。保证两者能独领风骚的关键内核是安全性、去中心化程度、价值共识。在以太坊生态中，明星项目EigenLayer再质押协议通过独特的设计和技术创新使得应用链可以共享以太坊生态的安全性。其中，安全性是由以太坊资产，而质押者可以通过质押获得收益。对于比特币，其安全性主要基于POW(Proof-of-Work)矿工的海量hash算力支持，并且随着挖矿难度的提升，这条世界上最安全的区块链将变得越来越安全。相对于模块化思路中再造一个与比特币、以太坊安全性接近且成本性能更优的区块链，或者要求具有足够安全性的Layer1作为Rollups的下三层或部分功能层，借助于比特币这样最安全公链来创造共享安全性服务，无疑是一种可行的选择，如Babylon。它继承了Bitcoin链的安全性，还赋予其资产更多的价值且更加灵活。
 

## 2. Babylon协议
&emsp;&emsp;PoS（Proof-of-Stack）链具有高能效和快速最终确定性，但面临多个安全问题：容易受到不可惩罚的长期安全攻击、低活性弹性以及从低代币估值中启动的困难。在没有外部可信源的情况下，POS链无法单独解决这些安全问题。Babylon协议，一套比特币权益质押(Bitcoin staking)协议，让比特币持有者能够在无需信任任何第三方的情况下质押比特币，具有质押权益的安全保证。该协议的关键是共享Bitcoin链的安全特性。然而，Bitcoin有哪些特性可被Babylon协议共享呢？  

### 2.1 Bitcoin特性
&emsp;&emsp;A、UTXO  
&emsp;&emsp;UTXO（未花费的交易输出模型，Unspent Transaction Outputs），是中本聪为比特币设计的交易模型，其核心思路极为简洁。交易即资金的进出，那么整个交易系统也仅需输入（Input）和输出（Output）这两种形式表达即可。所谓 UTXO 就是资金进来了，但花出去的资金并没有那么多时，余留下来的这部分即是未花费的交易输出（也就是未支付出去的比特币）。而比特币的整个账本实际上就是一个 UTXO 集合，通过记录每个 UTXO 的状态，管理比特币的所有权和流通，每次交易都会花费旧的 UTXO 并生成新的 UTXO。其属性具备一定潜在的可扩展的可能。  

&emsp;&emsp;B、Bitcoin timestamping  
&emsp;&emsp;Bitcoin的timestamp是基于一个时间戳服务器。时间戳服务器是这样⼯作的：为⼀组（block）记录（items）的哈希打上时间戳，⽽后把哈希⼴播出去。每个时间戳的哈希值都纳入了上一个时间戳，形成一条链，后面的时间戳进一步增强前一个时间戳。这种操作是由PoW(Proof-of-Work)支持的。时间戳机制为事件提供了不可逆的时间顺序。  


<center>
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
    src=fig_Babylon/image.png width = "80%" alt=""/>
    <br>
    <div style="color:orange; border-bottom: 1px solid #d9d9d9;
    display: inline-block;
    color: #999;
    padding: 2px;">
      <p align="center"><font face="黑体" size=3.>图 1 Bitcoin链中Hash值计算包含之前区块的Hash值</font></p>
      </div>
</center>

&emsp;&emsp;C、多重签名  
&emsp;&emsp;在比特币区块链中，为了避免一个私钥的丢失导致地址的资金丢失，比特币引入了多重签名机制，即一个交易需要两个或者更多签名才能生效，可以实现分散风险的功能。多重签名可以实现N个人持有私钥，其中M个人同意即可花费资金的功能。比特币的多重签名最多允许15个私钥参与签名，即可实现1-2至15-15的任意组合（1⩽M⩽N⩽15）。而比特币的多重签名采用的是施诺尔（Schnorr）签名，其安全性从数学上得到了证明。此外，施诺尔签名可以实现签名的聚合，即通过一种叫做密钥聚合（key aggregation）的技术，可以将任何一笔“m of n”多签中的 m 个签名聚合为 1 个签名，同时 m 个签名者的公钥也可以聚合为 1 个公钥，如对UTXO单个输入中的多个签名进行聚合，而且可以支持批量验证。  

&emsp;&emsp;D、比特币脚本  
&emsp;&emsp;比特币脚本（Bitcoin Script），通常被视为比特币繁华世界的幕后力量，实则是维护比特币交易安全与效率的关键要素。比特币脚本最引人注目的特性莫过于图灵非完备性。不同于能执行无限循环的图灵完备语言，比特币脚本的这种设计限制，是一种刻意的设计选择，提高了系统的安全性，具有可预见性，有效避免了无限循环所可能引发的风险。比特币脚本的基础是各种操作码，比如 OP_ADD（加法）或 OP_EQUAL（等值）等，尤其包括了Babylon协议中使用到的操作码OP_CHECKSEQUENCEVERIFY、OP_CHECKTEMPLATEWERIFY等。  

### 2.2 Babylon协议的安全性

&emsp;&emsp;比特币权益质押是一个双边市场：一方有安全需求并愿意为此支付费用的PoS链；另一方是拥有资本并愿望从中赚取收益的比特币持有者。比特币质押协议需要为双方提供强有力的安全保障。  

<center>
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
    src=fig_Babylon/image-1.png width = "90%" alt=""/>
    <br>
    <div style="color:orange; border-bottom: 1px solid #d9d9d9;
    display: inline-block;
    color: #999;
    padding: 2px;">
     <p align="center"><font face="黑体" size=3.>图 2 Bitcoin staking is a two-sided market place</font></p>
     </div>
</center>
&emsp;&emsp;Babylon比特币质押协议与现有的消费PoS链结合，具有三个重要的安全属性：1）全面可罚减的PoS安全性，对于质押者的违规行为可追溯(accountable assertion)，并且仅需三分子二的质押者遵守PoS协议，PoS链就能保持良好的活性；2）质押者的安全性，每一位诚实的质押者都可以到期或者提前解绑其质押的比特币；3）质押者的流动性，不要社区共识就能安全快速的解绑质押的比特币。Babylon协议的这些安全特性，是基于Bitcoin链可共享元素，通过创新性的设计，远程质押比特币资产在比特币链上，同时利用PoS链对违规者的可追溯和可消减特征共同完成了对安全性的基本保证。Babylon协议实现其功能涉及了Bitcoin链中的UTXO、时间戳、多重签名以及脚本等。 

&emsp;&emsp;通常，可将比特币质押者分为两大类：诚实的质押者和违规的质押者。在Babylon质押协议框架下，比特币质押的过程如下图所示：  
<center>
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
    src=fig_Babylon/image-2.png width = "90%" alt=""/>
    <br>
    <div style="color:orange; border-bottom: 1px solid #d9d9d9;
    display: inline-block;
    color: #999;
    padding: 2px;">
     <p align="center"><font face="黑体" size=3.>图 3 诚实的比特币质押过程和违规的比特币质押过程</font></p>
      </div>
</center>  

&emsp;&emsp;在实现以上两个不同的比特币质押行程中，Babylon有两个协议：第一个协议叫做 Bitcoin Staking ( 比特币质押 )，第二个协议叫做 Bitcoin Time Stamping（比特币时间戳 )。

#### 2.2.1 比特币质押协议  

&emsp;&emsp;在Babylon协议中，比特币的持有者将比特币质押在比特币链上，无需信任任何第三方的权益质押，实现“无信任(trustless)”质押。即，将质押的比特币锁在比特币链上的合约中，然后当质押者违反PoS 链协议时，在比特币链上将该违反协议者所质押的比特币进行罚减。这是一种“远程质押(Remote staking)”。  

&emsp;&emsp;  在实现“无信任(trustless)”质押的过程中，虽然供给链比特币链没有智能合约层，但是可以通过比特币脚本语言中的UTXO交易表达权益质押合约。在Babylon质押协议中，借助于比特币链上的UTXO，结合现有的操作码，可将质押合约的具体步骤拆解为四个步骤：锁定资金、条件验证、状态更新和收益分发。而从交易的角度分析质押过程，主要包括三种类型的交易：  

&emsp;&emsp;质押交易：BTC质押者通过建立质押交易获得投票权；

&emsp;&emsp;解帮交易：比特币质押者希望在其质押资产到期之前，可以使用解质押交易解绑其质押的资产；

&emsp;&emsp;罚没交易：当比特币质押者(或他们委托的最终性提供者)违规时，进行惩罚的交易。

&emsp;&emsp;流程如下图所示
<center>
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
    src=fig_Babylon/image-3.png width = "90%" alt=""/>
    <br>
    <div style="color:orange; border-bottom: 1px solid #d9d9d9;
    display: inline-block;
    color: #999;
    padding: 2px;">
     <p align="center"><font face="黑体" size=3.>图 4 质押流程</font></p>
      </div>
</center> 

&emsp;&emsp;这些步骤、交易或流程需要相应的机制或技术来保证。在Babylon质押协议中，具体包括以下内容：  

&emsp;&emsp;A、权益质押  

&emsp;&emsp;Babylon协议使用比特币限制盟约仿真器(Bitcoin covenant emulator)来执行权益质押合约(Staking contracts)。比特币限制条款(covenant)是一系列比特币脚本，能够实现包括质押、赎回、削减等简单的智能合约的功能。比特币限制条款仿真器(Covenant emulator)是一种daemon程序，功能与虚拟机(VM)相同，为比特币合约和硬件提供执行环境，将合约代码翻译成比特币脚本来执行，最终输出成UTXO来上链，从而将智能合约引入特比特网络，以增加网络的可编程性。仿真器由限制条款委员会(covenant committee)成员运行。委员会的作用是保护Babylon POS系统免受比特币质押者和验证者的攻击，这将通过对交易共同签署多重签名(multi-signature)来实现。委员会成员用于多签的公钥将会记录在Babylon 区块链的创世文件(genesis file)中。  

&emsp;&emsp;B、自动罚减质押  

&emsp;&emsp;Babylon协议通过accountable assertions和finality gadgets等方式来实现比特币的自动削减。对于accountable assertions，可采用EOTS(extractable one-time signature）来实现。此外，为了在共识协议场景下完成惩罚，Babylon协议在不改变基础共识协议签名方案的前提下，通过在基础共识协议最终块后额外增加一轮由EOTS(extractable one-time signature）签名投票实现，即finality gadgets，包含了多重签名。EOTS可以通过比特币Schnorr 签名来实现。如果一个区块不仅由基础共识协议进行了最终确认，“还获得”超过三分之二质押权益的EOTS签名，则该区块被视为已真正最终确定。在此修改后的协议下，如果还发生破坏区块链完好性的事件，那就说明超过三分之一的质押权益在同一高度用EOTS 签署了两个区块。这会导致这些权益质押者的私钥被提取，进而可以用这些提取的私钥来完成削减交易。  

&emsp;&emsp;C、快速解绑  

&emsp;&emsp;在原生权益质押(native staking)的PoS链中，因为区块链需要社区共识抵御远程攻击，从而需要很长时间才能完成解绑。在Babylon协议中，利用了比特币时间戳协议，将PoS链与比特币链紧密同步，从而无需社区共识，可将解质押时间缩短到1天。  

&emsp;&emsp;基于Babylon权益质押合约、自动罚减质押、以及快速解绑等技术，比特币权益质押协议的核心基础设施是比特币链与PoS 链之间的控制平面，如图所示。其中，控制平面负责多种关键功能，包括：提供比特币时间戳服务、权益质押登记、终局性签名等。控制平面以链的形式实现，以确保其去中心化、安全、抗审查和可扩展。另外，除了栺成区块和验证区块这些基础的共识协议的工作之外，每条PoS 链的验证人还在终局性小工具上签署终局性签名。这些校验者共同运行该架构的数据平面。  

<center>
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
    src=fig_Babylon/image-4.png width = "90%" alt=""/>
    <br>
    <div style="color:orange; border-bottom: 1px solid #d9d9d9;
    display: inline-block;
    color: #999;
    padding: 2px;">
      <p align="center"><font face="黑体" size=3.>图 5 由控制和数据平面组成的系统结构</font></p>
      </div>
</center> 

#### 2.2.2 比特币时间戳协议  

&emsp;&emsp;比特币时间戳协议是Babylon协议关键组成部分。该协议将简明可验证的任何数据发送到Bitcoin链上。其首要用途为在PoS链上打时间戳以强化完整性和安全性，如抵御长距离攻击(long range attacks)、分叉攻击(Forking attack)等。该协议利用比特币来提供时间戳服务，巴比伦区块链来聚合检查点和提供数据可用性，而其他 PoS 区块链则可以利用这种协议来提高自身的安全性。这个协议构建了一个混合型的区块链系统，将比特币的安全性与 PoS 区块链的效率相结合。

&emsp;&emsp;针对PoS安全性问题，Babylon基于比特币时间戳协议的解决方案如下图所示，主要包括Bitcoin主网、Babylon聚合层、IBC通信协议、PoS消费链(目标PoS区块链)等。其中，Bitcoin主网，即Bitcoin时间戳服务器，是信任需求的核心来源；而Babylon链是整个解决方案高效可行的关键。因为PoS直接与Bitcoin链进行交互会存在问题：1）必须检查每个包含交易请求的PoS区块；2）必要在每个检查点发布足够多的签名，以防止某些验证者发送任意哈希并假装正在检查比特币上的PoS块；3）比特币有限的区块空间存在扩展问题。
<center>
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
    src=fig_Babylon/image-5.png width = "90%" alt=""/>
    <br>
    <div style="color:orange; border-bottom: 1px solid #d9d9d9;
    display: inline-block;
    color: #999;
    padding: 2px;">
      <p align="center"><font face="黑体" size=3.>图 6 Babylon协议架构图</font></p>
      </div>
</center> 

&emsp;&emsp;Babylon比特币时间戳处理过程为：  

&emsp;&emsp;1）	数据提交：将PoS区块链上的节点生成的一些重要数据转换为哈希值，如交易或区块信息；

&emsp;&emsp;2）	提交到Bitcoin网络：Babylon链负责收集哈希并进行聚合打包，通过IBC将集合在某个特定的交易提交到Bitcoin链；

&emsp;&emsp;3）	生成时间戳：一旦这些哈希在Bitcoin链上被记录下来，PoS区块链将获得来自Bitcoin链的时间戳；

&emsp;&emsp;4）	使用时间戳：PoS区块链可以利用Bitcoin的时间戳验证其数据的安全性和时效性。
&emsp;&emsp;在Babylon协议中，Bitcoin时间戳提供安全的基本原理如下图所示，即

*	进行攻击的分支将获得BTC主链上一个更晚的BTC时间戳，则根据分支选择规则，该分支将不会被任何消费PoS选择；

*	如果攻击分支想获得被认可，需要在BTC上创建一条很长的分支使得PoS上的分支具有更早的时间戳。然而，这在经济上是不可接受的。
<center>
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
    src=fig_Babylon/image-6.png width = "90%" alt=""/>
    <br>
    <div style="color:orange; border-bottom: 1px solid #d9d9d9;
    display: inline-block;
    color: #999;
    padding: 2px;">
     <p align="center"><font face="黑体" size=3.>图 7 Babylon协议架构图</font></p>
      
      </div>
</center> 

&emsp;&emsp;在解决长距离攻击的同时，PoS块上不可逆的BTC时间戳为PoS链提供了额外的安全收益：  

&emsp;&emsp;•	<b>消除弱主观性</b>：比特币时间戳是客观的。从而可以消除 PoS 链对社会共识和弱主观性的依赖。

&emsp;&emsp;•	<b>更短的解绑时间</b>：通过取代社会共识，BTC 时间戳可以将 PoS 链的质押解绑时间从几周缩短到一天。

&emsp;&emsp;•	<b>新链引导</b>：估值较低的新 PoS 链更容易受到分叉攻击。 BTC 时间戳可以帮助保护链本身的增长。

&emsp;&emsp;•	<b>状态同步和快照的验证</b>：BTC 提供的 PoS 链的客观事实允许 PoS 链的用户验证从 P2P 网络下载的链状态或快照。

&emsp;&emsp;•	<b>保护重要交易</b>：BTC 时间戳可用于进一步确认重要的 PoS 交易，但代价是更长的确认延迟。

&emsp;&emsp;•	<b>抗审查性</b>：BTC 时间戳还可以通过将受审查的交易发布到 BTC 来对抗 PoS 链中的交易审查。

### 2.3 总结
&emsp;&emsp;总的来说，Babylon协议是基于BTC链的多种特性，通过创新性设计，使得消费PoS链可共享BTC链的安全性。Babylon协议叠加的安全性和性能仍需实践验证，而POS消费链的安全性最终要取决于其自身的安全性，并非比特币网络或Babylon协议。这在一定程度上对Babylon协议的生态存在考验。  

## 3. 思考
&emsp;&emsp;Babylon协议以模块化插件的方式作为中间层衔接Bitcoin链与PoS消费链。Bitcoin持有者通过远程质押资产获得收益，收益直接与质押的数量相关。首先，这将引发中心化风险。其次，质押与质押分配问题。从质押资产角度看，不同质押者具有显著的差异，会同时包含两个极端情况。在供需不平衡的时候，如何影响质押资产的分配。从消费PoS链的角度，尤其对于起步阶段的PoS链，竞争质押资产将处于劣势。这又如何解决。第三，质押资产的收益问题。如果比特币质押率过低，将严重影响项目的发展。且随着时间的推移，比特币质押收益必然减少。而当收益率低到一定程度时，将降低比特币持有者的参与意愿，导致项目的发展进入瓶颈期或走入下行。此外，安全性消费侧的需求不确定很高。若其需求无法与供给侧匹配，整个经济上的闭环就无法实现。

&emsp;&emsp;在8月22日晚，比特币质押项目 Babylon 正式开启其比特币质押主网第一阶段，引发了大量加密用户的关注。由于交易量激增，频繁操作以及比特币网络的大规模拥堵，导致比特币网络 Gas 费一度从 0.5 美元飙升至 132 美元，许多散户因高额 Gas 费用遭遇亏损。而且，该阶段质押总量仅1000BTC。当质押总量上升几个量级后，比特币网络是否足以支持满足低Gas费用。此外，该阶段的质押仅给与Babylon积分，其收益的可持续性有待观察。


## 参考资料
[1] https://docs.babylonchain.io/docs/

[2] Bitcoin-Enhanced Proof-of-Stake Security: Possibilities and Impossibilities

[3] Bitcoin Staking: Unlocking 21M Bitcoins to Secure the Proof-of-Stake Economy

[4] Bitcoin: A Peer-to-Peer Electronic Cash System

[5] https://www.techflowpost.com/article/detail_19080.html

[6] https://www.techflowpost.com/article/detail_19080.html

[7] https://www.youtube.com/watch?v=LoVpMH8-CiQ&ab_channel=ChrisHacks

[8] https://www.techflowpost.com/article/detail_19080.html



