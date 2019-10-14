<h2>简介</h2><br>
免费接入微信登录接口获取openid<br>
（无须申请，直接调用，适合web、pc、手机端，全平台兼容）<br>
无缝衔接微信获取openid、微信头像地址、微信昵称信息<br>
拿到openid之后，就可以自行操作更多身份验证的事情啦~~~<br>
<h2>1.获取临时编码和微信登录二维码base64图片</h2><br>
<code>调用地址：https://www.qijinlai.com/wxlogin/wxlogin.php</code><br>
将得到以下json（字符串）内容。<br>
其中webcode为临时编码（下面需要用这个临时编码获取用户是否登录和登录信息）；<br>
其中imgbase64code为微信登录二维码base64图片（如何使用base64图片请自行百度）；<br>
示例如下显示：<br>
{"webcode":"20191013165730**********","imgbase64code":"data:image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAQAB"}<br>
<img class="alignnone size-full wp-image-327" src="https://raw.githubusercontent.com/929355193/wxopenid/master/1.jpg" alt="" width="596" height="130" /><br>
<h2>2.第一步获取到二维码图片地址之后，自行用base64转化为图片，然后打开微信扫一扫登录</h2><br>
<img class="alignnone size-full wp-image-331" src="https://raw.githubusercontent.com/929355193/wxopenid/master/2.jpg" alt="" width="310" height="302" /><br>
<img class="alignnone wp-image-332 size-medium" src="https://raw.githubusercontent.com/929355193/wxopenid/master/3.jpg" alt="" width="138" height="300" /><br>
<img class="alignnone wp-image-333 size-medium" src="https://raw.githubusercontent.com/929355193/wxopenid/master/4.jpg" alt="" width="138" height="300" /><br>
<img class="alignnone wp-image-334 size-medium" src="https://raw.githubusercontent.com/929355193/wxopenid/master/5.jpg" alt="" width="138" height="300" /><br>
<h2>3.根据上面步骤获取到的webcode临时编码，调用以下地址，用来获取是否登录以及登录信息</h2><br>
<code>调用地址：https://www.qijinlai.com/wxlogin/wxlogincheck.php?webcode=****************</code><br>
将得到以下json（字符串）内容。<br>
其中state为状态参数，判断是否登录（0=未登录；1=登录）；<br>
其中webcode为上方临时编码参数；<br>
其中openid为用户唯一编码值（不会和别人重复，是该用户身份和微信的id凭证，一一对应）；如果获取到0，则未登录；<br>
其中nicheng为用户微信昵称；如果获取到0，则未登录；<br>
其中touxian为用户微信头像url地址；如果获取到0，则未登录；<br>
其中logintime为用户登录的时间；如果获取到0，则未登录；<br>
示例如下显示：<br>
{"state":"0","webcode":"20191013*******","openid":"0","nicheng":"0","touxiang":"0","logintime":"0"}<br>
{"state":"1","openid":"oCcAQ5S59***********","nicheng":"*********","touxiang":"https://wx.qlogo.cn/mmopen/vi_32/*************","logintime":"2019-01-01 16:59:16"}<br>
<img class="alignnone size-full wp-image-328" src="https://raw.githubusercontent.com/929355193/wxopenid/master/6.jpg" alt="" width="625" height="205" /> <img class="alignnone size-full wp-image-329" src="https://raw.githubusercontent.com/929355193/wxopenid/master/7.jpg" alt="" width="794" height="227" /><br>
欢迎大家有问题bug直接Issues反馈(*^__^*)<br>
<a href="https://www.dongganboy.com/wxlogin.php">演示DEMO</a>
