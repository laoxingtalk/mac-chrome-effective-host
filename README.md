### mac-chrome-effective-host 能干什么:
在开发或测试过程中需要经常切换 Host，在Mac下原来自己的方案是 SwitchHosts + Firefox + HostAdmin 插件，切换 Host后Firefox能够及时生效。Mac下Firefox很卡很慢，相比之下Chrome流畅很多，但Chrome找不到像Firefox下HostAdmin一样好用的插件，网上给的解决方案是 

- Navigate to chrome://net-internals/#dns and click "Clear Host Cache" 
- Navigate to chrome://net-internals/#sockets and click "Flush Socket Pools"

每次切Host后还要手动这么来一下，很是奔溃。

boreas320 写了个AppleScript https://github.com/boreas320/chrome_hosts_flush_util 但是用不了。

mac-chrome-effective-host 中 effective_chrome_host.applescript 是对 chrome_hosts_flush_util 中的修改，使在Mac下修改了Host文件后Chrome能及时生效。

### mac-chrome-effective-host 如何使用:
方案是 SwitchHosts + cmd (cflush) + Chrome
> cd /opt 

> git clone https://github.com/xburning/mac-chrome-effective-host.git 

> cd mac-chrome-effective-host 

> chmod 755 effective_chrome_host.applescript 

> vim ~/.zshrc (install "oh-my-zsh" before https://github.com/robbyrussell/oh-my-zsh) 

> alias cflush="/opt/mac-chrome-effective-host/effective_chrome_host.applescript" 

