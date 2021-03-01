# cocoscreator-斗地主
![image](https://raw.githubusercontent.com/JianghongJohn/cocoscreator-ddz/master/屏幕快照%202018-05-18%20下午1.36.30.png)
![image](https://raw.githubusercontent.com/JianghongJohn/cocoscreator-ddz/master/屏幕快照%202018-05-18%20下午1.37.06.png)
![image](https://raw.githubusercontent.com/JianghongJohn/cocoscreator-ddz/master/屏幕快照%202018-05-18%20下午1.37.53.png)
![image](https://raw.githubusercontent.com/JianghongJohn/cocoscreator-ddz/master/屏幕快照%202018-05-18%20下午1.38.13.png)

```
/**
 * 牌型
　　火箭：即双王（大王和小王），最大的牌。
　　炸弹：四张点数相同的牌，如：7777。
　　单牌：任意一张单牌。
　　对牌：任意两张点数相同的牌。
　　三张：任意三张点数相同的牌，如888。
　　三带一：点数相同的三张牌+一张单牌或一对牌。如：333+6 或 444+99。
　　单顺：任意五张或五张以上点数相连的牌，如：45678或78910JQK。不包括 2和双王。
　　双顺：三对或更多的连续对牌，如：334455、7788991010JJ。不包括 2 点和双王。
　　三顺：二个或更多的连续三张牌，如：333444 、555666777888。不包括 2 点和双王。
　　飞机带翅膀：三顺＋同数量的单牌或同数量的对牌。如：444555+79 或333444555+7799JJ
　　四带二：四张牌＋两手牌。（注意：四带二不是炸弹）。如：5555＋3＋8 或 4444＋55＋77 。
 */
var PokerObj = require("Poker");

var CardType = cc.Enum({
    c1: 0, //单牌。  
    c2: -1, //对子。 
    c20: -1, //王炸。  
    c3: -1, //3不带。  
    c4: -1, //炸弹。  
    c31: -1, //3带1。  
    c32: -1, //3带2。  
    c411: -1, //4带2个单，或者一对  
    c422: -1, //4带2对  
    c123: -1, //顺子。  
    c1122: -1, //连队。  
    c111222: -1, //飞机。  
    c11122234: -1, //飞机带单排.  
    c1112223344: -1, //飞机带对子.  
    c0: -1 //不能出牌  
});


//获取牌的等级
function getGrade(card) {
    return card.getComponent('Poker')._grade;
};

//牌生成一个反应数量的数组
function getCarAnalyseInfo(cards) {

    var oneArray = [];
    var twoArray = [];
    var threeArray = [];
    var fourArray = [];
    //循环跳过的数量=相同牌的数量
    var jumpCount = 1;
    for (let i = 0; i  =0 ; i--) {

            let grade = cardsInfo[2][i];
            for (let j = 0 ;  j  = thisCardsInfo[index][i]) {
                //出现一个小于则失败
                return false;
            }
        }
        return true;
    }

    return false;


}

//检查数组是否包含元素
function checkElementIsContain(element, array) {

    for (const grade of array) {
        if (grade == element) {
            return true;
        }
    }
    return false;
};
/** 
     * 对牌进行排序，从小到大，使用冒泡排序，此种方法不是很好 
     * 
     * @param cards 
     *            牌 
     */
    function bubbleSortCards(cards) {
        if (cards == null) {
            return cards;
        }
        let size = cards.length;
        // 冒泡排序,从左到右，从小到大  
        for (var i = 0; i < size; i++) {
            for (var j = 0; j < size - 1 - i; j++) {
                let pokerSpriteOne = cards[j];
                let PokerOne = pokerSpriteOne.getComponent('Poker');
                let pokerSpriteTwo = cards[j + 1];
                let PokerTwo = pokerSpriteTwo.getComponent('Poker');

                var gradeOne = PokerOne._grade;
                var gradeTwo = PokerTwo._grade;

                var isExchange = false;
                if (gradeOne < gradeTwo) {
                    isExchange = true;
                } else if (gradeOne == gradeTwo) {
                    // 2张牌的grade相同  
                    var type1 = PokerOne._bigType;
                    var type2 = PokerTwo._bigType;

                    // 从左到右，方块、梅花、红桃、黑桃  
                    if (type1 == PokerObj.CardBigType.HEI_TAO) {
                        isExchange = true;
                    } else if (type1 == PokerObj.CardBigType.HONG_TAO) {
                        if (type2 == PokerObj.CardBigType.MEI_HUA ||
                            type2 == PokerObj.CardBigType.FANG_KUAI) {
                            isExchange = true;
                        }
                    } else if (type1 == PokerObj.CardBigType.MEI_HUA) {
                        if (type2 == PokerObj.CardBigType.FANG_KUAI) {
                            isExchange = true;
                        }
                    }
                }
                if (isExchange) {
                    cards[j + 1] = pokerSpriteOne;
                    cards[j] = pokerSpriteTwo;
                }
            }
        }
        // console.log("我的牌"+ cards);
        // return cards;
    };
module.exports = {
    CardType: CardType,
    sortByLength: sortByLength,
    bubbleSortCards: bubbleSortCards,
    secondSortWithCards: secondSortWithCards,
    comparePokers:comparePokers

}
```


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)