# DecisionTree
DecisionTree pracrice on Jupyter
The Data from : https://www.kaggle.com/abcsds/pokemon 

## 資料分析目標與推測
### 目標
把 Pokemon 中龍屬性，飛行屬性，或是蟲屬性的篩選出來，以此為 y 值。
是則 y 為1，否則 y 為0。(Boolean Value)

### 推測
decision tree 的 node 部份，我認為：
* HP 較小的會較有可能是這三種類型的，因為 HP 高的往往都是地面系或是妖精系或是部份普通系
* 這三種類型的大都不會是防禦型的 Pokemon ，而是攻擊型，所以其物理攻擊和特殊攻擊必定都高於他的相對防禦值
* 這三種類行大都有翅膀，都用飛的，所以 Speed 必定會是大的


## 資料前處理
整理了該份 Data，讓它可以適合丟進去 decision tree 中

### 整理細目
* 將 Attack,	Defense 兩項，做減法，其值作為一個 column
* 將 Sp. Atk, Sp. Def 兩項，做減法，其值作為一個 column
* 刪去 #, Name, Type 1, Type 2, Total, Generation, Legendary 這些無法作為識別依據的 column
* 篩選 Type 1 和 Type 2 這兩個 column 只要屬性中有出現 Flying, Dragon, Bug，即視為 fast=1，若以上三個屬性皆未發現，則fast=0

### 整理結果
整理出這四項 feature：
HP, Speed, att_minus_def, sp_att_minus_def
以及對應的 fast?(Boolean Value)
這些 feature 分別代表
* HP: 母 Data 即有的資料
* Speed: 母 Dara 即有的資料
* att_minus_def: 物理攻擊-物理防禦的值，所以正值的話代表物理攻擊大於物理防禦，反之則小於
* sp_att_minus_def: 特殊攻擊-特殊防禦的值，所以正值的話代表特殊攻擊大於特殊防禦，反之則小於
