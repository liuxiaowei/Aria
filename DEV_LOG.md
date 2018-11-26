## 开发日志
  + v_3.5.2
    - 添加Serializable接口支持 https://github.com/AriaLyy/Aria/issues/320
    - 失败回调增加错误原因 https://github.com/AriaLyy/Aria/issues/310
      ```
      @Download.onTaskFail void taskFail(DownloadTask task, Exception e) {
         e.getMessage();
        ...
      }
      ```
     - fix bug https://github.com/AriaLyy/Aria/issues/322
     - 新增201 重定向支持 https://github.com/AriaLyy/Aria/issues/318
     - 修复使用`useServerFileName(true)`中含有`"`导致的文件后缀名错误问题
     - 优化logcat日志提示
     - 修改下载线程的优先级为`Process.setThreadPriority(Process.THREAD_PRIORITY_BACKGROUND);`
     - fix bug https://github.com/AriaLyy/Aria/issues/319
     - 修复分卡下载失败的问题 https://github.com/AriaLyy/Aria/issues/326
     - 初始化Aria时会将所有数据库状态为下载中的任务改为已停止，防止应用被kill后，任务状态错误
     - 初始化时自动判断文件是否被删除，文件被删除的任务将自动重置默认值
  + v_3.5.1
    - 优化`taskExists`方法
    - 添加`post`参数请求支持
      ```java
      Aria.download(SingleTaskActivity.this)
              .load(DOWNLOAD_URL)
              .setFilePath(path)
              .asPost() // post请求
              .setParam("key", "value") //传递参数
              //.setParams(Map<String, String>) // 传递多参数
              .start();
      ```
     - 增加强制设置文件路径的api, https://github.com/AriaLyy/Aria/issues/311
       ```
       Aria.download(SingleTaskActivity.this)
                     .load(DOWNLOAD_URL)
                     .setFilePath(path, true) // true表示忽略路径是否被占用
                     .start();
       ```
  + v_3.5
    - fix bug https://github.com/AriaLyy/Aria/issues/302
    - fix bug https://github.com/AriaLyy/Aria/issues/283
    - fix bug https://github.com/AriaLyy/Aria/issues/305
    - fix bug https://github.com/AriaLyy/Aria/issues/306
    - fix bug https://github.com/AriaLyy/Aria/issues/272  (现在，停止所有任务，未开始的任务状态将变为停止)
    - fix bug https://github.com/AriaLyy/Aria/issues/277
    - fix bug https://github.com/AriaLyy/Aria/issues/303
    - 优化停止任务的速度
    - 修复组合任务修改子任务文件名失败的问题
  + v_3.4.12
    - fix bug https://github.com/AriaLyy/Aria/issues/286
    - 优化线程池任务
  + v_3.4.11
    - fix bug https://github.com/AriaLyy/Aria/issues/288
    - fix bug https://github.com/AriaLyy/Aria/issues/282
  + v_3.4.10
    - fix bug https://github.com/AriaLyy/Aria/issues/280
  + v_3.4.9
    - fix bug https://github.com/AriaLyy/Aria/issues/276
  + v_3.4.8
    - 组合任务新增`updateUrls(List<String>)`用于修改组合子任务的url，[see](https://aria.laoyuyu.me/aria_doc/api/update_url.html)
    - 出于安全考虑，FTP数据库去掉密码的保存
    - 增加FTPS支持 [see](https://aria.laoyuyu.me/aria_doc/download/ftps.html)
    - 增加速度限制支持[see](https://aria.laoyuyu.me/aria_doc/api/speed_handle.html)
    - 增加内存空间不足验证
  + v_3.4.7
    - 修复分块任务异常操作导致的问题
  + v_3.4.6
    - 修复android 4.4.4 版本多dex下无法进行回调的问题
    - 新增`updateUrl(newUrl)`用于修改任务的url，[see](https://aria.laoyuyu.me/aria_doc/api/task_handle.html#%E6%9B%B4%E6%96%B0%E4%BB%BB%E5%8A%A1url)
    - 优化分块下载
    - 修复了字符串中有特殊字符导致的路径冲突问题；修复ftp分块下载失败问题
    - 修复连接中有`+`导致的地址呗使用问题。
    - 修复表重复创建导致的崩溃问题 https://github.com/AriaLyy/Aria/issues/264
  + v_3.4.4
    - 实现[多线程分块下载](https://aria.laoyuyu.me/aria_doc/start/config.html)
    - 修复`stopAll()`和`resumeAll()`导致的进度为0问题
    - 修复任务组添加header无效的问题
  + v_3.4.3
    - 修复在activity 的onStop中取消注册导致的内存泄露问题
    - fix bug https://github.com/AriaLyy/Aria/issues/258
    - fix bug https://github.com/AriaLyy/Aria/issues/259
  + v_3.4.2
    - fix bug https://github.com/AriaLyy/Aria/issues/248
    - fix bug https://github.com/AriaLyy/Aria/issues/247
    - fix bug https://github.com/AriaLyy/Aria/issues/250
    - 添加任务判断是否存在的api
    - 添加代理api
    - 修复删除所有没有进出等待的问题
    - 进度有时出错的问题
    - FTP添加超时处理
  + v_3.4.1
    - 移除记录配置文件，改用数据库记录任务记录
    - 上传配置添加io超时时间、缓存大小配置
    - 添加没有网络也会重试的开关
    - 修复多次删除记录的bug
    - 文件长度现在可动态增加，详情见 https://aria.laoyuyu.me/aria_doc/start/config.html
    - 修复多module同时引用Aria导致打正式包出错的问题 https://github.com/AriaLyy/Aria/issues/240
  + v_3.4
    - 优化大量代码
    - 重构Aria的ORM模型，提高了数据读取的可靠性和读写速度
    - 现在可在任意类中使用Aria了，[使用方法](http://aria.laoyuyu.me/aria_doc/start/any_java.html)
    - 添加`window.location.replace("http://xxxx")`类型的网页重定向支持
    - 支持gzip、deflate 压缩类型的输入流
    - 添加`useServerFileName`，可使用服务端响应header的`Content-Disposition`携带的文件名
  + v_3.3.16
    - 修复一个activity启动多次，无法进行回掉的bug https://github.com/AriaLyy/Aria/issues/200
    - 优化target代码结构，移除路径被占用的提示
    - 添加支持chunked模式的下载
    - 去掉上一个版本"//"的限制
  + v_3.3.14
    - 修复ftp上传和下载的兼容性问题
    - 如果url中的path有"//"将替换为"/"
    - 修复http上传成功后，如果服务器没有设置返回码导致上传失败的问题
    - 上传实体UploadEntity增加responseStr字段，http上传完成后，在被`@Upload.onComplete`注解的方法中，可通过`task.getEntity().getResponseStr())`获取服务器返回的数据
    - 如果服务器存在已上传了一部分的文件，用户执行删除该FTP上传任务，再次重新上传，会出现550，权限错误；本版本已修复该问题
  + v_3.3.13
    - 添加`@Download.onWait、@Upload.onWait、@DownloadGroup.onWait`三个新注解，队列已经满了，继续创建新任务，任务处于等待中，将会执行被这三个注解标志的方法
    - app被kill，但是还存在等待中的任务A；第二次重新启动，先创建一个新的任务B，Aria会自动把B放进等待队列中，这时再次创建任务A，会导致重复下载，进度错乱的问题；本版本已修复这个问题
  + v_3.3.11
    - 添加进度更新间隔api，在`aria_config.xml`配置`<updateInterval value="1000"/>`或在代码中调用
      `AriaManager.getInstance(AriaManager.APP).getDownloadConfig().setUpdateInterval(3000)`便可以改变进度刷新间隔
    - 修复下载过程中kill进程可能出现的文件错误的问题 https://github.com/AriaLyy/Aria/issues/192
    - 修复http上传的空指针问题 https://github.com/AriaLyy/Aria/issues/193
    - 修复下载地址中含有`'`导致的崩溃问题 https://github.com/AriaLyy/Aria/issues/194
  + v_3.3.10
    - 修复地址切换导致下载失败的问题 https://github.com/AriaLyy/Aria/issues/181
    - 添加重置状态的api，当下载信息不改变，只是替换了服务器的对应的文件，可用`Aria.download(this).load(url).resetState()`重置下载状态 https://github.com/AriaLyy/Aria/issues/182
  + v_3.3.9
    - 添加POST支持
    - 任务执行的过程中，如果调用removeRecord()方法，将会取消任务 https://github.com/AriaLyy/Aria/issues/174
    - 修复一个数据库初始化的问题 https://github.com/AriaLyy/Aria/issues/173
    - 修复head头部信息过长时出现的崩溃问题 https://github.com/AriaLyy/Aria/issues/177
  + v_3.3.7
    - 修复一个线程重启的问题 https://github.com/AriaLyy/Aria/issues/160
    - 修复配置文件异常问题、格式化速度为0问题 https://github.com/AriaLyy/Aria/issues/161
  + v_3.3.6
    - 增加日志输出级别控制
    - 修复公网FTP地址不能下载的问题  https://github.com/AriaLyy/Aria/issues/146
    - 修复http下载地址有空格的时候下载失败的问题 https://github.com/AriaLyy/Aria/issues/131
    - 修复Activity在`onDestroy()`中调用`Aria.download(this).unRegister();`导致回调失效的问题
    - 修复Adapter下载FTP任务问题、任务调度问题 https://github.com/AriaLyy/Aria/issues/157
    - 优化代码，优化了IO性能
  + v_3.3.5 修复任务组、上传任务无法启动的bug
  + v_3.3.4 优化任务代码结构，修复上一个版本暂停后无法自动执行任务的问题
  + v_3.3.3 修复进度条错乱的问题，修复同一时间多次调用start导致重复下载的问题
  + v_3.3.2 新加reTry()，修复上一个版本不会回调失败事件的问题；增加running状态下5秒钟保存一次数据库的功能；修复FTP断点上传文件不完整的问题
  + v_3.3.1 增加网络事件，网络未连接，将不会重试下载，修复删除未开始任务，状态回调错误
  + v_3.3.0 增加任务组子任务暂停和开始控制功能、修复5.0系统以上数据库多生成两个字段的bug、去掉addSchedulerListener事件
  + v_3.2.26 修复任务组有时注解不起作用的问题
  + v_3.2.25 修复删除任务组文件，记录无法删除的问题
  + v_3.2.17 修复一个版本兼容性问题，线程中使用Aria出错问题
  + v_3.2.15 修复大型文件分段下载失败的问题，修复中文URL乱码问题
  + v_3.2.14 修复恢复所有任务的api接口，不能恢复下载组任务的问题
  + v_3.2.13 修复某些服务器头文件返回描述文件格式错误的问题、修复有时删除任务，需要两次删除的问题
  + v_3.2.12 实现FTP多线程断点续传下载，FTP断点续传上传功能
  + v_3.2.9 修复任务组下载完成两次回掉的问题，修复又是获取不到下载状态的问题
  + v_3.2.8 修复下载超过2G大小的文件失败的问题
  + v_3.2.7 移除设置文件名的api接口，修复断开网络时出现的进度条错误的问题
  + v_3.2.6 移除广播事件，增加任务组下载功能
  + v_3.1.9 修复stopAll队列没有任务时崩溃的问题，增加针对单个任务监听的功能
  + v_3.1.7 修复某些文件下载不了的bug，增加apt注解方法，事件获取更加简单了
  + v_3.1.6 取消任务时onTaskCancel回调两次的bug
  + v_3.1.5 优化代码结构，增加优先下载任务功能。
  + v_3.1.4 修复快速切换，暂停、恢复功能时，概率性出现的重新下载问题，添加onPre()回调，onPre()用于请求地址之前执行界面UI更新操作。
  + v_3.1.0 添加Aria配置文件，优化代码
  + v_3.0.3 修复暂停后删除任务，闪退问题，添加删除记录的api
  + v_3.0.2 支持30x重定向链接下载
  + v_3.0.0 添加上传任务支持，修复一些已发现的bug
  + v_2.4.4 修复不支持断点的下载链接拿不到文件大小的问题
  + v_2.4.3 修复404链接卡顿的问题
  + v_2.4.2 修复失败重试无效的bug
  + v_2.4.1 修复下载慢的问题，修复application、service 不能使用的问题
  + v_2.4.0 支持https链接下载
  + v_2.3.8 修复数据错乱的bug、添加fragment支持
  + v_2.3.6 添加dialog、popupWindow支持
  + v_2.3.3 添加断点支持、修改下载逻辑，让使用更加简单、修复一个内存泄露的bug
  + v_2.3.1 重命名为Aria，下载流程简化
  + v_2.1.1 增加，选择最大下载任务数接口