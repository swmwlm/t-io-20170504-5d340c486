<h2>
  t-io: 让天下没有难开发的即时通讯
</h2>


<ol>
	<li><h3>简 介</h3>
		 <strong>t-io</strong>是基于jdk aio实现的易学易用、稳定耐操、性能超强、内置功能丰富、核心代码只有4000多行的即时通讯框架。字母<strong> t </strong>取<strong>talent</strong>（天才）的首字母，也可以理解为<strong>"特快"</strong>，同时也是<strong>作者姓氏</strong>的首字母。这里有<a href="https://my.oschina.net/talenttan/blog/863545" target="_blank">资料及问题汇总</a>。
	</li>
		 
	<li><h3>常见应用场景</h3>
		IM、实时监控、推送服务（已内置）、RPC、游戏、物联网等实时通讯类型的场景
	</li>
	
	<li><h3>特 点</h3>
		<ul class="masthead-links" style="">
		  <li>
			<strong>极简洁清晰易懂的API</strong>: 没有生涩难懂的新概念，只需<strong>花上30分钟</strong><a href="http://www.t-io.org:9292/quickstart.html" target="_blank">学习helloworld</a>就能很好地掌握并实现一个性能极好的即时通讯应用
		  </li>
		  <li>
			<strong>极震撼的性能</strong>
			<ul>
				<li>
					轻松支持<strong>百万级</strong>tcp长连接，彻底甩开业界<strong>C1000K</strong>烦恼（centos 单CPU4核 16G 测试数据: 17.82万长连接，只消耗800M内存，CPU毫无压力）
				</li>
				<li>
					最高时，每秒可以收发<strong>333.33万</strong>条消息(约<strong>93.33M</strong>)(windows7、i7、8g、群聊场景)
				</li>
			</ul>
		  </li>
		  
		  <li>
			<strong>极亲民的内置功能</strong>
			<ul>
				<li>
					框架层面帮你<strong>检测心跳</strong>(tcp server)、<strong>发送心跳</strong>(tcp client)
				</li>
				<li>
					框架层面支持<strong>自动重连</strong>(可设置重连间隔时间和重连次数)
				</li>
				<li>
					框架层面支持<strong>同步消息</strong>(消息发送后，等到响应消息再往下执行)
				</li>
				<li>
					框架层面支持<strong>绑定userid</strong>(用于用户关联)、<strong>绑定groupid</strong>(用于群聊)
				</li>
				<li>
					内置各项统计功能----接受过多少连接、关闭过多少连接、已发送的消息数、已接收的消息数、当前是多少正常连接、当前多少断开的连接等。
				</li>
			</ul>
		  </li>
		</ul>
	</li>
	
	
	<li><h3>性能数据</h3>
		<ol>
			<li>
				<h4>IM实例收发速度<strong>333万条/秒</strong></h4>
			</li>
			<li>
				<h4>IM实例<strong>17.82万TCP长连接且正常收发消息只消耗800M内存，CPU使用率极低</strong>，目测t-io可以支撑<strong>200万长连接</strong></h4>
			</li>
			<li>
				<h4>17万长连接反复破坏性测试（譬如断网又连网、反复断开客户端又连上客户端等），服务器内存保持稳定（600多M到900M间）</h4>
			</li>
		</ol>
	</li>


	
	
	<li><h3>t-io学习步骤（供参考，具体步骤根据各人而异）</h3>
		<ol>
			<li><h4>初步认识t-io</h4>
				<ol>
					<li>安装1.7以上版本的jdk及maven（已安装的略过此步骤）</li>
					<li>从<a href="https://git.oschina.net/tywo45/t-io" target="_blank">https://git.oschina.net/tywo45/t-io</a>处下载源代码</li>
					<li>双击install.bat安装t-io到本地maven仓库</li>
					<li>双击 "启动IM服务器.bat" 启动im server</li>
					<li>双击 "启动IM客户端.bat" 启动im client</li>
					<li>对着界面把玩几下，测试一把性能数据，对t-io形成感性认识</li>
				</ol>
			</li>
			
			<li><h4>了解代码目录结构（所有工程都是maven工程）</h4>
<h3>
<pre>
├─dist<span style='color:#06AD3D'>----------------成品</span>
│  └─examples<span style='color:#06AD3D'>----------------用t-io写的例子成品</span>
│      ├─helloworld
│      │  ├─client<span style='color:#06AD3D'>----------------helloworld的客户端</span>
│      │  └─server<span style='color:#06AD3D'>----------------helloworld的服务端</span>
│      ├─im
│      │  ├─client<span style='color:#06AD3D'>----------------im的客户端</span>
│      │  └─server<span style='color:#06AD3D'>----------------im的服务端</span>
│      └─showcase
│          ├─client<span style='color:#06AD3D'>----------------showcase的客户端</span>
│          └─server<span style='color:#06AD3D'>----------------showcase的服务端</span>
└─src
	├─core<span style='color:#06AD3D'>----------------t-io的核心代码</span>
	├─example<span style='color:#06AD3D'>----------------用t-io写的例子的源代码</span>
	│  ├─helloworld<span style='color:#06AD3D'>----------------helloworld的源代码</span>
	│  │  ├─client
	│  │  ├─common
	│  │  └─server
	│  ├─im<span style='color:#06AD3D'>----------------im的源代码</span>
	│  │  ├─client
	│  │  ├─common
	│  │  └─server
	│  ├─parent<span style='color:#06AD3D'>----------------例子的maven parent</span>
	│  └─showcase<span style='color:#06AD3D'>----------------showcase的源代码</span>
	│      ├─client
	│      ├─common
	│      └─server
	└─parent<span style='color:#06AD3D'>----------------maven工程的parent</span>
</pre>
</h3>
			</li>
			
			<li><h4>花30分钟学习hello world</h4>
				传送门: <a href="http://www.t-io.org:9292/quickstart.html" target="_blank">30分钟快乐入门</a>
			</li>
			
			<li><h4>花点时间学习showcase</h4>
				代码正在开发中，文档暂未开始... ...尽量在2017年4月30号前提供，在此之前有问题可以和作者沟通。有什么需求可以在这里反馈给我：
				<a href="https://my.oschina.net/talenttan/tweet/12616527" target="_blank">showcase需求反馈</a>
			</li>
		</ol>
	</li>
	
	
	<li><h3>案 例（案例太多，此处仅列举t-io开源第一个月内的案例）</h3>
		<ul class="masthead-links" style="font-size:14pt;">
		  <li>
			某网管系统(管理数百台刀片服务器的系统)
		  </li>
		  <li>
			某直播平台(视频直播+聊天)
		  </li>
		  <li>
			某智能设备检测系统(数据采集)<!--小白-->
		  </li>
		  <li>
			某物联网系统(服务端)<!--好像是jackkang-->
		  </li>
		  <li>
			深圳市某在线技术发展有限公司(中银联投资)：某网络安全运营支撑平台<!--小宇-->
		  </li>
		  <li>
			<a href="https://git.oschina.net/websterlu/redisx" target="_blank">redisx</a><!--小宇-->
		  </li>
		  <li>
			<a href="https://git.oschina.net/kangjie1209/talent_dubbo" target="_blank">talent_dubbo</a><!--jackkang-->
		  </li>
		  <li>
			某移动省公司CRM业务受理消息采集平台(数据采集)<!--福州-精灵-java-->
		  </li>
		</ul>
	</li>
	
		
	
	

	<li><h3>参与t-io</h3>
		<ol>
			<li>t-io是将多线程技巧运用到极致的框架，所以一旦您参与到本项目，将会从本项目中学到很多关于多线程的技巧。</li>
			<li>
			<a 
			  href="/tywo45/t-io/issues/new?issue%5Bassignee_id%5D=&amp;issue%5Bmilestone_id%5D="
			  class="ui mini green button"
			  title="提交issue">
			<i class="icon plus"></i>提交Issue
			</a>
			给项目提出有意义的新需求，或是帮项目发现BUG，或是上传你本地测试的一些数据让作者参考以便进一步优化。
			</li>

			<li>
			点击右上方的
			<span class="basic buttons mini star-container ui">
			<a href="javascritp:void(0);" class="ui button star" data-method="post" data-remote="true" rel="nofollow">Star</a>
			</span>
			以便随时掌握本项目的动态
			</li>
			
			
			

			
		</ol>
	</li>
	
	
	
</ol>


<h2>t-io承诺</h2>
<ol>
	<li><h3>永远基于LGPL协议开源</h3></li>
	<li><h3>代码将毫无保留地开放给世界</h3></li>
	<li><h3>以成为世界一流开源软件为目标，做国产优秀良心作品</h3></li>
	<li><h3>倾听用户需求，快速响应用户反馈</h3></li>
</ol>




