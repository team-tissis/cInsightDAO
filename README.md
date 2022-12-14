# cInsightDAO
__Portal Repository for cInsightDAO__  

プロジェクトホームページ  
https://chaininsight.tissis.xyz

Opensea  
https://testnets.opensea.io/collection/bonfire-v4

* * *
# For Hackathon
東京web3ハッカソンの審査員の方へ，要点のみ以下にまとめます．
## プロダクト概要
勉強会は，参加者が高め合いながら実力を伸ばせる有意義な場です．一方，管理者に負担が集中しがちな上，質の高い発表に対する報酬や組織拡大への貢献に対する報酬がなく，長期間持続させるのは困難です．
そこで私たちは，自律分散的な意思決定機構，貢献に対するインセンティブ機構，持続可能な組織拡大機構の3つを持ち合わせたDAOの実装を行いました．
意思決定機構については，NounsDAOをさらに改善する形で実装しました．これにより，管理者なしに投票を通じた意思決定が可能になります．
DAOメンバーは，発表や討論において他のメンバーに「いいね」を付与することができ，その数に応じてメンバーのDAOへの貢献度を表す「グレード」がアルゴリズムによって決まります．グレードの上昇は焚き火SBTの成長に反映され．グレードの高いメンバーには，焚き火SBTの色を変化させる火種の役割を持つスキンNFTが付与されます．
グレードが高いメンバーにはリファラル権が付与され，リファラル者には報酬が与えられます．これにより，勉強会の質を担保しつつ，メンバー間で友好的な関係を築きながら，DAOを拡大できることが期待されます．

## 勉強会の課題とソリューション
__課題__
- 勉強会はadminの負担が大きく，持続させることが難しい．
- 質の担保が難しい．

__Solusion__
1. **（持続性のために）分散的な意思決定機構とアップデート機構を持つ．**
    - 分散化されたガバナンス機構の実装
        - nouns folk
    - upgradability の担保
        - proxy contract による実装
2. **（質担保のために）リファラルを主として拡大する．**
    - リファラル機構の実装と報酬発行
    - グレードに応じてリファラル権が付与される．
    - リファラルによって，報酬が与えられる．

3. **（持続性・質担保のために）貢献（発表，ディスカッションの評価 etc.）に対して妥当な報酬が与えられる．**

- 貢献度の可視化と報酬
    - 貢献は dynamic SBT のグレードアップとして反映される
    - 報酬はグレードに応じて NFT が付与される．
- 客観的な貢献の評価のために，人間関係バイアスを低減する．
- 発表・ディスカッションに対していいねをつけることができ，このいいねの数に応じてグレードが向上し，報酬が与えられる．
- いいねをする（評価する）ことに対しても報酬が与えられる．

### 裏のテーマ

従来のプロダクトにはもたらし得なかった新しい視点はあるか？

- 多くの集団において，既得権益者による集団の意思決定の支配と，富の集中化が問題．
- 上記のような偏りを軽減することにより，多数の幸福が実現されうる．

→ 金銭的な権力を排除し参加者全員により対等な権利が与えられたDAO によってこの偏りの低減が可能

- しかしながら，近年の新たな既得権益構造として，インフルエンサーによる意思決定支配と，富の過度な集中化が存在し，DAOはこれの影響を大きく受ける．
- **インフルエンサーの影響が低減された，分散意思決定機構と富の分配機構を保持する組織を作りたい．**

→ on chain dataから得られる人物ネットワークから，人物間の影響力バイアスを算出することで，貢献に対する客観的な報酬発行と，高度に分散化された意思決定を実現する．

- 今回の勉強会DAOにおいては，on chain（SBT）上のリファラル関係から，disconnected tree graph を作成できる．この graph から人物間の距離を計算して，近い人物同士の評価（いいね）や投票などを割引する．
    - （future work）リファラルツリーだと，中期フェーズでのインフルエンサー導出としては弱いので，いいねネットワークなどを用いた割引を考える．

- - - 
# cInsight DAO の説明

## 本DAOの構成と特徴
### 1. スマートコントラクト全体構成
<img src="https://user-images.githubusercontent.com/34847784/200167730-a41fe5da-6881-4b02-8164-95ff33bb1cc1.png" width=700px>

### 2. Bonfire SBT
<img src="https://user-images.githubusercontent.com/34847784/200167732-655cbc2b-e80b-4af6-9f98-5fbfc5af87f7.png" width=700px>

### 3. Skin NFT
<img src="https://user-images.githubusercontent.com/34847784/200167733-9f123c3f-4b78-453c-ad46-0f5b94df0e11.png" width=700px>

### 4. Governance
<img src="https://user-images.githubusercontent.com/34847784/200167800-27c7cead-154c-4eab-bf8d-8ab6d87e6e2c.png" width=700px>



## 本DAO内の用語の解説

__Bonfire SBT__

勉強会DAOの会員証の役割を持つSBT。焚き火から着想を得ており、コミュニケーションの活性化を図る様々な工夫が実装されている。
DAOに対しての貢献に応じてSBTのグレードが決まり、グレードが高くなると火の勢いが増す。
後述する __スキンNFT__ を獲得すると、SBTの色や形態が変化する。

__いいね__

感謝や賞賛を伝え他のメンバーのDAOへの貢献を評価する手段としてSBT保有者は他のSBT保有者に対していいねをすることができる。
いいねは無料で行うことができるが、一月で使えるいいねの数には上限がある。
上限を全てのメンバーについて一律に設定することによって組織内の富の分配を行なっている。無料でいいねできることによって価値の流動性が向上する。

__薪__

前月の獲得いいね数やコミュニティへの貢献に従って毎月初めに薪が獲得できる。この薪の数によってDAO内でのグレードが決定される。
関係性が遠い人物から獲得したいいねはより多くの薪に変換され、これによって新規参入を活性化している。この仕組みはシビルアタックへの対抗策にもなっている。
所有している薪の数は月初めに一定の割合で減っていくため、初期メンバーに権力が集中しにくく新規参加者でも確かな貢献をしている人が高いグレードを得やすい構造となっている。

__グレード__

所持している薪の数に応じて、グレードが決定される。グレードが高いメンバーには後述するリファラル権や __スキンNFT__ などが付与される。また、グレードが高くなると __SBT__ の火の勢いが増す。

__リファラル__

このDAOはリファラル(紹介制度)を推進して組織を拡大していくことを目指している。
グレードに応じてリファラルできる人数が決まる。リファラルにより参加する人は通常よりも安い値段でSBT(会員証)を購入できる。
優秀なDAOメンバーの信頼する人脈から優秀な人を組織に参加させることができるため、勉強会の質を落とさずにDAOを拡大することができる。

__スキンNFT（新提案）__

グレードが高いメンバーにはスキンNFTが付与される。保持しているスキンNFTによってSBTの見た目が変化する。
このスキンNFTは二次流通させることもでき、DAOが拡大していくにつれてこのスキンNFTの価格も高騰していく。
つまり、スキンNFTを保持しているメンバーにとってはDAOを拡大することがインセンティブにつながる。


#### Smart Contract の構成

<!-- ![flow](https://user-images.githubusercontent.com/34847784/200167723-5fe4edb8-2f21-45e8-9e87-3fd81552ee4e.png) -->
<!-- ![資産](https://user-images.githubusercontent.com/34847784/200167734-4af54895-cb48-4fb6-a9ec-f897db4896c7.png) -->



#### Originality
- DAO内での貢献は他のメンバーのいいねによって公平に評価され、この評価に従ってインセンティブが与えられる。このスキームは貢献に対する評価方法、インセンティブ設計として様々なDAOに適用可能。
- リファラルによってDAOが拡大
  - リファラルでSBTを購入すると一般の価格より安くかえる。
  - グレードが高いほどリファラル権が多くもらえる。
  - リファラルの紹介をした場合SBTの価格の一部がリファラーに与えられる。
- skinNFT
  - DAO内での貢献(もらったいいね数)によってグレードが決まり、それによって動的にSBTイメージが変化すkk
  - グレードが高いと月に一回 skinnftが配布される。この配布されたskinnftによって動的にSBTイメージが変化する。

- DAO内のあらゆるパラメータ、ロジックは投票によってのみ変更可能

- SBTの人的ネットワークを用いて，投票・評価での人間関係バイアスを除去
    - （新規）リファラルツリーから，距離が一定以上近いもの同士は投票・評価を割引．
    - SBT間の影響力を考慮する発想自体は，vitalikが提案している（Quadratic Voting）


#### 使用した tech stacks
__Smart Contract__

Solidityを使用

- Upgradable Contract
   - SBT contract, Govenance Contract の両方について contProxy ContractとImplementation Contractに分けて実装。デプロイ後もアップグレード可能なDAOを実現した。
   - 「EIP-2535: Diamonds, Multi-Facet Proxy」を用いることによって実装後の拡張性を向上させた。
- dynamic sbt
  - SBT保有者のグレード、所持しているskinNFTによって画像が動的に変化するSBT。
- governance
  - proposal → voting → smart contract update をシームレスに実現する分散ガバナンス機構を実装。ロジックやパラメータの変更はこのプロセス以外では実行できない。


__Frontend__

React.js

__Backend__

node.js・django


#### 使用したBlockChain

Polygonテストネット Mumbaiを使用

#### deployしたContract
レポジトリ: https://github.com/team-tissis/cInsightContracts

__コントラクト__
- Governance
  - Proxy.sol
    - https://mumbai.polygonscan.com/address/0x6573330b11f30a3583bd4c15f7cbbbea912e0727
  - LogicV1.sol
     -  https://mumbai.polygonscan.com/address/0xd96ce135c3b83cec2a112e9b7aaaf41b68cdd159

- Executor
  - Executor.sol
    - https://mumbai.polygonscan.com/address/0xb9bd0fe4a48c591fe69c6a322960b2841d5b7a52

- Bonfire
  - BonfireProxy.sol
    - https://mumbai.polygonscan.com/address/0x3a76707e7e789fed03c01282d90d5e0a7d13fc1d

  - BonfireLogic.sol
    - https://mumbai.polygonscan.com/address/0x81d391eee3aeef9438f66fe489569e5145d8d366

- SkinNFT
  ー SkinNft.sol
    - https://mumbai.polygonscan.com/address/0x9abf727cbb849aa5077a00db29bf7495fee5e9ac


#### テスト手順を含むレポジトリへのリンク
__Smart Contract (https://github.com/team-tissis/cInsightContracts)__

__Frontend (https://github.com/team-tissis/cInsightFrontend)__

__Backend (https://github.com/team-tissis/cInsightBackend)__

#### 審査やテストのためにプロジェクトにアクセスする方法など
SBTのmintに0.1matic(mumbai testnet)必要です。
