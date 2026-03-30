安装net工具  sudo apt install net-tools
检测监听端口  sudo  netstat -tlnp t：tcp协议 l:监听  n:数量  p:进程 
切换到的目录打开虚拟环境 不然会报错 开启虚拟环境 我之前安装过 source venv/bin/activate
安装一个三方库 pip install python-snap7
编辑服务端脚本 nano s7_test.py
执行脚本 python s7_test.py
重开一个终端 打开wireshark  sudo wireshark
再开一个终端 编辑客服端脚本  nano s7_client.py
运行 python s7_client.py
wireshark网卡选择any  过滤条件是tcp.port == 102
截图协议分析
