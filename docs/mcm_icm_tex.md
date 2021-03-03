---
title: 数模LaTeX模版踩坑记录
date: 2021-02-03 00:00:00
categories:
 - 未分类
tags:
 - latex
---

> latex相关名词解释
> https://www.moonpapers.com/manual/latex/basic/first/term.html

数学建模，找到个[latex模版](https://github.com/latexstudio/CUMCMThesis)，以为到手即用，结果一build就疯狂报错，折腾了两个晚上终于搞定了。

一是因为我的texlive装的是basic版的（当时装的时候网速慢），缺少了好多宏包，足足缺了10个。。。而且不会一次性全部报错出来，一次只报一个，所以我要装好一个，build，看错误信息，再装，重复10次，而且在装的时候不知道后面还差几个。。。

宏包的安装参考了下面两个链接，因为我的texlive没有图形化界面，所以都是手动从CTAN上下包，手动安装。

> miktex安装宏包： https://www.cnblogs.com/zf-blog/p/12331590.html
>
> 宏包路径 /Miktex/tex/latex/
>
> 
> texlive安装宏包： https://www.cnblogs.com/yfjack/p/4639185.html
> 
> 宏包路径 D:\texlive\2014\texmf-dist\tex\latex

具体步骤：

1. 在 https://www.ctan.org/pkg/ 中搜索缺失的宏包，下载；
2. 如果下载解压得到的宏包没有.sty，只有.ins文件，则打开命令控制台，并cd 到下载的宏包文件夹下，然后使用`latex xxx.ins`获得在同目录下获得对应的.sty文件；如果没有.ins只有.dtx文件，则类似地先进入该目录下，然后使用`tex xxx.dtx`命令；
3. 将上面得到的含.sty文件的文件夹复制到latex安装目录下（我的版本为 /usr/local/texlive/2019basic/texmf-dist/tex/latex/ ）；
4. 在terminal中运行`sudo texhash`

终于搞定了宏包的问题，接着又是字体的问题。装SimSun完了，又报错simkai，装完simkai又报错，原来这个simkai没有粗体。。。

所以我就想到在模版里面把默认字体改成mac系统的对应字体（宋体和楷体）。

> mac字体路径：
> ```
> /System/Library/Fonts
> /System/Library/AssetsV2/com_apple_MobileAsset_Font6/
> /Users/Yora/Library/Fonts/ （用户自定义）
> ```

用`fc-list :lang=zh-cn`命令可以给出所有中文字体的路径。

::: details
```zsh
% fc-list :lang=zh-cn
/Users/Yora/Library/Fonts/simkai.ttf: 楷体_GB2312,KaiTi_GB2312:style=Regular
/System/Library/AssetsV2/com_apple_MobileAsset_Font6/b6841082981e7a8ab74788c20cb89f11493fd4bf.asset/AssetData/LingWaiSC-Medium.otf: 凌慧体\-简,凌慧體\-簡,LingWai SC:style=中黑体,中黑體,Medium
/System/Library/AssetsV2/com_apple_MobileAsset_Font6/fedef1896002be99406da1bf1a1a6104a1737b39.asset/AssetData/Xingkai.ttc: 行楷\-简,行楷\-簡,Xingkai SC:style=粗体,粗體,Bold
/System/Library/Fonts/STHeiti Medium.ttc: 黑体\-简,黑體\-簡,Heiti SC,黒体\-簡,Heiti\-간체:style=中等,中黑,Medium,Halbfett,Normaali,Moyen,Medio,ミディアム,중간체,Médio,Средний,Normal,Media
/Users/Yora/Library/Fonts/FandolKai-Regular.otf: FandolKai:style=Regular
/System/Library/Fonts/PingFang.ttc: 苹方\-简,蘋方\-簡,PingFang SC:style=常规体,標準體,Regular
/System/Library/Fonts/STHeiti Light.ttc: 黑体\-繁,黑體\-繁,Heiti TC,黒体\-繁,Heiti\-번체:style=细体,細體,Mager,Fein,Light,Ohut,Fin,Leggero,ライト,가는체,Licht,Tynn,Leve,Светлый,Fina
/System/Library/Fonts/Supplemental/Songti.ttc: 宋体\-简,宋體\-簡,Songti SC:style=细体,細體,Light
/System/Library/Fonts/Supplemental/Songti.ttc: 宋体\-繁,宋體\-繁,Songti TC:style=常规体,標準體,Regular
/System/Library/Fonts/Supplemental/Songti.ttc: 宋体\-简,宋體\-簡,Songti SC:style=常规体,標準體,Regular
/System/Library/Fonts/PingFang.ttc: .苹方\-简,.蘋方\-簡,.PingFang SC:style=中黑体,中黑體,Medium
/System/Library/AssetsV2/com_apple_MobileAsset_Font6/a4374b18bc562b80a5a4940e1f2008bbd58156c4.asset/AssetData/STXIHEI.ttf: STHeiti:style=细体,細體,Mager,Fein,Light,Ohut,Fin,Leggero,ライト,가는체,Licht,Tynn,Leve,Светлый,Fina
/System/Library/Fonts/Supplemental/Songti.ttc: 宋体\-繁,宋體\-繁,Songti TC:style=细体,細體,Light
/System/Library/Fonts/PingFang.ttc: .苹方\-简,.蘋方\-簡,.PingFang SC:style=中粗体,中粗體,Semibold
/System/Library/AssetsV2/com_apple_MobileAsset_Font6/cb9a85576455613deae27ccbede3cece696b39c0.asset/AssetData/Hanzipen.ttc: 翩翩体\-简,翩翩體\-簡,HanziPen SC,翩翩體 簡:style=粗体,粗體,Bold
/System/Library/Fonts/PingFang.ttc: .苹方\-简,.蘋方\-簡,.PingFang SC:style=常规体,標準體,Regular
/System/Library/Fonts/Supplemental/Songti.ttc: 宋体\-简,宋體\-簡,Songti SC:style=黑体,黑體,Black
/System/Library/Fonts/PingFang.ttc: 苹方\-简,蘋方\-簡,PingFang SC:style=极细体,極細體,Ultralight
/Users/Yora/Library/Fonts/SimSun.ttf: 宋体,SimSun:style=Regular
/System/Library/AssetsV2/com_apple_MobileAsset_Font6/c2e85ff2325814a0f6ebd90957fbdb5e5b396867.asset/AssetData/YuppySC-Regular.otf: 雅痞\-简,雅痞\-簡,Yuppy SC:style=常规体,標準體,Regular
/Users/Yora/Library/Fonts/FandolHei-Regular.otf: FandolHei:style=Regular
/System/Library/AssetsV2/com_apple_MobileAsset_Font6/00e58c0676b9e589e9309dbca4b795bbba3b5420.asset/AssetData/Kaiti.ttc: 楷体\-繁,楷體\-繁,Kaiti TC:style=常规体,標準體,Regular
/Library/Fonts/Arial Unicode.ttf: Arial Unicode MS:style=Regular,Normal,obyčejné,Standard,Κανονικά,Normaali,Normál,Normale,Standaard,Normalny,Обычный,Normálne,Navadno,Arrunta
/System/Library/AssetsV2/com_apple_MobileAsset_Font6/fedef1896002be99406da1bf1a1a6104a1737b39.asset/AssetData/Xingkai.ttc: Xingkai TC,行楷\-繁:style=细体,細體,Light
/System/Library/Fonts/PingFang.ttc: 苹方\-简,蘋方\-簡,PingFang SC:style=细体,細體,Light
/System/Library/AssetsV2/com_apple_MobileAsset_Font6/00e58c0676b9e589e9309dbca4b795bbba3b5420.asset/AssetData/Kaiti.ttc: 楷体\-简,楷體\-簡,Kaiti SC:style=常规体,標準體,Regular
/System/Library/AssetsV2/com_apple_MobileAsset_Font6/c91371d5492434af5929487028bf10767406267c.asset/AssetData/Baoli.ttc: 报隶\-简,報隸\-簡,Baoli SC:style=常规体,標準體,Regular
/System/Library/Fonts/PingFang.ttc: .苹方\-简,.蘋方\-簡,.PingFang SC:style=极细体,極細體,Ultralight
/System/Library/AssetsV2/com_apple_MobileAsset_Font6/36440aa0be75aaa7a1fab8c5c42930b7d407dc48.asset/AssetData/Hei.ttf: Hei:style=Regular
/System/Library/Fonts/Hiragino Sans GB.ttc: .Hiragino Sans GB Interface:style=W6
/System/Library/Fonts/Hiragino Sans GB.ttc: .Hiragino Sans GB Interface:style=W3
/System/Library/AssetsV2/com_apple_MobileAsset_Font6/fcc77abee40ac0268e0a78ea256448a23736fcaf.asset/AssetData/WeibeiSC-Bold.otf: 魏碑\-简,魏碑\-簡,Weibei SC:style=粗体,粗體,Bold
/Users/Yora/Library/Fonts/FandolSong-Regular.otf: FandolSong:style=Regular
/System/Library/AssetsV2/com_apple_MobileAsset_Font6/c91371d5492434af5929487028bf10767406267c.asset/AssetData/Baoli.ttc: 报隶\-繁,報隸\-繁,Baoli TC:style=常规体,標準體,Regular
/System/Library/AssetsV2/com_apple_MobileAsset_Font6/bf625d290b705582d5fd619878281f3325b075d0.asset/AssetData/STHEITI.ttf: STHeiti:style=常规体,標準體,Ordinær,Normal,Regular,Normaali,Regolare,レギュラー,일반체,Regulier,Обычный
/System/Library/AssetsV2/com_apple_MobileAsset_Font6/ec2979c8550757993101e27b30b2b89cb45917fc.asset/AssetData/Yuanti.ttc: 圆体\-简,圓體\-簡,Yuanti SC:style=粗体,粗體,Bold
/System/Library/Fonts/Supplemental/Arial Unicode.ttf: Arial Unicode MS:style=Regular,Normal,obyčejné,Standard,Κανονικά,Normaali,Normál,Normale,Standaard,Normalny,Обычный,Normálne,Navadno,Arrunta
/System/Library/Fonts/PingFang.ttc: .苹方\-简,.蘋方\-簡,.PingFang SC:style=细体,細體,Light
/System/Library/Fonts/PingFang.ttc: 苹方\-简,蘋方\-簡,PingFang SC:style=中黑体,中黑體,Medium
/System/Library/AssetsV2/com_apple_MobileAsset_Font6/a3b1936b33a95120db4abbc9c59da5bdbea384ee.asset/AssetData/Lantinghei.ttc: 兰亭黑\-简,蘭亭黑\-簡,Lantinghei SC:style=纤黑,纖黑,Extralight
/System/Library/Fonts/PingFang.ttc: 苹方\-简,蘋方\-簡,PingFang SC:style=纤细体,纖細體,Thin
/System/Library/Fonts/STHeiti Medium.ttc: 黑体\-繁,黑體\-繁,Heiti TC,黒体\-繁,Heiti\-번체:style=中等,中黑,Medium,Halbfett,Normaali,Moyen,Medio,ミディアム,중간체,Médio,Средний,Normal,Media
/System/Library/AssetsV2/com_apple_MobileAsset_Font6/ec88728883c8296c7eb583ce64501d3242b25c2f.asset/AssetData/LingWaiTC-Medium.otf: 凌慧体\-繁,凌慧體\-繁,LingWai TC:style=中黑体,中黑體,Medium
/System/Library/AssetsV2/com_apple_MobileAsset_Font6/263f8d1ebcf06f4703bab24071039da20fb4bb92.asset/AssetData/Libian.ttc: 隶变\-繁,隸變\-繁,Libian TC:style=常规体,標準體,Regular
/System/Library/AssetsV2/com_apple_MobileAsset_Font6/263f8d1ebcf06f4703bab24071039da20fb4bb92.asset/AssetData/Libian.ttc: 隶变\-简,隸變\-簡,Libian SC:style=常规体,標準體,Regular
/System/Library/Fonts/Supplemental/Songti.ttc: 宋体\-简,宋體\-簡,Songti SC:style=粗体,粗體,Bold
/System/Library/AssetsV2/com_apple_MobileAsset_Font6/d980a16edc19d62d8e2af1c1c99d786f6e01bbf9.asset/AssetData/Hannotate.ttc: 手札体\-简,手札體\-簡,Hannotate SC:style=常规体,標準體,Regular
/System/Library/Fonts/STHeiti Light.ttc: 黑体\-简,黑體\-簡,Heiti SC,黒体\-簡,Heiti\-간체:style=细体,細體,Mager,Fein,Light,Ohut,Fin,Leggero,ライト,가는체,Licht,Tynn,Leve,Светлый,Fina
/System/Library/Fonts/PingFang.ttc: .苹方\-简,.蘋方\-簡,.PingFang SC:style=纤细体,纖細體,Thin
/System/Library/Fonts/Supplemental/Songti.ttc: 宋体\-繁,宋體\-繁,Songti TC:style=粗体,粗體,Bold
/System/Library/AssetsV2/com_apple_MobileAsset_Font6/fedef1896002be99406da1bf1a1a6104a1737b39.asset/AssetData/Xingkai.ttc: 行楷\-简,行楷\-簡,Xingkai SC:style=细体,細體,Light
/Users/Yora/Library/Fonts/FandolSong-Bold.otf: FandolSong:style=Bold
/System/Library/Fonts/Hiragino Sans GB.ttc: 冬青黑体简体中文,冬青黑體簡體中文,Hiragino Sans GB,冬青黑體簡體中文 W6,Hiragino Sans GB W6,冬青黑体简体中文 W6:style=W6,Bold
/Users/Yora/Library/Fonts/FandolFang-Regular.otf: FandolFang,FandolFang R:style=Regular
/System/Library/AssetsV2/com_apple_MobileAsset_Font6/7cb72b1f60ccd0551894a1f248aa7c28fa3afb1d.asset/AssetData/Kai.ttf: Kai:style=Regular
/System/Library/AssetsV2/com_apple_MobileAsset_Font6/00e58c0676b9e589e9309dbca4b795bbba3b5420.asset/AssetData/Kaiti.ttc: 楷体\-简,楷體\-簡,Kaiti SC:style=粗体,粗體,Bold
/Users/Yora/Library/Fonts/FandolHei-Bold.otf: FandolHei:style=Bold
/System/Library/AssetsV2/com_apple_MobileAsset_Font6/4c66b413a81d594dc2fc430266c1629c30a5237b.asset/AssetData/STFANGSO.ttf: STFangsong:style=常规体,標準體,Ordinær,Normal,Regular,Normaali,Regolare,レギュラー,일반체,Regulier,Обычный
/System/Library/AssetsV2/com_apple_MobileAsset_Font6/a3b1936b33a95120db4abbc9c59da5bdbea384ee.asset/AssetData/Lantinghei.ttc: 兰亭黑\-简,蘭亭黑\-簡,Lantinghei SC:style=Demibold,中黑
/System/Library/AssetsV2/com_apple_MobileAsset_Font6/b6c310298897f0ac2b38dafd41cef452a0557a31.asset/AssetData/YuppyTC-Regular.otf: Yuppy TC,雅痞\-繁:style=常规体,標準體,Regular
/System/Library/AssetsV2/com_apple_MobileAsset_Font6/ec2979c8550757993101e27b30b2b89cb45917fc.asset/AssetData/Yuanti.ttc: 圆体\-简,圓體\-簡,Yuanti SC:style=常规体,標準體,Regular
/System/Library/AssetsV2/com_apple_MobileAsset_Font6/00e58c0676b9e589e9309dbca4b795bbba3b5420.asset/AssetData/Kaiti.ttc: STKaiti:style=常规体,標準體,Ordinær,Normal,Regular,Normaali,Regolare,レギュラー,일반체,Regulier,Обычный
/System/Library/AssetsV2/com_apple_MobileAsset_Font6/00e58c0676b9e589e9309dbca4b795bbba3b5420.asset/AssetData/Kaiti.ttc: 楷体\-繁,楷體\-繁,Kaiti TC:style=粗体,粗體,Bold
/System/Library/AssetsV2/com_apple_MobileAsset_Font6/a3b1936b33a95120db4abbc9c59da5bdbea384ee.asset/AssetData/Lantinghei.ttc: 兰亭黑\-简,蘭亭黑\-簡,Lantinghei SC:style=Heavy,特黑
/System/Library/AssetsV2/com_apple_MobileAsset_Font6/00e58c0676b9e589e9309dbca4b795bbba3b5420.asset/AssetData/Kaiti.ttc: 楷体\-简,楷體\-簡,Kaiti SC:style=黑体,黑體,Black
/System/Library/Fonts/Supplemental/Songti.ttc: STSong:style=常规体,標準體,Ordinær,Normal,Regular,Normaali,Regolare,レギュラー,일반체,Regulier,Обычный
/System/Library/AssetsV2/com_apple_MobileAsset_Font6/4c5fb4ab37ef16487d14e6bfa70a8b98f7e1efa8.asset/AssetData/WawaSC-Regular.otf: 娃娃体\-简,娃娃體\-簡,Wawati SC:style=常规体,標準體,Regular
/System/Library/AssetsV2/com_apple_MobileAsset_Font6/00e58c0676b9e589e9309dbca4b795bbba3b5420.asset/AssetData/Kaiti.ttc: 楷体\-繁,楷體\-繁,Kaiti TC:style=黑体,黑體,Black
/System/Library/AssetsV2/com_apple_MobileAsset_Font6/fedef1896002be99406da1bf1a1a6104a1737b39.asset/AssetData/Xingkai.ttc: Xingkai TC,行楷\-繁:style=粗体,粗體,Bold
/System/Library/AssetsV2/com_apple_MobileAsset_Font6/cb9a85576455613deae27ccbede3cece696b39c0.asset/AssetData/Hanzipen.ttc: 翩翩体\-简,翩翩體\-簡,HanziPen SC,翩翩體 簡:style=常规体,標準體,Regular
/System/Library/Fonts/PingFang.ttc: 苹方\-简,蘋方\-簡,PingFang SC:style=中粗体,中粗體,Semibold
/System/Library/Fonts/Hiragino Sans GB.ttc: 冬青黑体简体中文,冬青黑體簡體中文,Hiragino Sans GB,冬青黑體簡體中文 W3,Hiragino Sans GB W3,冬青黑体简体中文 W3:style=W3,Regular
/System/Library/Fonts/LastResort.otf: .LastResort:style=Regular
/System/Library/AssetsV2/com_apple_MobileAsset_Font6/d980a16edc19d62d8e2af1c1c99d786f6e01bbf9.asset/AssetData/Hannotate.ttc: 手札体\-简,手札體\-簡,Hannotate SC:style=粗体,粗體,Bold
/System/Library/AssetsV2/com_apple_MobileAsset_Font6/ec2979c8550757993101e27b30b2b89cb45917fc.asset/AssetData/Yuanti.ttc: 圆体\-简,圓體\-簡,Yuanti SC:style=细体,細體,Light
```
:::

在`/usr/local/texlive/2019basic/texmf-dist/tex/latex/ctex/fontset`里面有如下的latex默认字体配置：

```
ctex-fontset-adobe.def		ctex-fontset-macold.def
ctex-fontset-fandol.def		ctex-fontset-ubuntu.def
ctex-fontset-founder.def	ctex-fontset-windows.def
ctex-fontset-mac.def		ctex-fontset-windowsnew.def
ctex-fontset-macnew.def		ctex-fontset-windowsold.def
```

在`ctex-fontset-macold.def`里面看见楷体和宋体的默认字体为STKaiti和STSong：

```latex
\GetIdInfo$Id: ctex.dtx 735dfe2 2019-05-29 21:42:29 +0800 Qing Lee <sobenlee@gmail.com> $
  {Mac OS X fonts definition for Yosemite or earlier version (CTEX)}
\ProvidesExplFile{ctex-fontset-macold.def}
  {\ExplFileDate}{2.4.16}{\ExplFileDescription}
\sys_if_engine_pdftex:TF
  { \ctex_fontset_error:n { mac } }
  {
    \sys_if_engine_uptex:TF
      { \ctex_fontset_error:n { mac } }
      {
        \setCJKmainfont [ BoldFont = STHeiti , ItalicFont = STKaiti ] { STSong }
        \setCJKsansfont [ BoldFont = STHeiti ] { STXihei }
        \setCJKmonofont { STFangsong }
        \setCJKfamilyfont { zhsong } { STSong }
        \setCJKfamilyfont { zhhei }  { STHeiti }
        \setCJKfamilyfont { zhfs }   { STFangsong }
\setCJKfamilyfont { zhkai }  { STKaiti }
      }
  }
\NewDocumentCommand \songti   { } { \CJKfamily { zhsong } }
\NewDocumentCommand \heiti    { } { \CJKfamily { zhhei } }
\NewDocumentCommand \fangsong { } { \CJKfamily { zhfs } }
\NewDocumentCommand \kaishu   { } { \CJKfamily { zhkai } }
```

在模版的`cumcmthesis.cls`把楷体和宋体的默认字体改好就能用了。

```latex
\setCJKfamilyfont{kai}[AutoFakeBold]{simkai.ttf}
\newcommand*{\kai}{\CJKfamily{kai}}
\setCJKfamilyfont{song}[AutoFakeBold]{SimSun}
\newcommand*{\song}{\CJKfamily{song}}

%%改成如下%%

\setCJKfamilyfont{kai}[AutoFakeBold]{STKaiti}
\newcommand*{\kai}{\CJKfamily{kai}}
\setCJKfamilyfont{song}[AutoFakeBold]{STSong}
\newcommand*{\song}{\CJKfamily{song}}
```

---

*一天之后更新：*

国赛模版和美赛模版差别比较大，所以换了个美赛模版。一build又疯狂报错，真是无语了，气得我把basic版卸载了装完全版的MacTeX，解决了一切问题。

这个故事说明开发工具就算一开始安装多么困难，还是要坚持完美装好，磨刀不误砍柴工啊。。。

