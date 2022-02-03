# Chromium-design
工作需要，就开始看chromium 设计文档，做点笔记   
https://www.chromium.org/developers/design-documents    

## [Chromium for Mac](https://github.com/chromium/chromium/blob/main/docs/mac_build_instructions.md)
1. 获取代码
   通过chromium提供的depot_tools获取代码    
   ```shell
   git config --global core.precomposeUnicode true
   git clone https://chromium.googlesource.com/chromium/tools/depot_tools   # 国外源
   git clone https://source.codeaurora.org/quic/lc/chromium/tools/depot_tools    # 国内源
   # 在bash_profile插入下面代码 
   export PATH="/path to depot_tools/depot_tools:$PATH"
   function proxy_off(){
        unset http_proxy
        unset https_proxy
        unset ftp_proxy
        unset rsync_proxy
        echo -e "已关闭代理"
   }
    function proxy_on() {
        export no_proxy="localhost,127.0.0.1,localaddress,.localdomain.com"
        export http_proxy="http://127.0.0.1:1087"
        export https_proxy=$http_proxy
        export ftp_proxy=$http_proxy
        export rsync_proxy=$http_proxy
        export HTTP_PROXY=$http_proxy
        export HTTPS_PROXY=$http_proxy
        export FTP_PROXY=$http_proxy
        export RSYNC_PROXY=$http_proxy
        echo -e "已开启代理"
    }
    # 保存
    source ~/.bash_profile
   # 注意，根据自己的配置设置有可能会是1080或1086
   # 需要使用代理时开启ss全局模式，然后打开终端，输入proxy_on就会启动。如果需要关闭，只需要输入proxy_off。
    proxy_on
    mkdir chromium && cd chromium   
    # 大约需要半小时到一小时
    fetch chromium 
   ```
