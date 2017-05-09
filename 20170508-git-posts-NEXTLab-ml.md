[網誌文章位址](https://www.next-lab.ml/2017/05/open-souce-gitmyblog-posts.html)

<div class="separator" style="clear: both; text-align: center;">
[![](https://git-scm.com/images/logo@2x.png)](https://git-scm.com/images/logo@2x.png)</div>

[Git是分散式系統](http://dylandy.github.io/Easy-Git-Tutorial/)的一種，在Open Source社群、程式開發、PaaS與共享經濟上早已常被使用，但一般人可能比較不大有感覺要如何使用，這邊想說將Git作為手殘人（如我）的保護機制。過程中就一直同步把文章的HTML格式Ctrl+A,C的方式貼到Git目錄下的一份文件(.md)做同步，同時也讓手機上可以編輯文章（blogger的編輯對於行動裝置的支援真的讓人傻眼.....希望晚點測試在iOS上的Safari或APP有比較好用 .)&nbsp; 於是參考Youtube開始動手把Blog Post透過類似的方式做版本追蹤，理想是做到像[StackOverflow](http://stackoverflow.com/questions/29297154/github-invalid-username-or-password/34919582)、[WIKIPEDIA](https://en.wikipedia.org/wiki/Main_Page)讓別人協助更新內容。

<table align="center" cellpadding="0" cellspacing="0" class="tr-caption-container" style="margin-left: auto; margin-right: auto; text-align: center;"><tbody>
<tr><td style="text-align: center;">[![](https://4.bp.blogspot.com/-s7rdjYvusuY/WRBqIyoHbaI/AAAAAAACfj8/O7d2KD2HsWMjhv7kuOj25PoCRQbjCY0pwCKgB/s320/Screenshot%2Bfrom%2B2017-05-08%2B17-50-02.png)](https://4.bp.blogspot.com/-s7rdjYvusuY/WRBqIyoHbaI/AAAAAAACfj8/O7d2KD2HsWMjhv7kuOj25PoCRQbjCY0pwCKgB/s1600/Screenshot%2Bfrom%2B2017-05-08%2B17-50-02.png)</td></tr>
<tr><td class="tr-caption" style="text-align: center;">在gedit文字編輯器看HTML的樣子</td></tr>
</tbody></table>
git環境設定好之後，使用到的指令順序如以下(這邊直接用 master)：

1.  git status
2.  git add -A
3.  git commit -m "This is to modify something or add something"
4.  git pull
5.  git push
&nbsp;（P.S.邊看邊動手做比自己在那邊慢慢看[ProGit](https://git-scm.com/book/en/v2)快多了....）

<div class="separator" style="clear: both; text-align: center;">
<iframe allowfullscreen="" class="YOUTUBE-iframe-video" data-thumbnail-src="https://i.ytimg.com/vi/HVsySz-h9r4/0.jpg" frameborder="0" height="266" src="https://www.youtube.com/embed/HVsySz-h9r4?feature=player_embedded" width="320"></iframe></div>
<!--more-->

不過這裡有個二階段認証的問題，導致以https
 clone Repository後，要把東西重新丟上去GitHub時始終卡在無法通過Username/Password認証來git
push文章上去（[StackOverflow](http://stackoverflow.com/questions/29297154/github-invalid-username-or-password/34919582)），最後只好重新改以SSH
key來Clone Repo後才順利git push。另外在文章的格式上面需要注意的是如果以html儲存會無法閱讀，需要透過類似這個GitHub提供的([GitHub &amp; BitBucket HTML Preview](https://github.com/htmlpreview/htmlpreview.github.com))才能預覽內容，所以.....在這邊乾脆直接以.md格式來命名存在本機上的檔案. 同時找到一個好工具可以將[HTML轉換為MarkDown](http://www.atool.org/html2markdown.php)

[ (Repository) TonyCChen/MyBlog](https://github.com/TonyCCHEN/MyBlog)

<table align="center" cellpadding="0" cellspacing="0" class="tr-caption-container" style="margin-left: auto; margin-right: auto; text-align: center;"><tbody>
<tr><td style="text-align: center;">[![](https://4.bp.blogspot.com/-UvSegXa08_4/WRA7wwg_cDI/AAAAAAACfiQ/y0CB6UbEPkMJeFLGK6txivjW1fFlfVTfwCKgB/s400/Screenshot%2Bfrom%2B2017-05-08%2B16-46-16.png)](https://4.bp.blogspot.com/-UvSegXa08_4/WRA7wwg_cDI/AAAAAAACfiQ/y0CB6UbEPkMJeFLGK6txivjW1fFlfVTfwCKgB/s1600/Screenshot%2Bfrom%2B2017-05-08%2B16-46-16.png)</td></tr>
<tr><td class="tr-caption" style="text-align: center;">(Screen) git push to repository succeed</td></tr>
</tbody></table>
<table align="center" cellpadding="0" cellspacing="0" class="tr-caption-container" style="margin-left: auto; margin-right: auto; text-align: center;"><tbody>
<tr><td style="text-align: center;">[![](https://4.bp.blogspot.com/-rkEMpZcEHa0/WRBp1FqjnLI/AAAAAAACfjg/zGXTl_yoltMSObA-0NJkp_As_p7mFwQWACKgB/s320/Screenshot%2Bfrom%2B2017-05-08%2B18-29-29.png)](https://4.bp.blogspot.com/-rkEMpZcEHa0/WRBp1FqjnLI/AAAAAAACfjg/zGXTl_yoltMSObA-0NJkp_As_p7mFwQWACKgB/s1600/Screenshot%2Bfrom%2B2017-05-08%2B18-29-29.png)</td></tr>
<tr><td class="tr-caption" style="text-align: center;">Blog post在GitHub看的樣子</td></tr>
</tbody></table>

<table align="center" cellpadding="0" cellspacing="0" class="tr-caption-container" style="margin-left: auto; margin-right: auto; text-align: center;"><tbody>
<tr><td style="text-align: center;">[![](https://2.bp.blogspot.com/-JpicoG4gBCs/WRBp1HaJX-I/AAAAAAACfjg/FgBQOl9tJY0lwWp7hr-0nupKyROUpsftwCKgB/s320/Screenshot%2Bfrom%2B2017-05-08%2B18-29-36.png)](https://2.bp.blogspot.com/-JpicoG4gBCs/WRBp1HaJX-I/AAAAAAACfjg/FgBQOl9tJY0lwWp7hr-0nupKyROUpsftwCKgB/s1600/Screenshot%2Bfrom%2B2017-05-08%2B18-29-36.png)</td></tr>
<tr><td class="tr-caption" style="text-align: center;">編輯歷史可以看到已經編輯了幾次與修改哪些地方</td></tr>
</tbody></table>
<span id="goog_386113051"></span><span id="goog_386113052"></span>

延伸閱讀：

1.  [&nbsp;5 Best GitHub client for iOS as of 2017](https://www.slant.co/topics/1429/~github-clients-for-ios)
2.  [GitHub Hello World](https://guides.github.com/activities/hello-world/)&nbsp;
3.  [Connecting to GitHub with SSH - User Documentation - GitHub Help](https://help.github.com/articles/connecting-to-github-with-ssh/)
4.  [&nbsp; Generating a new SSH key and adding it to the ssh-agent(Linux)](https://help.github.com/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent/)
<div style="max-width: 560;">
<div style="height: 0; padding-bottom: 56.25%; position: relative;">
<iframe allowfullscreen="" frameborder="0" height="315" scrolling="no" src="https://embed.ted.com/talks/jonathan_zittrain_the_web_is_a_random_act_of_kindness" style="height: 100%; left: 0; position: absolute; top: 0; width: 100%;" width="560"></iframe></div>
</div>
（網路的生命期愈來愈短了,人所擁有的事物也是..... "Put yourself in others' shoes")

文末：就像這篇文章原本打了大半.....然後手殘......ctrl+A.....del，就全部砍掉重練過....然後又經歷編輯時東西消失出現儲存中發生錯誤......blogger編輯器很不好用阿
  為什麼不像Goodle Docs/Sheet..0rz&nbsp; 
