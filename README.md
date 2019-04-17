# DecisionTree
DecisionTree pracrice on Jupyter.

The Data from : https://www.kaggle.com/abcsds/pokemon 

## Outline of My README
* 資料分析目標與推測
* 資料前處理及設計
* 討論

## 資料分析目標與推測
### 目標
使用原有的 Pokemon Data 去做設計，加上自己的設計想法，
把 Pokemon 中龍屬性，飛行屬性，或是蟲屬性的篩選出來，以此為 y 值。
有這三種屬性之一則 y 為1，反之則 y 為0。(Boolean Value)

### 推測&設計邏輯
decision tree 的 node 部份，我認為：
* HP 較小的會較有可能是這三種類型的，因為 HP 高的往往都是地面系或是妖精系或是部份普通系
* 這三種類型的大都不會是防禦型的 Pokemon ，而是攻擊型，所以其物理攻擊和特殊攻擊必定都高於他的相對防禦值
* 這三種類行大都有翅膀，都用飛的，所以 Speed 必定會是大的


## 資料前處理及設計
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
* Speed: 母 Data 即有的資料
* att_minus_def: 物理攻擊-物理防禦的值，所以正值的話代表物理攻擊大於物理防禦，反之則小於
* sp_att_minus_def: 特殊攻擊-特殊防禦的值，所以正值的話代表特殊攻擊大於特殊防禦，反之則小於

## 討論
因為 Pokemon 有十八種屬性，所以本論點的 y 值，僅佔 3/18 的屬性數量，且龍屬性的 Pokemon 又較少，因此在 decision tree 中才會有較少的葉節點是正確答案，而與所設計的邏輯相同的是速度較快的的確有較高的比例會是這上述的三種 Pokemon。
但是不同的是， HP 部份是介在中上的階段，推測可能原因是龍屬性和飛行屬性的 Pokemon 都屬於較強的 Pokemon，所以他們可能原本的 HP 素質就比就算是其他偏重 HP 屬性的 Pokemon 還要高。
