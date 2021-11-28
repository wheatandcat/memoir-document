---
theme: ./theme
title: 振り返りアプリを作ってみた話
class: text-center
highlighter: shiki
lineNumbers: false
info: |
  ## 振り返りアプリを作ってみた話

  Learn more at [memoirの開発ログ](https://zenn.dev/wheatandcat/scraps/78d2c5aa4c9435)
drawings:
  persist: false
fonts:
  sans: Noto Sans Japanese
  serif: Roboto Slab
  mono: Fira Code
---

<div class="flex justify-center">
  <img
    class="w-60"
    src="/logo.svg"
  />
</div>
<br/>
<br/>
<br/>
<h2 class="font-sans">振り返りアプリを作ってみた話</h2>

<br/>
<br/>
- タスクを記録して可視化する。行動ログのメモアプリ -


<!--
The last comment block of each slide will be treated as slide notes. It will be visible and editable in Presenter Mode along with the slide. [Read more in the docs](https://sli.dev/guide/syntax.html#notes)
-->

---

<div class="flex pb-5">
  <div class="px-5">
    <div class="rounded-full bg-white w-30 h-30 overflow-hidden border-2 border-black border-dotted border-opacity-20">
      <img
        class="w-40 pt-2"
        src="/account.png"
      />
    </div>
  </div>
  <div class="mt-6">
    <h2>自己紹介</h2>
  </div>
</div>
<br />

- 📝 飯野陽平（[wheatandcat](https://github.com/wheatandcat)）
- 🏢 フリーランスエンジニア（シェアフル株式会社CTO）
- 💻 Blog: https://www.wheatandcat.me/
- 📚 Booth: https://wheatandcat.booth.pm/
- 🛠 今までに作ったもの
  - [memoir](https://memoir-lp-mvbeacmwe-wheatandcat.vercel.app/)
  - [ペペロミア](https://peperomia.app/)
  - [Atomic Design Check List](https://atomic-design-checklist.vercel.app/)

---

# memoirって、どんなアプリ？


<div class="text-2xl font-700 absolute top-60 left-25">
タスクを記録して可視化する、<br/>
行動ログのメモアプリです。
</div>

<img
  class="w-120 absolute top-35 right-40"
  src="/mock01.png"
/>
<img
  class="w-120 absolute top-35 right-0"
  src="/mock02.png"
/>


---

# どんな体制で開発している？


<div>
  <div class="flex justify-around mt-20 w-220">
    <div class="flex justify-center flex-col">
      <div>
        <div class="rounded-full bg-white w-40 h-40 overflow-hidden border-2 border-black border-dotted border-opacity-20">
          <img
            class="w-40 pt-2"
            src="/account.png"
          />
        </div>
      </div>
      <div class="pt-3 text-center text-xl">
        <p><span class="font-700">wheatandcat</span></p>
        <p><span class="font-700">開発</span></p>
      </div>
    </div>
    <div class="flex justify-center flex-col">
      <div>
        <div class="rounded-full bg-white w-40 h-40 overflow-hidden border-2 border-black border-dotted border-opacity-20">
          <img
            class="w-40 pt-2"
            src="/mitsubisi.png"
          />
        </div>
      </div>
      <div class="pt-3 text-center text-xl">
        <p><span class="font-700">mitsubisi</span></p>
        <p><span class="font-700">デザイン</span></p>
      </div>
    </div>
  </div>
</div>

---

<div class="text-4xl font-700 title">
どんな感じで開発を始めたか？
</div>

<style>
.title {
  display: flex;
  height: 100%;
  width: 100%;
  justify-content: center;
  align-items: center;
}
</style>

---
clicks: 1
---

## 元々、以下のような事を行っていた


<arrow v-click="1" x1="450" y1="330" x2="550" y2="330" color="#46AE35" width="3" arrowSize="1" />
<br/>
<br/>
<div class="flex justify-between w-210">
  <div>
    <div>
      <div class="text-xl font-700">①.毎週日曜日の午後に振り返り</div>
      <p class="text-sm font-700">
        参加者: 家族<br/>
        お互いの１週間の出来事を共有
      </p>
    </div>
    <div>
      <img
        class="h-70 pt-2"
        src="/memo01.png"
      />
    </div>
  </div>
  <div v-click="1">
    <div>
      <div class="text-xl font-700">②.議事録を家族共有のslackで共有</div>
      <div class="h-19"/>
    </div>
    <div>
      <img
        class="h-70 pt-2"
        src="/memo02.png"
      />
    </div>
  </div>
</div>

---

# 元々の運用の振り返りの問題点

<br/>
<br/>

 - 振り返りの時に、今週の出来事を思い出せない
 - まとまった単位での振り返りをしたい時にテキスト情報のみだとピックアップしづらい
 - 良かった出来事のみピックアップしたい
 - 振り返りを開催する時間帯がズレる

<br />
<br />

<div v-click="1" class="text-center mt-10 text-4xl font-700 strong">
  上記の問題を解決するためにアプリを開発！
</div>

<style>
.strong {
  color: #E93581;
}
</style>


---
clicks: 3
---


# どんな感じで開発を始めたか ①

<div class="text-sm">担当: wheatandcat</div>

<div class="relative">
    <div class="absolute top-0 left-0 right-0 bottom-0 w-80">
      <p class="text-base font-700">①.ラフで画面構成を作成</p>
      <img
        class="h-30"
        src="/create_01.png"
      />
    </div>
    <div v-click="1" class="absolute top-0 left-90 bottom-0 w-80">
      <p class="text-base font-700">②.Figmaで仮デザイン作成</p>
      <img
        class="h-30"
        src="/create_02.png"
      />
    </div>
    <div v-click="2" class="absolute top-50 left-0 bottom-0 w-80">
      <p class="text-base font-700">③.仮のデザインガイドラインを作成</p>
      <img
        class="h-30"
        src="/create_03.png"
      />
    </div>
    <div v-click="3" class="absolute top-65 left-115 bottom-0 w-80 h-25 border-3 border-gray-700 border-dotted rounded-lg">
      <p class="text-lg font-700 pt-5 pl-4 text-gray-700">ここまで出来たらデザイナーに渡す</p>
    </div>
</div>

<arrow v-click="1" x1="280" y1="205" x2="400" y2="205" color="#46AE35" width="3" arrowSize="1" />
<arrow v-click="2" x1="400" y1="260" x2="300" y2="325" color="#46AE35" width="3" arrowSize="1" />
<arrow v-click="3" x1="280" y1="430" x2="500" y2="430" color="#46AE35" width="3" arrowSize="1" />


---
clicks: 6
---

# どんな感じで開発を始めたか ②

<div class="text-sm">担当: mitsubisi</div>


<div class="relative">
    <div class="absolute top-0 left-0 right-0 bottom-0">
      <p class="text-base font-700">④.正式にデザインガイドラインを作成</p>
      <img
        class="h-60"
        src="/create_04.png"
      />
    </div>
    <div  v-click="1" class="absolute top-0 left-110 bottom-0 w-80">
      <p class="text-base font-700">⑤.StyleをFigmaに登録</p>
      <img
        class="h-60"
        src="/create_05.png"
      />
    </div>
    <div v-click="2" v-if="$slidev.nav.clicks == 2" class="absolute top-20 left-5 right-0 bottom-0 w-25 h-32 border-3 border-red-700"/>
    <div v-click="3" v-if="$slidev.nav.clicks === 3" class="absolute top-20 left-48 right-0 bottom-0 w-15 h-18 border-3 border-red-700"/>
    <div v-click="4" class="absolute top-15 left-170 bottom-0 w-80">
      <img
        class="h-60"
        src="/create_06.png"
      />
    </div>

</div> 

<arrow v-click="1" v-if="$slidev.nav.clicks === 1" x1="340" y1="305" x2="480" y2="305" color="#46AE35" width="3" arrowSize="1" />
<arrow v-click="2" v-if="$slidev.nav.clicks === 2" x1="175" y1="260" x2="490" y2="360" color="rgba(185, 28, 28)" width="3" arrowSize="1" />
<arrow v-click="3" v-if="$slidev.nav.clicks === 3" x1="305" y1="245" x2="490" y2="245" color="rgba(185, 28, 28)" width="3" arrowSize="1" />
<arrow v-click="5"  v-if="$slidev.nav.clicks === 5" x1="560" y1="230" x2="870" y2="300" color="rgba(185, 28, 28)" width="3" arrowSize="1" />
<arrow v-click="6"  v-if="$slidev.nav.clicks === 6" x1="560" y1="335" x2="870" y2="370" color="rgba(185, 28, 28)" width="3" arrowSize="1" />
---

# どんな感じで開発を始めたか ③

<div class="text-sm">担当: mitsubisi</div>


<p class="text-base font-700 pl-18">⑥.ガイドラインに沿って正式なデザインを作成</p>
<div class="flex items-center w-full flex-col">
  <img
    class="w-180"
    src="/create_07.png"
  />
</div> 
---

# どんな感じで開発を始めたか ④

<div class="text-sm">担当: wheatandcat & mitsubisi</div>


<p class="text-base font-700 pl-18">⑥.画面遷移をPrototypeに落とし込む</p>
<div class="flex pl-20 w-full flex-col">
  <img
    class="w-140"
    src="/create_08.png"
  />
</div> 

Prototype **[Demo](https://www.figma.com/proto/cLruhS5vc5IQsvqoXYSyP8/memoir?page-id=141%3A129&node-id=141%3A273&viewport=241%2C48%2C0.5&scaling=min-zoom&starting-point-node-id=141%3A273)** .
---

# ここまで完成したら実装開始 & 改善のループを開始

<div class="text-sm">担当: wheatandcat & mitsubisi</div>
<br/>

 <ul>
  <li>以下をループでする形式で実装していく
    <ul>
      <li v-click="1">①. 設計 & 機能実装</li>
      <li v-click="2">②. Expoでデモアプリ配布して、実際に使用</li>
      <li v-click="3">③. 週1回の振り返りを行う</li>
      <li v-click="4">④. 改善内容 & バグ報告をslackに通知</li>
      <li v-click="5">⑤. issue作成</li>
      <li v-click="6">⑥. Zennのスクラップに実装報告を記載</li>
      <li v-click="7">⑦. ①に戻る</li>
    </ul>
  </li>
</ul>
<br/>

Zenn: **[memoirの開発ログ](https://zenn.dev/wheatandcat/scraps/78d2c5aa4c9435)** .

---

# どこまで出来ているの？

<div class="text-4xl font-700 title">
実機でデモ
</div>

 **[LPサイトは、こちら](https://memoir-lp-mvbeacmwe-wheatandcat.vercel.app/)** .

<style>
.title {
  display: flex;
  height: 80%;
  width: 100%;
  justify-content: center;
  align-items: center;
  color: #46AE35;
}
</style>
---




# コードは全てGitHubで公開しています

<br/>

 - memoir
   - **https://github.com/wheatandcat/memoir**
 - memoir-backend
   - **https://github.com/wheatandcat/memoir-backend**
 - memoir-notification
   - **https://github.com/wheatandcat/memoir-notification**
 - memoir-tools
   - **https://github.com/wheatandcat/memoir-tools**
 - memoir-lp
   - **https://github.com/wheatandcat/memoir-lp**
---




<div class="text-2xl font-700 title">
アプリのストア公開は来年の2月くらいの予定です
</div>

<style>
.title {
  display: flex;
  height: 100%;
  width: 100%;
  justify-content: center;
  align-items: center;
}
</style>
---
layout: center
class: "text-center"
---

<div class="text-2xl font-700 text-enter w-full">
  <div>ご清聴ありがとうございました</div>
</div>



<style>
.main {
  display: flex;
  height: 80%;
  width: 100%;
  justify-content: center;
  align-items: center;
  color: #46AE35;
}
</style>

