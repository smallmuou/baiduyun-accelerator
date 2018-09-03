# 百度云加速器 - baiduyun-accelerator

随着百度云限速的到来，速度已经降到100KB/s以内，本工具是为了提升下载速度而生。该工具使用了 HTTP RANGE原理进行分段下载，可以将一个文件分成N块来下载，这样下载速度就有可能提升最大N倍

### 使用

下载baiduyun-accelerator至本地

```bash
/bin/bash baiduyun-accelerator redirection-url [split-number]

redirection-url是重定向的下载地址，可以在浏览器中点击下载，在下载队列 - 详情中找到Redirection
split-number是分块的数目，默认10个；理论上配置越大越好，但要考虑时间CPU、文件大小、带宽，因此配置越大，下载速度并不一定越大，具体可以在时间网络中测试。
```

### 对比结果

单个（浏览器）下载速度
```bash
smou:baiduyun-accelerator $ /bin/bash baiduyun-accelerator 'https://d11.baidupcs.com/file/1775ee70ef849f6b442c7540868a3f25?bkt=p3-00008c600f8c69bb2150622466d47de9ab8a&xcode=671f0e660fc919180776ea6ad9d4e9bcd63f0c04783d1f719cd11a99d56a137169272f8fe280ef0947ee41204567a91c&fid=87338191-250528-212614922664897&time=1535955568&sign=FDTAXGERLQBHSK-DCb740ccc5511e5e8fedcff06b081203-X8HP4ShkOgbIadwToFqXzXHoTwU%3D&to=d11&size=24908868&sta_dx=24908868&sta_cs=177437&sta_ft=ape&sta_ct=6&sta_mt=6&fm2=MH%2CYangquan%2CAnywhere%2C%2Cfujian%2Cct&resv0=cdnback&resv1=0&vuk=282335&iv=0&htype=&newver=1&newfm=1&secfm=1&flow_ver=3&pkey=00008c600f8c69bb2150622466d47de9ab8a&sl=76480590&expires=8h&rt=sh&r=233439886&mlogid=9154848837080176738&vbdid=3049029286&fin=%E8%AF%B4%E6%95%A3%E5%B0%B1%E6%95%A3-%E5%89%8D%E4%BB%BB3.ape&fn=%E8%AF%B4%E6%95%A3%E5%B0%B1%E6%95%A3-%E5%89%8D%E4%BB%BB3.ape&rtype=1&dp-logid=9154848837080176738&dp-callid=0.1.1&hps=1&tsl=80&csl=80&csign=ZMLyV6T0L9zkkwFfMOo%2F4sxc4LA%3D&so=0&ut=6&uter=4&serv=0&uc=359584213&ti=26fa64dbec28822482b9f079f8a5dcf2fbcbbbe60893ad2e305a5e1275657320&by=themis' 1
Progress: 0%     0KB/s
Progress: 0%     84KB/s
Progress: 0%     112KB/s
Progress: 1%     64KB/s
Progress: 1%     64KB/s
Progress: 1%     128KB/s
Progress: 2%     64KB/s
Progress: 2%     100KB/s
Progress: 2%     64KB/s
Progress: 3%     64KB/s
Progress: 3%     64KB/s
Progress: 3%     128KB/s
Progress: 4%     64KB/s
Progress: 4%     64KB/s
Progress: 4%     100KB/s
Progress: 5%     64KB/s
Progress: 5%     128KB/s
```

提速下载（10个分块）结果

```bash
smou:baiduyun-accelerator $ /bin/bash baiduyun-accelerator 'https://d11.baidupcs.com/file/1775ee70ef849f6b442c7540868a3f25?bkt=p3-00008c600f8c69bb2150622466d47de9ab8a&xcode=671f0e660fc919180776ea6ad9d4e9bcd63f0c04783d1f719cd11a99d56a137169272f8fe280ef0947ee41204567a91c&fid=87338191-250528-212614922664897&time=1535955568&sign=FDTAXGERLQBHSK-DCb740ccc5511e5e8fedcff06b081203-X8HP4ShkOgbIadwToFqXzXHoTwU%3D&to=d11&size=24908868&sta_dx=24908868&sta_cs=177437&sta_ft=ape&sta_ct=6&sta_mt=6&fm2=MH%2CYangquan%2CAnywhere%2C%2Cfujian%2Cct&resv0=cdnback&resv1=0&vuk=282335&iv=0&htype=&newver=1&newfm=1&secfm=1&flow_ver=3&pkey=00008c600f8c69bb2150622466d47de9ab8a&sl=76480590&expires=8h&rt=sh&r=233439886&mlogid=9154848837080176738&vbdid=3049029286&fin=%E8%AF%B4%E6%95%A3%E5%B0%B1%E6%95%A3-%E5%89%8D%E4%BB%BB3.ape&fn=%E8%AF%B4%E6%95%A3%E5%B0%B1%E6%95%A3-%E5%89%8D%E4%BB%BB3.ape&rtype=1&dp-logid=9154848837080176738&dp-callid=0.1.1&hps=1&tsl=80&csl=80&csign=ZMLyV6T0L9zkkwFfMOo%2F4sxc4LA%3D&so=0&ut=6&uter=4&serv=0&uc=359584213&ti=26fa64dbec28822482b9f079f8a5dcf2fbcbbbe60893ad2e305a5e1275657320&by=themis' 10
Progress: 0%     0KB/s
Progress: 2%     680KB/s
Progress: 5%     648KB/s
Progress: 8%     716KB/s
Progress: 11%    832KB/s
Progress: 14%    760KB/s
Progress: 17%    700KB/s
Progress: 21%    928KB/s
Progress: 23%    556KB/s
Progress: 28%    1000KB/s
Progress: 31%    760KB/s
Progress: 34%    708KB/s
Progress: 37%    844KB/s
Progress: 40%    744KB/s
Progress: 43%    808KB/s
Progress: 47%    772KB/s
Progress: 51%    1096KB/s
Progress: 53%    580KB/s
```

PS: 可以看出速度提升了8-9倍

