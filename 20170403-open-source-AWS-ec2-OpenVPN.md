 <a href="https://www.next-lab.ml/2017/04/open-source-amazon-web-serviceopenvpn.html" target="_blank">網誌文章位址</a>

<a href="https://www.linux.com/blog/ubuntu-1604-lts-now-available-download" style="clear: left; float: left; margin-bottom: 1em; margin-right: 1em;" target="_blank"></a><a href="https://aws.amazon.com/" style="clear: right; float: right; margin-bottom: 1em; margin-left: 1em;" target="_blank"></a><a href="https://openvpn.net/index.php/access-server/docs/admin-guides/182-how-to-connect-to-access-server-with-linux-clients.html" style="clear: left; float: left; margin-bottom: 1em; margin-right: 1em;" target="_blank"><img alt="https://openvpn.net/index.php/access-server/docs/admin-guides/182-how-to-connect-to-access-server-with-linux-clients.html" border="0" height="43" src="https://docs.openvpn.net/wp-content/themes/openvpn/images/OP-Logo.png" width="200" /></a>+<img alt="https://aws.amazon.com/" border="0" height="73" src="https://images-na.ssl-images-amazon.com/images/G/01/webservices/aws_logo._V400518270_.png" width="200" />+<img alt="Xenial" border="0" src="http://www.linuxandubuntu.com/uploads/2/1/1/5/21152474/6886431_orig.png" height="141" width="200" /><br />
<div class="separator" style="clear: both; text-align: center;">
</div>
<div class="separator" style="clear: both; text-align: center;">
</div>
<div class="separator" style="clear: both; text-align: center;">
<a href="https://docs.openvpn.net/wp-content/themes/openvpn/images/OP-Logo.png" imageanchor="1" style="clear: left; float: left; margin-bottom: 1em; margin-right: 1em;"></a></div>
<div class="separator" style="clear: both; text-align: center;">
<a href="http://www.linuxandubuntu.com/uploads/2/1/1/5/21152474/6886431_orig.png" imageanchor="1" style="clear: right; float: right; margin-bottom: 1em; margin-left: 1em;"></a></div>
<br />
<div style="text-align: center;">
<i><b>"Every drop in the ocean counts, and here's mine"</b></i></div>
<div style="text-align: center;">
<i><b><br /></b></i></div>
網路的本質是開放，大多數的在情境下我們總希望我們的網路使用是不會被限制、監控或是管制的條件下使用。最有名的就是中國的網路長城，其次就是每個組織與機關的IT們的各自表述。透過VPN的方式（付費或是免費）是最快的方式，但是最後都會礙於頻寬限制而無法順利的在牆內看到外面的資料。無論是Google 
服務、FB、或是其他影音網頁。以往常見的方式是在家裡的 NAS or WiFi AP上架設VPN 
server，但是如果長時間不在旁邊很難說不會有當機的狀況發生，而且同時也有安全上的疑慮（如果家用網路上設置VPN的server。）當然也可以單純的把家用WiFi
 AP當作VPN Client用，這樣安全性相對高，不過也是需要找個付費或免費的VPN Server（到頭來還是要花一次工？） 
既然都已經在用Ubuntu LTS了（前陣子雖然不慎把他砍掉重練...不對是還原），乾脆就安裝在<a href="https://aws.amazon.com/free/faqs/" target="_blank">12個月免費的AWS</a> <a href="https://aws.amazon.com/ec2/?nc2=h_m1" target="_blank">EC2</a>上。(每個月有750hrs，而且有許多知名的企業都是用這套精簡又24小時不打烊的容器。<br />
<div class="separator" style="clear: both; text-align: center;">
<iframe allowfullscreen="" class="YOUTUBE-iframe-video" data-thumbnail-src="https://i.ytimg.com/vi/TsRBftzZsQo/0.jpg" frameborder="0" height="266" src="https://www.youtube.com/embed/TsRBftzZsQo?feature=player_embedded" width="320"></iframe></div>
<br />
<div class="title-wrapper section">
<div class="row title">
<div class="twelve columns">
<h3 id="What_is_the_AWS_Free_Usage_Tier?">
 <span style="font-size: x-small;"> What is the AWS Free Usage Tier?</span></h3>
</div>
</div>
</div>
<span style="font-size: x-small;">AWS is offering a free usage tier for new AWS customers. Per month, the AWS</span><span style="font-size: x-small;">750 hours of <a href="https://aws.amazon.com/ec2">Amazon EC2</a>&nbsp;Linux
 or RHEL or SLES t2.micro instance usage (1 GiB of memory and 32-bit and
 64-bit platform support) – enough hours to run continuously each month*</span><br />
<br />
所以就著手開始設定。萬事起頭難，花了不少時間在找資料看與try and debug，以下紀錄過程中精簡的步驟，看著照做就可以讓OpenVPN動，或許有一些設定過程會碰到的小問題，相關網誌的連結有的失效了，或許可以參考我測試的方式一步一步過去，最後我這邊是可以所有裝置都順利連入AWS上的OpenVPN。<br />
<br />
第一步到EC2的設定AMI選擇Free (基本上Linux的都是，所以就以常用的Ubuntu Server），<br />
<!--more--><br />
<div class="separator" style="clear: both; text-align: center;">
<a href="https://3.bp.blogspot.com/-S2s2o2b08lI/WOJoQOFjw9I/AAAAAAACclQ/SpvWTqDQmuIAuWdaJ8sOFTiivl6ut7eVQCKgB/s1600/Screenshot%2Bfrom%2B2017-04-02%2B22-50-02.png" imageanchor="1" style="margin-left: 1em; margin-right: 1em;"><img border="0" height="178" src="https://3.bp.blogspot.com/-S2s2o2b08lI/WOJoQOFjw9I/AAAAAAACclQ/SpvWTqDQmuIAuWdaJ8sOFTiivl6ut7eVQCKgB/s320/Screenshot%2Bfrom%2B2017-04-02%2B22-50-02.png" width="320" /></a></div>
第二步是選擇Instance Type:這邊也以free tier 的t2.micro為虛擬主機<br />
<div class="separator" style="clear: both; text-align: center;">
<a href="https://4.bp.blogspot.com/-mjR8JUkkfYE/WOJo57K7tXI/AAAAAAACclU/6W48mP2XSl4uLzyq4uLAUWPFdP_OroiLACKgB/s1600/Screenshot%2Bfrom%2B2017-04-02%2B22-50-32.png" imageanchor="1" style="margin-left: 1em; margin-right: 1em;"><img border="0" height="179" src="https://4.bp.blogspot.com/-mjR8JUkkfYE/WOJo57K7tXI/AAAAAAACclU/6W48mP2XSl4uLzyq4uLAUWPFdP_OroiLACKgB/s320/Screenshot%2Bfrom%2B2017-04-02%2B22-50-32.png" width="320" /></a></div>
第三步將OpenVPN對應的port設定在Security Group（其他頁的都可以直接以Next帶過）<br />
<div class="separator" style="clear: both; text-align: center;">
</div>
<div class="separator" style="clear: both; text-align: center;">
<a href="https://2.bp.blogspot.com/-jAbPj6s7_To/WOJpNidLTtI/AAAAAAACclY/v9vP9zAt3T0CX2oDMG8lEwk81jodcBKCQCKgB/s1600/Screenshot%2Bfrom%2B2017-04-03%2B07-30-26.png" imageanchor="1" style="margin-left: 1em; margin-right: 1em;"><img border="0" height="179" src="https://2.bp.blogspot.com/-jAbPj6s7_To/WOJpNidLTtI/AAAAAAACclY/v9vP9zAt3T0CX2oDMG8lEwk81jodcBKCQCKgB/s320/Screenshot%2Bfrom%2B2017-04-03%2B07-30-26.png" width="320" /></a></div>
第四步.需要Review再確認看有沒有需要付費的資訊(就只是確定Amazon不會順便幫你扣款)<br />
<div class="separator" style="clear: both; text-align: center;">
<a href="https://2.bp.blogspot.com/--FIzDUcxF6U/WOJpNoaisWI/AAAAAAACclY/sPIu7atxSvk7JowCMW54A-xhl4q1temqwCKgB/s1600/Screenshot%2Bfrom%2B2017-04-02%2B22-54-21.png" imageanchor="1" style="margin-left: 1em; margin-right: 1em;"><img border="0" height="179" src="https://2.bp.blogspot.com/--FIzDUcxF6U/WOJpNoaisWI/AAAAAAACclY/sPIu7atxSvk7JowCMW54A-xhl4q1temqwCKgB/s320/Screenshot%2Bfrom%2B2017-04-02%2B22-54-21.png" width="320" /></a></div>
第五步. 設定並下載你主機的金鑰，這個憑證檔就是你連入你的server需要的資料檔<br />
<div class="separator" style="clear: both; text-align: center;">
<a href="https://3.bp.blogspot.com/-KtQWiazKUXM/WOJswl8TG1I/AAAAAAACclg/dCT3Gaka7aomPmomlnX8_eKcgReHEZlxACKgB/s1600/Screenshot%2Bfrom%2B2017-04-02%2B22-55-04.png" imageanchor="1" style="margin-left: 1em; margin-right: 1em;"><img border="0" height="179" src="https://3.bp.blogspot.com/-KtQWiazKUXM/WOJswl8TG1I/AAAAAAACclg/dCT3Gaka7aomPmomlnX8_eKcgReHEZlxACKgB/s320/Screenshot%2Bfrom%2B2017-04-02%2B22-55-04.png" width="320" /></a></div>
<br />
第六步.EC2 Dashboard可以看到有運行中的Ubuntu server了<br />
<div class="separator" style="clear: both; text-align: center;">
<a href="https://4.bp.blogspot.com/-ZiQUKLYHt4o/WOJpNlwFwWI/AAAAAAACclY/mf8tFug6c7UND4Dm9TFngJMLQ3cBvmDsACKgB/s1600/Screenshot%2Bfrom%2B2017-04-02%2B22-49-46.png" style="margin-left: 1em; margin-right: 1em;"><img border="0" height="179" src="https://4.bp.blogspot.com/-ZiQUKLYHt4o/WOJpNlwFwWI/AAAAAAACclY/mf8tFug6c7UND4Dm9TFngJMLQ3cBvmDsACKgB/s320/Screenshot%2Bfrom%2B2017-04-02%2B22-49-46.png" width="320" /></a></div>
<br />
<br />
第六步.SSH連線到IPv4的IP位置（需使用前面下載的PEM 金鑰）P.S.Windows 可用PuttyGen (<a href="https://blog.json.tw/teaching-ten-minutes-to-quickly-build-a-free-amazon-ec2-host" target="_blank">[教學]十分鐘快速建立Amazon EC2免費主機</a>）<br />
開啟終端機，輸入<code class="highlighter-rouge">ssh ubuntu@public_ip -i key.pem</code>，ubuntu為預設登入帳號無需更改，
<code class="highlighter-rouge">public_ip</code> 替換為你的IP，<code class="highlighter-rouge">key.pem</code> 替換為先前下載的key，確認後送出(P.S.如果你的instance是AMI, 則記得將ubuntu改為ec2-user,後來我重新以Amazon Linux AMI 2017.03.0 (HVM)測試其他server時笨很久)：
<br />
<div class="separator" style="clear: both; text-align: center;">
</div>
<br />
<table align="center" cellpadding="0" cellspacing="0" class="tr-caption-container" style="margin-left: auto; margin-right: auto; text-align: center;"><tbody>
<tr><td style="text-align: center;"><a href="https://blog.json.tw/img/post/aws/step9%E9%80%A3%E7%B7%9A.png" imageanchor="1" style="margin-left: auto; margin-right: auto;"><img border="0" height="206" src="https://blog.json.tw/img/post/aws/step9%E9%80%A3%E7%B7%9A.png" width="320" /></a></td></tr>
<tr><td class="tr-caption" style="text-align: center;">忘了截圖...用提到的網誌上的</td></tr>
</tbody></table>
<span style="font-size: small;">第七步.在AWS的主機上面下載並安裝OpenVPN(下載網址先來<a href="http://openvpn.net/index.php/access-server/download-openvpn-as-sw.html" target="_blank">OpenVPN確認版本與路徑</a>),我的是Ubuntu, 就用sudo dpkg -i進行安裝, 結束後他會跳到設定OpenVPN使用的admin密碼</span><br />
<span style="font-size: small;"></span><br />
<div class="separator" style="clear: both; text-align: center;">
</div>
<div class="separator" style="clear: both; text-align: center;">
</div>
<div class="separator" style="clear: both; text-align: center;">
</div>
<div class="separator" style="clear: both; text-align: center;">
</div>
<div class="separator" style="clear: both; text-align: center;">
</div>
<div class="separator" style="clear: both; text-align: center;">
<span style="font-size: small;"><a href="https://3.bp.blogspot.com/-nVK2Ce0rXE0/WOJvIpveGCI/AAAAAAACclo/KTRBBX4s0ooSD6ksY70ZxaLb8_lPXdxawCLcB/s1600/Screenshot%2Bfrom%2B2017-04-02%2B23-35-28%2528Blur%2529.png" imageanchor="1" style="margin-left: 1em; margin-right: 1em;"><img border="0" height="179" src="https://3.bp.blogspot.com/-nVK2Ce0rXE0/WOJvIpveGCI/AAAAAAACclo/KTRBBX4s0ooSD6ksY70ZxaLb8_lPXdxawCLcB/s320/Screenshot%2Bfrom%2B2017-04-02%2B23-35-28%2528Blur%2529.png" width="320" /></a></span></div>
<br />
<span style="font-size: small;">
密碼則須以下指令設定:<br />
<span style="background-color: #cccccc;">passwd openvpn</span><br />
這指令是對 openvpn 這個帳號進行密碼更新，按 enter 後就會看到要輸入新的密碼了<br />
<br />
<span style="background-color: #cccccc;">Enter new UNIX password:</span><br />
<span style="background-color: #cccccc;">Retype new UNIX password:
passwd:&nbsp;</span> </span><br />
<br />
<span style="font-size: small;">第八步. 這邊需要到Amazon EC2設定<a href="http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/elastic-ip-addresses-eip.html#eip-basics" target="_blank">Elastic IP</a>，因為AWS的主機對外的Public IP要與OpenVPN的對應我們才能連入OpenVPN.所以需要在Dashboard確定有沒有對應好</span><br />
&nbsp;-------<br />
這件事在AWS的管理介面中進行，AWS會馬上配發一個Elastic IP，<span style="color: blue;">注意，一定要把這個Elastic IP&nbsp;連結到 openvpn伺服器</span>，才算生效。<br />
---------<br />
第九步.用網頁瀏覽器連入OpenVPN的admin頁面確認有正確運作中<br />
https://Elastic IP:943/admin&nbsp; <br />
<div class="separator" style="clear: both; text-align: center;">
<a href="https://4.bp.blogspot.com/-RGgWBcCw0Pc/WOJxjlTLOII/AAAAAAACcls/f3mUsWr_8RU3G2rEijQN6i67jXPzfKeTQCKgB/s1600/Screenshot%2Bfrom%2B2017-04-03%2B09-00-02.png" imageanchor="1" style="margin-left: 1em; margin-right: 1em;"><img border="0" height="179" src="https://4.bp.blogspot.com/-RGgWBcCw0Pc/WOJxjlTLOII/AAAAAAACcls/f3mUsWr_8RU3G2rEijQN6i67jXPzfKeTQCKgB/s320/Screenshot%2Bfrom%2B2017-04-03%2B09-00-02.png" width="320" /></a></div>
<br />
<div class="separator" style="clear: both; text-align: center;">
</div>
第十步.從要連入該VPN的裝置上連入client頁面(登入後最下面那），<br />
https://Elastic IP:943/<br />
並記得修改config檔(*.ovpn）中的IP成 Elastic IP，而不是原本OpenVPN設定的IP再來使用用裝置上的OpenVPN開啟。(我是用Telegram傳到電腦上修改內容再丟回去行動裝置）<br />
<div class="separator" style="clear: both; text-align: center;">
<a href="https://1.bp.blogspot.com/-yvs1WDVW-sA/WOJyS0BaCNI/AAAAAAACcl4/n1ZPZm5L-aY38kR68Iz1qJRsqs0s-GF3wCKgB/s1600/Screenshot%2Bfrom%2B2017-04-03%2B14-48-01.png" imageanchor="1" style="margin-left: 1em; margin-right: 1em;"><img border="0" height="164" src="https://1.bp.blogspot.com/-yvs1WDVW-sA/WOJyS0BaCNI/AAAAAAACcl4/n1ZPZm5L-aY38kR68Iz1qJRsqs0s-GF3wCKgB/s320/Screenshot%2Bfrom%2B2017-04-03%2B14-48-01.png" width="320" /></a></div>
第11步. 在iPhone 開啟修改為elastic IP後的設定檔連線並測速(原本光纖速度是20/20M, 透過AWS VPN還有10/10M的速度）,同時用<a href="https://whatismyipaddress.com/" target="_blank">WhatIsMyIPAddress</a>查詢也會發現IP已經變成Amazon的.<br />
<div class="separator" style="clear: both; text-align: center;">
<a href="https://1.bp.blogspot.com/-5Icj15nLk1k/WOJ032ht3tI/AAAAAAACcl8/KWi_dA4_L0I8Ok0olxOIaCfF6TjqRlw3QCKgB/s1600/IMG_7064.PNG" imageanchor="1" style="clear: left; float: left; margin-bottom: 1em; margin-right: 1em;"></a><a href="https://1.bp.blogspot.com/-q1LsC28LJ2U/WOJ03-oGJII/AAAAAAACcl8/BSWF2Okd03Izr8zz7iOYdk8jaZP_DDoxgCKgB/s1600/IMG_7065.PNG" imageanchor="1" style="clear: right; float: right; margin-bottom: 1em; margin-left: 1em;"><img border="0" height="320" src="https://1.bp.blogspot.com/-q1LsC28LJ2U/WOJ03-oGJII/AAAAAAACcl8/BSWF2Okd03Izr8zz7iOYdk8jaZP_DDoxgCKgB/s320/IMG_7065.PNG" width="180" /></a><img border="0" height="320" src="https://1.bp.blogspot.com/-5Icj15nLk1k/WOJ032ht3tI/AAAAAAACcl8/KWi_dA4_L0I8Ok0olxOIaCfF6TjqRlw3QCKgB/s320/IMG_7064.PNG" width="180" /></div>
<br />
延伸閱讀：<br />
<ol>
<li><a href="https://docs.openvpn.net/how-to-tutorialsguides/virtual-platforms/amazon-web-services-ec2-tiered-appliance-quick-start-guide/" target="_blank">Amazon Web Services EC2 Tiered Appliance Quick Start Guide</a></li>
<li><a href="http://scl13.com/nas-vpn-server/" target="_blank">NAS VPN 伺服器設定教學, Synology, QNAP, Asustor</a>&nbsp;</li>
<li><a href="https://openvpn.net/index.php/open-source/documentation/howto.html#security" target="_blank">OpenVPN HowTo&nbsp;</a></li>
<li><a href="https://blog.json.tw/teaching-ten-minutes-to-quickly-build-a-free-amazon-ec2-host" target="_blank">&nbsp;[教學]十分鐘快速建立Amazon EC2免費主機</a></li>
<li><a href="http://mackung.blogspot.tw/2012/11/amazon-web-service-openvpn.html" target="_blank">&nbsp; 在 Amazon Web Service 上架設私人的 openvpn 伺服器 </a></li>
<li><a href="https://www.ptt.cc/bbs/iPhone/M.1409162491.A.C10.html" target="_blank">美國Spotify免費服務</a></li>
</ol>
<b><span style="text-decoration: underline;">Windows連線的方式: (參照延伸閱讀1)</span></b><br />
<div class="separator" style="clear: both; text-align: center;">
<a href="https://docs.openvpn.net/wp-content/uploads/2012/04/PuTTYgen.png" imageanchor="1" style="margin-left: 1em; margin-right: 1em;"><img border="0" height="309" src="https://docs.openvpn.net/wp-content/uploads/2012/04/PuTTYgen.png" width="320" /></a></div>
<b><span style="text-decoration: underline;"><br /></span></b>
<b><span style="text-decoration: underline;"><br /></span></b>
<b><span style="text-decoration: underline;">Ubuntu/Debian</span>連線的方式:</b><br />
<br />
<div style="padding-left: 30px;">
<b><span style="font-family: &quot;courier new&quot; , &quot;courier&quot;; font-size: 10pt;"><span style="color: red;">sudo</span> openvpn --config client.ovpn</span></b><br />
<br />
<br />
<div style="text-align: left;">
(2017-04-23) 今天上去查詢Billing 發現有0.01 USD! 流量目前也累計7.8GB了。看起來一直拿來使用當Spotify+AMAZON prime跳板聽音樂跟看電影好像也會多少有影響</div>
<div class="separator" style="clear: both; text-align: center;">
<a href="https://4.bp.blogspot.com/-6WbW5EZxVWk/WPxhoTL1MZI/AAAAAAACeJI/zZcjb72tCW8-TPpvD8RCnFaDI63AjSnhgCKgB/s1600/IMG_7653.PNG" imageanchor="1" style="margin-left: 1em; margin-right: 1em;"><img border="0" height="320" src="https://4.bp.blogspot.com/-6WbW5EZxVWk/WPxhoTL1MZI/AAAAAAACeJI/zZcjb72tCW8-TPpvD8RCnFaDI63AjSnhgCKgB/s320/IMG_7653.PNG" width="180" /></a></div>
<br />
BTW 在使用OpenVPN使用Spotify基本上就跟美國的免費用戶一樣，可以使用所有的功能（包括Running）這對於早起跑步的我還蠻有用的。<br />
<table align="center" cellpadding="0" cellspacing="0" class="tr-caption-container" style="margin-left: auto; margin-right: auto; text-align: center;"><tbody>
<tr><td style="text-align: center;"><a href="https://1.bp.blogspot.com/-bHGWqRlIdDQ/WREmi3pTpwI/AAAAAAACfmE/JtkLcSyh9kEbvSZskpcZmKudTGJEUaWCACKgB/s1600/IMG_8071.PNG" imageanchor="1" style="margin-left: auto; margin-right: auto;"><img border="0" height="320" src="https://1.bp.blogspot.com/-bHGWqRlIdDQ/WREmi3pTpwI/AAAAAAACfmE/JtkLcSyh9kEbvSZskpcZmKudTGJEUaWCACKgB/s320/IMG_8071.PNG" width="180" /></a></td></tr>
<tr><td class="tr-caption" style="text-align: center;">Running</td></tr>
</tbody></table>
<table align="center" cellpadding="0" cellspacing="0" class="tr-caption-container" style="margin-left: auto; margin-right: auto; text-align: center;"><tbody>
<tr><td style="text-align: center;"><a href="https://2.bp.blogspot.com/-jIa7ZdAzmRs/WREmi1KH4zI/AAAAAAACfmE/BHgGcfzi9sISLy_Mk3bMMmJSzS1u7DHQwCKgB/s1600/IMG_8084.JPG" imageanchor="1" style="margin-left: auto; margin-right: auto;"><img border="0" height="240" src="https://2.bp.blogspot.com/-jIa7ZdAzmRs/WREmi1KH4zI/AAAAAAACfmE/BHgGcfzi9sISLy_Mk3bMMmJSzS1u7DHQwCKgB/s320/IMG_8084.JPG" width="320" /></a></td></tr>
<tr><td class="tr-caption" style="text-align: center;">5點的太陽</td></tr>
</tbody></table>
</div>

