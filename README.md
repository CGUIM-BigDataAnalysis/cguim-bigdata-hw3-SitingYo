長庚大學 大數據分析方法 作業三
================

網站資料爬取
------------

``` r
#這是R Code Chunk
library(rvest)
```

    ## Warning: package 'rvest' was built under R version 3.3.3

    ## Loading required package: xml2

    ## Warning: package 'xml2' was built under R version 3.3.3

``` r
dfALL<-NULL
for(i in 1:6){
  indexnum<-i
  url<-paste0('https://www.ptt.cc/bbs/NBA/index',indexnum,'.html')
  nbaurl<-read_html(url)
  title<-nbaurl%>%html_nodes('.title a')%>%html_text()
  author<-nbaurl%>%html_nodes('.author')%>%html_text()
  pushnum<-nbaurl%>%html_nodes('.nrec')%>%html_text()
  df<-data.frame(Title=title,PushNUm=pushnum,Author=author)
  dfALL<-rbind(dfALL,df)
}
```

爬蟲結果呈現
------------

``` r
#這是R Code Chunk
knitr::kable(dfALL) ##請將iris取代為上個步驟中產生的爬蟲資料資料框
```

| Title                                              | PushNUm | Author       |
|:---------------------------------------------------|:--------|:-------------|
| \[轉錄\]Lyotard 對於太陽板討論串的結論             | 27      | Price        |
| \[公告\] 請停止一切關於本次活動的發言              | 19      | Price        |
| \[轉錄\]跟之前那篇比起來 我覺得這篇也應該轉過來    | 4       | Frankaze     |
| \[轉錄\]再轉一篇好文來                             | 2       | Frankaze     |
| \[轉錄\]\[情報\] 夏洛特山貓系列                    |         | Price        |
| \[轉錄\]Re: \[心得\] 真是受不了糗爺....            | 19      | Price        |
| \[轉錄\]總冠軍賽NO.2觀後感                         |         | Price        |
| \[心得\] Rasheed Wallace                           |         | AmuroNamie   |
| 掌控球賽的男人                                     |         | toptree      |
| \[閒聊\] 說說2004季後賽名場面回顧                  | 2       | skchang      |
| \[心得\] 其實說穿了 就是活塞的防守太可怕了         | 6       | shineup      |
| Re: \[閒聊\] 說說2004季後賽名場面回顧              | 1       | cOvi         |
| Re: \[閒聊\] 說說2004季後賽名場面回顧              | 2       | ykshih       |
| Re: \[閒聊\] 說說2004季後賽名場面回顧              | 1       | Frankaze     |
| \[轉錄\]Re: 總冠軍賽NO.3觀後感                     | 1       | Price        |
| \[轉錄\]Re: 總冠軍賽NO.3觀後感                     | 4       | Frankaze     |
| Re: \[轉錄\]Re: 總冠軍賽NO.3觀後感                 |         | star1        |
| Re: \[轉錄\]Re: 總冠軍賽NO.3觀後感                 |         | coldspring   |
| Re: Kobe is frustrated...                          |         | airbear      |
| Re: \[轉錄\]Re: 總冠軍賽NO.3觀後感                 |         | pennykidd    |
| Re: 如何你是Phil Jackson會怎麼作??                 | 2       | jayyoung     |
| Re: 如何你是Phil Jackson會怎麼作??                 | 1       | kairy        |
| Re: 如何你是Phil Jackson會怎麼作??                 |         | MHJH         |
| Re: 如何你是Phil Jackson會怎麼作??                 |         | upt          |
| Re: 如何你是Phil Jackson會怎麼作??                 |         | ball22       |
| Re: 如何你是Phil Jackson會怎麼作??                 |         | Vanlencia    |
| Re: \[問題\] 活塞的罰球數比湖人多的多              |         | bdavid       |
| 中場節目 瓦勒斯專訪.... ￣▽￣||                      | fj      | umonkey      |
| Re: \[閒聊\] 封王後的現象                          |         | fingerroll   |
| Re: \[討論\] 戰敗後的f4                            |         | STARKS3      |
| Re: \[問題\]場邊...                                | 2       | sarahgirl    |
| Re: \[閒聊\] 封王後的現象                          |         | bdavid       |
| Re: \[心得\] 三分線...                             |         | freijaking   |
| Re: \[問題\]場邊...                                |         | jph          |
| Re: 請問哈達威跟歐肥有瑜亮情節嗎?                  |         | FWD          |
| Re: \[問題\]場邊...                                |         | LUDWIN       |
| Re: \[問題\]場邊...                                |         | AtpRyan      |
| Re: 強烈建議湖人使用駭班戰術                       |         | immigo       |
| Re: 強烈建議湖人使用駭班戰術                       |         | hypocrisy    |
| Re: \[問題\] kobe會走嗎....                        |         | joyboytoy    |
| Re: \[討論\] 大家來說說你反湖的理由....            |         | STARKS3      |
| Re: \[討論\] 大家來說說你反湖的理由....            |         | STARKS3      |
| \[處置\] 暫時關閉推文系統                          |         | Lyotard      |
| \[試行\] 不開放推文系統                            |         | Lyotard      |
| Re: \[問題\] 請問                                  |         | catz         |
| \[轉錄\]Thank you, Los Angeles Lakers, 2003- …     | 1       | Price        |
| \[試行\] 版主停止討論的權力                        |         | Lyotard      |
| 夢七名單                                           |         | sam369       |
| \[轉錄\]Larry Brown，沒人比你更值得這個榮耀        |         | g331767      |
| Re: 夢七名單                                       |         | Arbus        |
| Re: 夢七名單                                       | 1       | fatfatfat    |
| Re: \[轉錄\]Thank you, Los Angeles Lakers, 2003- … |         | betwgoev     |
| Re: 夢七名單                                       |         | star1        |
| Milicic骨折                                        |         | Motola       |
| Re: 夢七名單                                       |         | chinlingts   |
| Re: 夢七名單                                       |         | bigjuju      |
| Re: Milicic骨折                                    |         | Hanglin      |
| Re: Milicic骨折                                    |         | BIASONICA    |
| Re: Milicic骨折                                    |         | BIASONICA    |
| \[公告\] 解除所有水桶名單                          |         | Lyotard      |
| \[轉錄\]Re: 球員交易rumor-T-Mac                    | 1       | Price        |
| 【版務公告看板】(最近公告：投票代議裁）            |         | Lyotard      |
| \[情報\] 2003-04 季賽個人獎項整理 (1)              | 1       | Lyotard      |
| \[情報\] 2003-04 季賽個人獎項整理 (2)              |         | Lyotard      |
| \[情報\] 2003-04 季賽個人獎項整理 (3)              | 1       | Lyotard      |
| \[情報\] 2003-04 季賽個人獎項整理 (4)              | 1       | Lyotard      |
| \[公告\] 新增板主                                  |         | fayechen     |
| \[轉錄\]Re: 活塞的勝利，等於 Iverson 的失敗        |         | Price        |
| Re: Milicic骨折                                    |         | SHB          |
| \[文選\] 2004.06.12 - 2004.06.18                   |         | Lyotard      |
| \[投票\] 票選妳/你最喜歡的 NBA 球隊                | 2       | Lyotard      |
| \[轉貼\]小王子的影片                               |         | ccccccc7     |
| \[影片\]                                           |         | salazopyrin  |
| \[影片\]NBA Mix                                    |         | Motola       |
| \[情報\] NBA 版目前人氣球隊投票狀況                |         | Lyotard      |
| \[影片\] top ten plays in finals                   |         | salazopyrin  |
| 【新聞摘要看板】(新：T-Mac, 夢碎隊, 交易與選秀)    |         | Lyotard      |
| \[bt\]1996年明星賽                                 |         | gjli         |
| Re: \[bt\]1996年明星賽                             |         | FURTURE      |
| \[情報\] 你還來得及惡補今年的選秀！                | 2       | Lyotard      |
| Re: \[問題\] 請問一下                              | 1       | JustCold     |
| \[情報\] 2004 選秀結果                             |         | conan        |
| \[情報\] NBA 版人氣投票第二次揭載                  |         | Lyotard      |
| \[請益\] 球員名單                                  |         | McDaniel     |
| Re: \[請益\] 球員名單                              |         | bluewalker   |
| \[情報\] 2004 NBA 選秀結果名單與選秀交易           |         | Lyotard      |
| \[情報\] draft的評論                               |         | nonavailable |
| 2002nba明星賽                                      |         | manufacter   |
| \[NEWS\]O'Neal：離隊是湖人咎由自取                 |         | Lopez8       |
| \[整理\] 各隊選秀綜合報導—大西洋區                 |         | Lyotard      |
| \[整理\] 各隊選秀綜合報導—中央區                   | 1       | Lyotard      |
| Finally Magic deal McGrady for Francis             |         | chpan        |
| Another lockout looming for NBA?                   |         | chpan        |
| \[整理\] 各隊選秀綜合報導—東南區                   |         | Lyotard      |
| \[話題球隊\] 7/1-7/7 沙加緬度國王                  |         | Lyotard      |
| \[整理\] 各隊選秀綜合報導—西南區                   |         | Lyotard      |
| \[奧義\] NBA 版休季期開放推文管理原則              | 9       | Lyotard      |
| \[影片\]Baron Davis Mix                            | 12      | Motola       |
| Re: \[NEWS\]O'Neal：離隊是湖人咎由自取             | 2       | CGary        |
| Re: 再問一個小問題                                 | 9       | CGary        |
| Re: \[NEWS\]O'Neal：離隊是湖人咎由自取             | 1       | CGary        |
| \[投票\] 票選十年來妳/妳最喜歡的國王球員           | 3       | Lyotard      |
| \[國王\] 淺談 Geoff Petrie                         | 12      | Minard       |
| Re: \[話題\] 之所以喜歡國王的理由？                | 5       | sjvious      |
| Top FA -- PF篇                                     | 11      | Finley       |
| Re: \[話題\] 之所以喜歡國王的理由？                | 5       | panvc        |
| Re: \[話題\] 之所以喜歡國王的理由？                | 6       | hbryant      |
| Top FA -- 中鋒篇                                   | 11      | Finley       |
| Top FA -- SG篇                                     | 6       | Finley       |
| 19年戒指夢滅心灰意冷 郵差馬龍正式宣布退役......    | 5       | Dioner       |
| \[情報\] Teams with money to spend                 | 1       | bluewalker   |
| Re: \[話題\] 之所以喜歡國王的理由？                |         | obeyxxxx     |
| \[閒聊\] nash要去太陽的樣子                        | 8       | blueash      |
| Re: 19年戒指夢滅心灰意冷 郵差馬龍正式宣布退役. …   | 3       | DessiMansiz  |
| \[情報\] VC要求交易? (From ESPN)                   | 1       | KaMiRyuu     |
| Re: \[話題\] 之所以喜歡國王的理由？                | 3       | lors         |
| Re: \[話題\] 之所以喜歡國王的理由？                | 6       | GreenJJ      |
| NBA／太陽大手筆　5年21億9505萬簽奈許               | 23      | Motola       |
| Top FA -- PG篇                                     | 13      | Finley       |
| \[情報\] 前NBA球員Manute Bol車禍嚴重受傷           | 6       | MikaHakkinen |

解釋爬蟲結果
------------

``` r
#這是R Code Chunk
dim(dfALL)
```

    ## [1] 120   3

``` r
#有120列(120筆資料) 3行(3個欄位)
nrow(dfALL)
```

    ## [1] 120

``` r
#有120列(120筆資料)
str(dfALL)
```

    ## 'data.frame':    120 obs. of  3 variables:
    ##  $ Title  : Factor w/ 91 levels "[公告] 請停止一切關於本次活動的發言",..: 6 1 10 9 5 7 11 2 15 4 ...
    ##  $ PushNUm: Factor w/ 15 levels "","1","19","2",..: 5 3 6 4 1 3 1 1 1 4 ...
    ##  $ Author : Factor w/ 71 levels "airbear","AmuroNamie",..: 7 7 5 5 7 7 7 2 11 9 ...

``` r
#dfALL是資料框
AuthorNum<-data.frame(table(dfALL$Author))
colnames(AuthorNum)<-c('作者','文章數')
knitr::kable(AuthorNum)
```

| 作者         | 文章數 |
|:-------------|:------:|
| airbear      |    1   |
| AmuroNamie   |    1   |
| coldspring   |    1   |
| cOvi         |    1   |
| Frankaze     |    4   |
| pennykidd    |    1   |
| Price        |    9   |
| shineup      |    1   |
| skchang      |    1   |
| star1        |    2   |
| toptree      |    1   |
| ykshih       |    1   |
| AtpRyan      |    1   |
| ball22       |    1   |
| bdavid       |    2   |
| fingerroll   |    1   |
| fjumonkey    |    1   |
| freijaking   |    1   |
| FWD          |    1   |
| hypocrisy    |    1   |
| immigo       |    1   |
| jayyoung     |    1   |
| joyboytoy    |    1   |
| jph          |    1   |
| kairy        |    1   |
| LUDWIN       |    1   |
| MHJH         |    1   |
| sarahgirl    |    1   |
| STARKS3      |    3   |
| upt          |    1   |
| Vanlencia    |    1   |
| Arbus        |    1   |
| betwgoev     |    1   |
| BIASONICA    |    2   |
| bigjuju      |    1   |
| catz         |    1   |
| chinlingts   |    1   |
| fatfatfat    |    1   |
| g331767      |    1   |
| Hanglin      |    1   |
| Lyotard      |   23   |
| Motola       |    4   |
| sam369       |    1   |
| ccccccc7     |    1   |
| fayechen     |    1   |
| FURTURE      |    1   |
| gjli         |    1   |
| salazopyrin  |    2   |
| SHB          |    1   |
| bluewalker   |    2   |
| CGary        |    3   |
| chpan        |    2   |
| conan        |    1   |
| JustCold     |    1   |
| Lopez8       |    1   |
| manufacter   |    1   |
| McDaniel     |    1   |
| nonavailable |    1   |
| blueash      |    1   |
| DessiMansiz  |    1   |
| Dioner       |    1   |
| Finley       |    4   |
| GreenJJ      |    1   |
| hbryant      |    1   |
| KaMiRyuu     |    1   |
| lors         |    1   |
| MikaHakkinen |    1   |
| Minard       |    1   |
| obeyxxxx     |    1   |
| panvc        |    1   |
| sjvious      |    1   |

共爬出幾篇文章標題? 共爬出120篇標題

哪個作者文章數最多? 120篇文章中,作者Lyotard最多,共23篇

``` r
#這是R Code Chunk
TitleNum<-data.frame(table(dfALL$Title))
colnames(TitleNum)<-c('標題名稱','重複數量')
knitr::kable(TitleNum)
```

| 標題名稱                                           | 重複數量 |
|:---------------------------------------------------|:--------:|
| \[公告\] 請停止一切關於本次活動的發言              |     1    |
| \[心得\] Rasheed Wallace                           |     1    |
| \[心得\] 其實說穿了 就是活塞的防守太可怕了         |     1    |
| \[閒聊\] 說說2004季後賽名場面回顧                  |     1    |
| \[轉錄\]\[情報\] 夏洛特山貓系列                    |     1    |
| \[轉錄\]Lyotard 對於太陽板討論串的結論             |     1    |
| \[轉錄\]Re: \[心得\] 真是受不了糗爺....            |     1    |
| \[轉錄\]Re: 總冠軍賽NO.3觀後感                     |     2    |
| \[轉錄\]再轉一篇好文來                             |     1    |
| \[轉錄\]跟之前那篇比起來 我覺得這篇也應該轉過來    |     1    |
| \[轉錄\]總冠軍賽NO.2觀後感                         |     1    |
| Re: \[閒聊\] 說說2004季後賽名場面回顧              |     3    |
| Re: \[轉錄\]Re: 總冠軍賽NO.3觀後感                 |     3    |
| Re: Kobe is frustrated...                          |     1    |
| 掌控球賽的男人                                     |     1    |
| Re: \[心得\] 三分線...                             |     1    |
| Re: \[討論\] 戰敗後的f4                            |     1    |
| Re: \[問題\] kobe會走嗎....                        |     1    |
| Re: \[問題\] 活塞的罰球數比湖人多的多              |     1    |
| Re: \[問題\]場邊...                                |     4    |
| Re: \[閒聊\] 封王後的現象                          |     2    |
| Re: 如何你是Phil Jackson會怎麼作??                 |     6    |
| Re: 強烈建議湖人使用駭班戰術                       |     2    |
| Re: 請問哈達威跟歐肥有瑜亮情節嗎?                  |     1    |
| 中場節目 瓦勒斯專訪.... ￣▽￣||                      |     1    |
| \[公告\] 解除所有水桶名單                          |     1    |
| \[處置\] 暫時關閉推文系統                          |     1    |
| \[試行\] 不開放推文系統                            |     1    |
| \[試行\] 版主停止討論的權力                        |     1    |
| \[轉錄\]Larry Brown，沒人比你更值得這個榮耀        |     1    |
| \[轉錄\]Thank you, Los Angeles Lakers, 2003- …     |     1    |
| Milicic骨折                                        |     1    |
| Re: \[討論\] 大家來說說你反湖的理由....            |     2    |
| Re: \[問題\] 請問                                  |     1    |
| Re: \[轉錄\]Thank you, Los Angeles Lakers, 2003- … |     1    |
| Re: Milicic骨折                                    |     4    |
| Re: 夢七名單                                       |     5    |
| 夢七名單                                           |     1    |
| \[bt\]1996年明星賽                                 |     1    |
| \[公告\] 新增板主                                  |     1    |
| \[文選\] 2004.06.12 - 2004.06.18                   |     1    |
| \[投票\] 票選妳/你最喜歡的 NBA 球隊                |     1    |
| \[情報\] 2003-04 季賽個人獎項整理 (1)              |     1    |
| \[情報\] 2003-04 季賽個人獎項整理 (2)              |     1    |
| \[情報\] 2003-04 季賽個人獎項整理 (3)              |     1    |
| \[情報\] 2003-04 季賽個人獎項整理 (4)              |     1    |
| \[情報\] NBA 版目前人氣球隊投票狀況                |     1    |
| \[情報\] 你還來得及惡補今年的選秀！                |     1    |
| \[影片\]                                           |     1    |
| \[影片\] top ten plays in finals                   |     1    |
| \[影片\]NBA Mix                                    |     1    |
| \[轉貼\]小王子的影片                               |     1    |
| \[轉錄\]Re: 活塞的勝利，等於 Iverson 的失敗        |     1    |
| \[轉錄\]Re: 球員交易rumor-T-Mac                    |     1    |
| 【版務公告看板】(最近公告：投票代議裁）            |     1    |
| 【新聞摘要看板】(新：T-Mac, 夢碎隊, 交易與選秀)    |     1    |
| Re: \[bt\]1996年明星賽                             |     1    |
| \[NEWS\]O'Neal：離隊是湖人咎由自取                 |     1    |
| \[情報\] 2004 NBA 選秀結果名單與選秀交易           |     1    |
| \[情報\] 2004 選秀結果                             |     1    |
| \[情報\] draft的評論                               |     1    |
| \[情報\] NBA 版人氣投票第二次揭載                  |     1    |
| \[奧義\] NBA 版休季期開放推文管理原則              |     1    |
| \[話題球隊\] 7/1-7/7 沙加緬度國王                  |     1    |
| \[影片\]Baron Davis Mix                            |     1    |
| \[請益\] 球員名單                                  |     1    |
| \[整理\] 各隊選秀綜合報導—大西洋區                 |     1    |
| \[整理\] 各隊選秀綜合報導—中央區                   |     1    |
| \[整理\] 各隊選秀綜合報導—西南區                   |     1    |
| \[整理\] 各隊選秀綜合報導—東南區                   |     1    |
| 2002nba明星賽                                      |     1    |
| Another lockout looming for NBA?                   |     1    |
| Finally Magic deal McGrady for Francis             |     1    |
| Re: \[NEWS\]O'Neal：離隊是湖人咎由自取             |     2    |
| Re: \[問題\] 請問一下                              |     1    |
| Re: \[請益\] 球員名單                              |     1    |
| Re: 再問一個小問題                                 |     1    |
| \[投票\] 票選十年來妳/妳最喜歡的國王球員           |     1    |
| \[國王\] 淺談 Geoff Petrie                         |     1    |
| \[情報\] Teams with money to spend                 |     1    |
| \[情報\] VC要求交易? (From ESPN)                   |     1    |
| \[情報\] 前NBA球員Manute Bol車禍嚴重受傷           |     1    |
| \[閒聊\] nash要去太陽的樣子                        |     1    |
| 19年戒指夢滅心灰意冷 郵差馬龍正式宣布退役......    |     1    |
| NBA／太陽大手筆　5年21億9505萬簽奈許               |     1    |
| Re: \[話題\] 之所以喜歡國王的理由？                |     6    |
| Re: 19年戒指夢滅心灰意冷 郵差馬龍正式宣布退役. …   |     1    |
| Top FA -- PF篇                                     |     1    |
| Top FA -- PG篇                                     |     1    |
| Top FA -- SG篇                                     |     1    |
| Top FA -- 中鋒篇                                   |     1    |

其他爬蟲結果解釋

(1)由表TitleNum看出在120篇文章中, Re: \[話題\] 之所以喜歡國王的理由？ 以及 Re: 如何你是Phil Jackson會怎麼作?? 兩個標題是文章重複數量較高的

(2)由表dfALL觀察出, 文章:\[轉錄\]Lyotard 對於太陽板討論串的結論 作者:Price 推文數是最高的有27個推文
