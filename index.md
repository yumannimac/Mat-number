<script src="main.js"></script>
  <script type="text/javascript" id="MathJax-script" async
    src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js">
    </script>
  <script>
    MathJax = {
      loader: { load: ['[tex]/physics','[tex]/newcommand','[tex]/mathtools'] },
      tex: {
        inlineMath: [['$', '$'], ['\\(', '\\)']],
        packages: { '[+]': ['physics', 'newcommand','mathtools'] },
      },
      chtml: {
        matchFontHeight: false
      }
    };
  </script>

$$
\newcommand{\la}{\lambda}
\newcommand{\e}{\varepsilon}
\renewcommand{\l}{\left}
\renewcommand{\r}{\right}
\newcommand{\del}{\partial}
\newcommand{\q}{\quad}
\newcommand{\qq}{\qquad}
\newcommand{\dis}{\displaystyle}
\newcommand{\dc}{\Leftrightarrow}
\def\rank{\mathrm{rank}}
\newcommand{\hr}{\hrulefill}
\newcommand{\m}{\item}
\newcommand{\drac}[2]{\dfrac{#1}{#2}}
\newcommand{\delu}[3][]{\drac{\partial^{#1} {#2}}{\partial {#3}^{#1}}}
$$



a

# 複素数の導入に含まれる問題 {#introduction}

虚数単位$i$は通常二次方程式 


$$
\label{虚数} x^2+1=0
$$

の相異なる$2$解の$1$つとして定義され，複素数は$1$と$i$の線型結合として定義される．しかし，そもそも「解」というのは何かということが問題になってくる．「複素数」というくらいだから数でなければならないはずであるが複素数を「知らない」段階では数とは当然実数のことである．とすれば，虚数単位$i$を「$2$乗すると$-1$になる'実数'」として定義してしまっていることになっているのではないか．（そのような実数など存在しない．）このままでは虚数を用いて証明される実数の性質（恒等式など）であっても「虚数は存在しない」という一言で否定することができてしまうような気さえする．

今回は本問題を解決するため，[\[虚数\]](#虚数){reference-type="eqref"
reference="虚数"}を二次正方行列の行列方程式 
$$
X^2+E=0
$$

と読み替え，（$E$は単位行列とした．）解の一つとして虚数単位を定義する立場から複素数の諸性質と複素関数の微分積分を考えることにする．ついでにコーシーの積分定理の証明（グリーンの定理や微小三角形を用いるもの）にも不満があって書いている途中にパラメータ積分として証明できることをたまたま思いついたのでその証明も残した．（が，よく考えると結局無理だった．）あと微分方程式やテイラー展開を使わずにオイラーの公式を導いた．複素数がテーマなので，行列版代数学の基本定理を示すことまでを目標とする．

# 複素数の定義

## 複素数

$a，b\in{\mathbb{R}}$に対し， 
$$
aE+bI
$$

をと呼ぶ．ただし，$E$は二次正方単位行列，$I$は$2$乗すると$-E$になる行列の一つとする．ここでは簡単のため

$$
I=
\begin{pmatrix}
0 & -1 \\
1 & 0 \\
\end{pmatrix}
$$
 として考える．すなわち 
$$
aE+bI=
a\begin{pmatrix}
1 & 0 \\
0 & 1\\
\end{pmatrix}+b
\begin{pmatrix}
0 & -1 \\
1 & 0 \\
\end{pmatrix}
=\begin{pmatrix}
a & -b \\
b & a \\
\end{pmatrix}
$$
 という"行列"を複素数と呼ぶことにするのである．

## 定義の由来

二次正方行列として考えたのは，体にする(四則演算ができるようにする)ためである．

### 解釈1 {#解釈1 .unnumbered}

回転行列 
$$
R_{\theta}=\begin{pmatrix*}[r]
\cos\theta & -\sin\theta\\
\sin\theta & \cos\theta
\end{pmatrix*}
$$
 を考える．いま 
$$
-E=R_{\pi}
$$
 より， $2$ 乗すると $-E$
になる行列として 
$$
I=R_{\frac{\pi}{2}}=\begin{pmatrix}
0&-1\\
1&0
\end{pmatrix}
$$

を考えるのが自然であるような気がする．この方法で複素数を構成すると

$$
R_{\theta}=E{\cos\theta}+I{\sin\theta}
$$

となり，複素数平面としてのイメージがしやすくなるという利点がある．

### 解釈2 {#解釈2 .unnumbered}

$I$ と$E$ が一次独立であるようにするため 
$$
I=\begin{pmatrix}
0&b\\
c&0
\end{pmatrix}
$$
 と仮におくと 
$$
I^2=bcE
$$
 より $bc=-1$
でなければならない．$b，c\in\mathbb{Z}$として 
$$
(b，c)=(1,-1),(-1,1)
$$

である．後者を$I$とおけば，前者は$-I$で表せる．この解釈においても

$$
I=\begin{pmatrix}
0&-1\\
1&0
\end{pmatrix}
$$
 である．

# 複素数の性質

以後複素数の集合を$\mathbb{C}$と呼ぶことにする．$\mathbb{C}\in M_2\l(\mathbb{R}\r)$である．ここで$M_2\l(\mathbb{R}\r)$は実二次正方行列の集合とした．複素数の加減乗法は行列のものを用いて定義する．$\mathbb{C}$には乗法の単位元$E$，零元$O$，$O$でない元$A$に対する逆元$A^{-1}$の存在，乗法の可換性から$\mathbb{C}$は体である．

以下は適宜計算して示すこと．

-   $\forall A,B\in \mathbb{C}\  AB=BA$

-   $\left( aE+bI \right)^{-1}=\drac{1}{a^2+b^2}\l(aE-bI\r)$

$\sqrt{\det A}=\sqrt{a^2+b^2}$を$A$の絶対値と呼ぶことにして，ここだけの記号として$\l|A\r|$（$\det A$と区別することに注意）と表すことにする．

# 複素数の微分

写像$f:\mathbb{C}\to \mathbb{C}$の微分を以下のように定義する．（ただし$O \neq H\in \mathbb{C}$とする．）



$$
\dv{f\l(Z\r) }{Z}\bigg|_{Z=A}=\lim_{\l|H\r|  \to 0}\l\{f\l(A+H\r) -f\l(A\r) \r\} H^{-1}
$$


## 行列の微分公式

## オイラーの公式

写像$\exp : \mathbb{C} \to  \mathbb{C}$；微分可能
を以下を満たす写像として定義する．
写像$\exp$が存在しかつ一通りに定まる，すなわち$\forall r,\theta \in \mathbb{R}$に対して



$$
\exp \l(rE+\theta I\r) =e^r \begin{pmatrix}
    \cos \theta & -\sin \theta \\
    \sin \theta & \cos \theta 
    \end{pmatrix} =e^r R_{\theta }=e^r \l(E\cos \theta +I\sin \theta \r)
$$
    
であることを示す．これは有名なオイラーの公式の行列表記である．
(1)によって を示せば十分である．

### ［1］の証明 {#の証明 .unnumbered}

$f: \mathbb{R}\to \mathbb{C}，r\mapsto f\l(r\r)=e^{-r}\exp \l(rE\r)$とする．$f\l(r\r) =g\l(r\r) E+h\l(r\r) I$であるとすると，



$$
\dv{}{r} f\l(r\r) =\pmat{
        g'\l(r\r) & -h'\l(r\r) \\
        h'\l(r\r) & g'\l(r\r)   
    }
$$
     である． 
    
    
$$
    \begin{split}
        \dv{}{r}\exp \l(rE\r)=\, & \lim_{\Delta r \to 0}\drac{1}{\Delta r}\left\{\exp \l(\left(r+\Delta r\right)E\r)-\exp \l(rE \r)\right\} \\
        \stackrel{(1)}{=}\; & 
        \lim_{\Delta r \to 0}\drac{1}{\Delta r}\l\{\exp \l(\Delta r E \r) -\exp \l(O\r) \r\} \exp \l(r E\r) 
        \\
        =\, &  \lim_{\Delta r \to 0}\l(\Delta r E\r) ^{-1}\l\{\exp \l(\Delta r E \r) -\exp \l(O\r) \r\} \exp \l(r E\r) 
        \\
        \stackrel{(3)}{=}\; & \exp \l(rE\r) 
    \end{split}
$$
     より



$$
\dv{}{r}f\l(r\r) =-e^{-r}\exp \l(rE \r) +e^{-r}\exp \l(r E\r) =O=\begin{pmatrix}
    0& 0\\
    0& 0
    \end{pmatrix}
$$
    
から$g'\l(r\r) =h'\l(r\r) =0$．したがって$f\l(r\r)$は定数で

$$
f\l(r\r) =f\l(0\r) =\exp \l(O\r) \stackrel{(2)}{=}E
$$
 である．
以上より 


$$
\exp \l(rE\r)=e^r E
$$
 であることが示された．（証明終）

### ［2］の証明 {#の証明-1 .unnumbered}

$\Theta: \mathbb{R}\to \mathbb{C}，\theta \mapsto \Theta\l(\theta \r)=R_{-\theta }\exp \l(\theta I\r) =\left( E\cos \theta -I\sin \theta \right) 
\exp \l(\theta I\r)$とする．
$\Theta\l(\theta \r) =\varphi \l(\theta \r)E +\phi\l(\theta \r)I$とすると



$$
\begin{split}
        \dv{}{\theta }\exp \l(\theta I\r) 
        =\, & 
        \lim_{\Delta \theta  \to 0} \drac{1}{\Delta \theta }\l\{\exp \l(\theta +\Delta \theta \r) I-\exp \l(\theta I\r) \r\} \\
        \stackrel{(1)}{=}\,&  \lim_{\Delta \theta  \to 0}\drac{1}{\Delta \theta }\l\{\exp \l(\Delta \theta I\r) -\exp \l(O\r) \r\}\exp \l(\theta I\r) 
        \\
        \stackrel{}{=}\, & \lim_{\Delta \theta  \to 0}I\l(\Delta \theta I\r) ^{-1}\l\{\exp \l(\Delta \theta I\r) -\exp \l(O\r) \r\}\exp \l(\theta I\r) \\
        \stackrel{(3)}{=}\, & I \exp \l(\theta I\r) 
    \end{split}
$$
     であり 
    
    
$$
    \dv{}{\theta }R_{-\theta }=\pmat{
        -\sin \theta &\cos \theta \\
        -\cos \theta &-\sin \theta 
    }=
    \pmat{
        \cos \theta &\sin \theta \\
        -\sin \theta &\cos \theta 
    }
    \begin{pmatrix}
    0& 1\\
    -1& 0
    \end{pmatrix} 
    =-R_{-\theta }I
$$
     より



$$
\dv{ }{\theta }\Theta\l(\theta \r)=-R_{-\theta} I \exp \l(\theta  I\r)+R_{-\theta} I \exp \l(\theta  I\r)  =O.
$$

［1］同様$\varphi' \l(\theta \r) =\phi' \l(\theta \r) =0$より$\Theta\l(\theta \r)$は定数であり



$$
\Theta\l(\theta \r) =\Theta\l(0\r) =\exp \l(O\r) \stackrel{(2)}{=}E.
$$

以上より 


$$
\exp \l(\theta I\r) =R_{\theta }
$$

であることが示された．（証明終）\
以上の［1］，［2］の証明では写像$\exp$が存在するならば
$\exp \l(rE+\theta I\r) = e^r R_{\theta }$に定まることを示した．上式が確かに(1)(2)(3)を満たすことを示そう．

なお 


$$
\exp {\pi I }+E=0
$$
 はオイラーの等式である．\
また 


$$
\begin{split}
        \dv{}{Z}\exp Z\bigg|_{Z=A}=\, &  \lim_{\l|H\r|  \to 0} \l\{\exp \l(A+H\r) -\exp A\r\}{H}^{-1}
    \\
    =\, &   \lim_{\l|H\r|  \to 0} \exp A\l\{\exp \l(H\r) -E\r\}{H}^{-1}\\
    =\, & \exp A
    \end{split}
$$
    
であることから写像$\exp$が複素数平面全域において全方向から微分可能つまり正則であることも確認できる．

## その他の関数の拡張

以下，簡単のため複素数$Z$に対し$\exp Z$を$e^{Z}$と表すことにする．\
オイラーの公式より 


$$
\begin{aligned}
    e^{\theta I}=E \cos \theta +I \sin \theta \label{オイラー１}\\
    e^{-\theta I}=E \cos \theta -I \sin \theta\label{オイラー２}\end{aligned}
$$
    
[\[オイラー１\]](#オイラー１){reference-type="eqref"
reference="オイラー１"}と[\[オイラー２\]](#オイラー２){reference-type="eqref"
reference="オイラー２"}を足して$2$で割ると

$$
E \cos \theta =\drac{e^{\theta I}+e^{-\theta I}}{2}
$$

[\[オイラー１\]](#オイラー１){reference-type="eqref"
reference="オイラー１"}から[\[オイラー２\]](#オイラー２){reference-type="eqref"
reference="オイラー２"}を引いて$\drac{1}{2}I^{-1}$かけると

$$
E \sin \theta =\drac{e^{\theta I}-e^{-\theta I }}{2}I^{-1}
$$

である．これを用いて三角関数を拡張することにする．すなわち複素数$\Theta$の三角関数を



$$
\begin{aligned}
\label{sinの定義}
     \cos \Theta &:=\drac{e^{\Theta I}+e^{-\Theta I}}{2}\\
\label{cosの定義}
     \sin \Theta &:=\drac{e^{\Theta I}-e^{-\Theta I }}{2}I^{-1}\end{aligned}

$$
     
と定めることにする．[\[sinの定義\]](#sinの定義){reference-type="eqref"
reference="sinの定義"}，[\[cosの定義\]](#cosの定義){reference-type="eqref"
reference="cosの定義"}の定義のもとで 


$$
\begin{aligned}
    \cos \l(\theta E\r) =E \cos \theta \\
    \sin \l(\theta E\r) =E \sin \theta \end{aligned}
$$
    
である．行列の微分公式から 


$$
\begin{aligned}
    \dv{}{\Theta}\cos \Theta&=\drac{Ie^{I\Theta}-Ie^{-I\Theta}}{2}=-\drac{e^{\Theta I}-e^{-\Theta I}}{2}I^{-1}=-\sin \Theta\\
    \dv{}{\Theta}\sin \Theta&=\drac{Ie^{I\Theta}+Ie^{-I\Theta}}{2}I^{-1}=\drac{e^{\Theta I}+e^{-\Theta I}}{2}=\cos \Theta\end{aligned}
$$
    
が得られる．これは実数における微分と対応し，かつここから複素数の写像$\cos$，$\sin$が正則であることが確認できる．

# 複素数の積分

複素数の積分を以下で定義する．



$$
\int_{C}^{} f\l(Z\r) \, dZ \equiv \lim_{n \to \infty} \sum_{k=1}^{n}  f\l(Z_{k}\r) \Delta Z_k
$$

ただし$\Delta Z_k=Z_{k}-Z_{k-1}$とする．

ここで$Z=xE+yI$，$f\l(xE+yI\r) =g\l(x,y\r) E+h\l(x,y\r) I$とおくと，$x:x_1 \to x_n$，$y:y_1 \to y_n$



$$
\begin{split}
        \int_{C}^{} f\l(Z\r) \, dZ =\, & 
        \lim_{ \delta\l(\Delta\r)  \to 0} \sum_{k=1}^{n} \l\{g\l(x_k,y_k\r) E+h\l(x,y\r) I\r\}\l(\Delta x_kE +\Delta y_k I\r) \\
        =\, & \lim_{ \delta\l(\Delta\r)  \to 0} \sum_{k=1}^{n} \left\{\left(g\Delta x_k -h\Delta y_k\right)E+\l(g\Delta y_k+h\Delta x_k\r)I \right\}\\
        =\, & \left(\int_{x_0}^{x_n} g\l(x,y\l(x\r) \r) \, dx-\int_{y_0}^{y_n} h\l(x\l(y\r), y\r) \, dy\right)E
        \\
        &\qq \qq
        +\l(\int_{y_0}^{y_n} g\l(x\l(y\r) ,y\r) dy+\int_{x_0}^{x_n} h\l(x,y\l(x\r) \r) \, dx\r) I
    \end{split}
$$
     である．

## コーシーの積分定理

$x=x\l(t\r) ,y=y\l(t\r)$とすると合成関数の微分法によって 


$$
\begin{split}
        \int_{C}^{} f\l(Z\r) \, dZ =\, & 
        E\int_{t_0}^{t_n} \left\{g\l(x\l(t\r) ,y\l(t\r) \r) \, x'\l(t\r) -h\l(x\l(t\r) ,y\l(t\r) \r) \, y'\l(t\r)\right\}\, dt  \\
        &\qq 
        +I\int_{t_0}^{t_n} \left\{g\l(x\l(t\r) ,y\l(t\r) \r) \, y'\l(t\r) +h\l(x\l(t\r) ,y\l(t\r) \r) \, x'\l(t\r)\right\}\, dt 
    \end{split}
$$
     であることがわかる．

ここで$f$が正則であるとすると，コーシー・リーマンの関係式



$$
\begin{aligned}
        \delu{g}{y}&=-\delu{h}{x} \label{cl1}\\ 
        \delu{g}{x}&=\delu{h}{y}\label{cl2}
    \end{aligned}
$$
     を満たす． 
    
    
$$
    \begin{aligned}
    u&=\int_{}^{} g \, dx+\int_{}^{} \left\{\l(-h\r) -\delu{}{y}\l(\int_{}^{} g \, dx\r)    \right\} dy\\ 
    v&=\int_{}^{} h \, dx+\int_{}^{} \left\{g - \delu{}{x}\l(\int_{}^{} g \, dy\r)\right\} \, dx\end{aligned}
$$
    
とおくと[\[cl1\]](#cl1){reference-type="eqref"
reference="cl1"},[\[cl2\]](#cl2){reference-type="eqref"
reference="cl2"}より 


$$
\begin{split}
        \int_{C}^{} f\l(Z\r) \, dZ =\, & 
        E\int_{t_0}^{t_n} \left(\delu{u}{x} \drac{dx}{dt} +\delu{u}{y}\drac{dy}{dt}\right) \, dt 
        +I\int_{t_0}^{t_n} \left(\delu{v}{y}\drac{dy}{dt} +\delu{v}{x}\drac{dx}{dt}\right)\, dt \\
        &=\, E \int_{t_0}^{t_n} \drac{du}{dt }\, dt +I \int_{t_0}^{t_n} \drac{dv }{dt }\, dt  \\
        &=\, E\left\{ u\l(x\l(t_n\r) ,y\l(t_n\r) \r)  -u\l(x\l(t_0\r) ,y\l(t_0\r) \r)  \right\} 
        \\
        &\qq  +I\left\{ v\l(x\l(t_n\r) ,y\l(t_n\r) \r) -v\l(x\l(t_0\r) ,y\l(t_0\r) \r)  \right\}\\
        &=\, O
    \end{split}
$$
    
である．コーシーの積分定理が合成関数の微分公式としてあっさり証明できてしまったわけである．（？）本来あるべき「単純閉曲線$C$が含まれる領域$D$の内部で常に正則である」$\cdots (*)$という条件が無視されているが，これは$u$と$v$がともに連続であるという条件に言い換えられたと考えられる．（例えば$f\l(Z\r) =Z^{-1}$の単位円上の積分を$x=\cos t,y=\sin t$の置換積分により計算してみればわかる．）

結局パラメータ積分を用いる方法ではここまでが限界なのでグリーンの定理や区間縮小法を用いて（妥協しつつ）以下を示すことになる．




$$
\oint_{C} f\l(Z\r) \, dZ=O
$$

コーシーの積分定理により積分の値が経路によらないことを示すことができる．
行列の置換積分を示したい．以降簡単のため複素数$A$の逆行列を$\drac{1}{A}$のように簡略化して表すことにする．

## コーシーの積分公式


$$
f\l(A\r) =\drac{-I}{2\pi }\oint_{C} f\l(Z\r) \l(Z-A\r) ^{-1}\, dZ
$$


### 証明 {#証明 .unnumbered}

$Z=xE+yI+A,x=\cos \theta ,y=\sin \theta$とパラメータ表示することで$C$を中心$A$の円周上の経路として



$$
\oint_{C}^{} \l(Z-A\r) ^{-1}\, dZ=2\pi I
$$
 がわかる．よって



$$
\oint_{C}^{} f\l(Z\r) \l(Z-A\r) ^{-1}\, dZ 
    = \oint_{C} \left\{ f\l(Z\r) -f\l(A\r)  \right\}\l(Z-A\r) ^{-1}\, dZ+2\pi If\l(A\r)
$$
    
であり第一項は$C$の半径$\rho$として$C$上において$\l|f\l(Z\r) -f\l(A\r) \r| <\e$とすると



$$
\l|\oint_{C} \left\{ f\l(Z\r) -f\l(A\r)  \right\}\l(Z-A\r) ^{-1}\, dZ\r| 
    \leq  \oint_{C} \drac{1}{\rho}\e \, dZ=2\pi \rho\drac{1}{\rho}\e=2\pi \e
$$
    
であり，$\e \to 0$で$2\pi \e \to 0$になるので示す等式が得られた．

## 代数学の基本定理

## 留数定理

# 解析的延長

本章では実関数の複素数への拡張が正則なものとして一通りに定まることを示す．\




