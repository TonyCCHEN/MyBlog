<br />
<div class="separator" style="clear: both; text-align: center;">
<a href="https://git-scm.com/images/logo@2x.png" imageanchor="1" style="margin-left: 1em; margin-right: 1em;"><img border="0" src="https://git-scm.com/images/logo@2x.png" /></a></div>
<br />
Git是分散式系統的一種，在Open Source社群、程式開發、PaaS與共享經濟上早已常被使用，但一般人可能比較不常接觸與使用，這邊想說以最無腦的方式為手殘人（如我）做一個防呆機制。 <br />
這裡把想到說要把Blog Post的資料透過類似的方式做版本追蹤，尤其當有時候總會誤砍內容，而過程中使用的指令很單純的就只有以下，不過這裡有個不解之謎就是當以https clone了Repository後，要把東西重新丟上去GitHub時始終卡在無法通過Username/Password認証來git push文章上去(user/password authentication failed)，最後只好重新改以SSH key來Clone(<a href="http://stackoverflow.com/questions/29297154/github-invalid-username-or-password/34919582" target="_blank">StackOverflow</a>)的配套後才順利git push。<br />
<table align="center" cellpadding="0" cellspacing="0" class="tr-caption-container" style="margin-left: auto; margin-right: auto; text-align: center;"><tbody>
<tr><td style="text-align: center;"><a href="https://4.bp.blogspot.com/-UvSegXa08_4/WRA7wwg_cDI/AAAAAAACfiQ/y0CB6UbEPkMJeFLGK6txivjW1fFlfVTfwCKgB/s1600/Screenshot%2Bfrom%2B2017-05-08%2B16-46-16.png" imageanchor="1" style="margin-left: auto; margin-right: auto;"><img border="0" height="224" src="https://4.bp.blogspot.com/-UvSegXa08_4/WRA7wwg_cDI/AAAAAAACfiQ/y0CB6UbEPkMJeFLGK6txivjW1fFlfVTfwCKgB/s400/Screenshot%2Bfrom%2B2017-05-08%2B16-46-16.png" width="400" /></a></td></tr>
<tr><td class="tr-caption" style="text-align: center;">(Screen) git push to repository succeed</td></tr>
</tbody></table>
以下Youtube教學示範了以下指令如何快速的在本機上設定git環境（P.S.照本宣科動手做比自己在那邊看<a href="https://git-scm.com/book/en/v2" target="_blank">ProGit</a>快多了....）：<br />
git init<br />
git status<br />
git add -A<br />
git commit -m "This is to modify something or add something"<br />
git pull<br />
git push<br />
<br /><div class="separator" style="clear: both; text-align: center;">
<iframe allowfullscreen="" class="YOUTUBE-iframe-video" data-thumbnail-src="https://i.ytimg.com/vi/HVsySz-h9r4/0.jpg" frameborder="0" height="266" src="https://www.youtube.com/embed/HVsySz-h9r4?feature=player_embedded" width="320"></iframe></div>
後記：就像這篇文章原本打了大半.....然後手殘......ctrl+A.....del，就全部砍掉重練過....網頁編輯器只有儲存卻沒有版本追蹤真的很不好用阿 0rz
