<br />
<div class="separator" style="clear: both; text-align: center;">
<a href="https://git-scm.com/images/logo@2x.png" imageanchor="1" style="margin-left: 1em; margin-right: 1em;"><img border="0" src="https://git-scm.com/images/logo@2x.png" /></a></div>
<br />
<a href="http://dylandy.github.io/Easy-Git-Tutorial/" target="_blank">Git是分散式系統</a>的一種，在Open Source社群、程式開發、PaaS與共享經濟上早已常被使用，但一般人可能比較不大有感覺要如何使用，這邊想說將Git作為手殘人（如我）的保護機制。過程中就一直同步把文章的HTML格式Ctrl+A,C的方式貼到Git目錄下的一份文件(.md)做同步，同時也讓手機上可以編輯文章（blogger的編輯對於行動裝置的支援真的讓人傻眼.....希望晚點測試在iOS上的Safari或APP有比較好用 .)&nbsp; 於是參考Youtube開始動手把Blog Post透過類似的方式做版本追蹤，理想是做到像<a href="http://stackoverflow.com/questions/29297154/github-invalid-username-or-password/34919582" target="_blank">StackOverflow</a>、<a href="https://en.wikipedia.org/wiki/Main_Page" target="_blank">WIKIPEDIA</a>讓別人協助更新內容。<br />
<br />
git環境設定好之後，使用到的指令順序如以下： <br />
<ol>
<li>git status</li>
<li>git add -A</li>
<li>git commit -m "This is to modify something or add something"</li>
<li>git pull</li>
<li>git push</li>
</ol>
&nbsp;（P.S.邊看邊動手做比自己在那邊慢慢看<a href="https://git-scm.com/book/en/v2" target="_blank">ProGit</a>快多了....）<br />
<div class="separator" style="clear: both; text-align: center;">
<iframe allowfullscreen="" class="YOUTUBE-iframe-video" data-thumbnail-src="https://i.ytimg.com/vi/HVsySz-h9r4/0.jpg" frameborder="0" height="266" src="https://www.youtube.com/embed/HVsySz-h9r4?feature=player_embedded" width="320"></iframe></div>
不過這裡有個二階段認証導致以https
 clone Repository後，要把東西重新丟上去GitHub時始終卡在無法通過Username/Password認証來git 
push文章上去（<a href="http://stackoverflow.com/questions/29297154/github-invalid-username-or-password/34919582" target="_blank">StackOverflow</a>），最後只好重新改以SSH 
key來Clone Repo後才順利git push<br />
<br />
後記：就像這篇文章原本打了大半.....然後手殘......ctrl+A.....del，就全部砍掉重練過....然後又經歷編輯時東西消失出現儲存中發生錯誤......blogger編輯器很不好用阿
  為什麼不像Goodle Docs/Sheet..0rz <br />
<table align="center" cellpadding="0" cellspacing="0" class="tr-caption-container" style="margin-left: auto; margin-right: auto; text-align: center;"><tbody>
<tr><td style="text-align: center;"><a href="https://4.bp.blogspot.com/-UvSegXa08_4/WRA7wwg_cDI/AAAAAAACfiQ/y0CB6UbEPkMJeFLGK6txivjW1fFlfVTfwCKgB/s1600/Screenshot%2Bfrom%2B2017-05-08%2B16-46-16.png" style="margin-left: auto; margin-right: auto;"><img border="0" height="224" src="https://4.bp.blogspot.com/-UvSegXa08_4/WRA7wwg_cDI/AAAAAAACfiQ/y0CB6UbEPkMJeFLGK6txivjW1fFlfVTfwCKgB/s400/Screenshot%2Bfrom%2B2017-05-08%2B16-46-16.png" width="400" /></a></td></tr>
<tr><td class="tr-caption" style="text-align: center;">(Screen) git push to repository succeed</td></tr>
</tbody></table>
<br />
<br />
<br />
<br />
延伸閱讀：<br />
<ol>
<li><a href="https://www.slant.co/topics/1429/~github-clients-for-ios" target="_blank">&nbsp;5 Best GitHub client for iOS as of 2017</a></li>
<li><a href="https://guides.github.com/activities/hello-world/" target="_blank">GitHub Hello World</a>&nbsp;</li>
<li><a href="https://help.github.com/articles/connecting-to-github-with-ssh/" target="_blank">Connecting to GitHub with SSH - User Documentation - GitHub Help</a></li>
<li><a href="https://help.github.com/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent/" target="_blank">&nbsp; Generating a new SSH key and adding it to the ssh-agent(Linux)</a></li>
</ol>
<div style="max-width: 560;">
<div style="height: 0; padding-bottom: 56.25%; position: relative;">
<iframe allowfullscreen="" frameborder="0" height="315" scrolling="no" src="https://embed.ted.com/talks/jonathan_zittrain_the_web_is_a_random_act_of_kindness" style="height: 100%; left: 0; position: absolute; top: 0; width: 100%;" width="560"></iframe></div>
</div>
（網路的生命期愈來愈短了,人所擁有的事物也是..... "Put yourself in others' shoes")
