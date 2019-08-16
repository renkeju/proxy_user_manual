系统代理
------------

Windows 10
^^^^^^^^^^^^

* 手动代理

  1. 点击右下角通知按钮

    .. image:: _images/system/windows/手动代理/通知.png

  2. 在弹出的对话框内点击 :guilabel:`所有设置`

    .. image:: _images/system/windows/手动代理/所有设置.png

  3. 之后在 :guilabel:`设置` 中选择 :guilabel:`网络和 Internet` 选项

    .. image:: _images/system/windows/手动代理/网络和Internet.png

  4. 在弹出的选项卡中，选择 :guilabel:`代理` 与 :guilabel:`使用代理` 选项

    .. image:: _images/system/windows/手动代理/代理.png

  5. 在代理选项内选择开启代理开关，在手动输入地址：|proxy_address| 和端口：|proxy_port|。

    .. image:: _images/system/windows/手动代理/手动代理.png

* PAC 代理

  1. 进入 :guilabel:`控制面板`

    .. image:: _images/system/windows/PAC/控制面板.png

  2. 点击控制面板的 :guilabel:`网络和 Internet`

    .. image:: _images/system/windows/PAC/网络和Internet.png

  3. 进入 :guilabel:`Internet属性` 面板

    .. image:: _images/system/windows/PAC/Internet属性-常规.png

  4. 在 :guilabel:`Internet属性` 面板上方选择 :guilabel:`连接`

    .. image:: _images/system/windows/PAC/Internet属性-连接.png

  5. 点击 :guilabel:`局域网设置` 按钮

    .. image:: _images/system/windows/PAC/局域网设置.png

  6. 点击 :guilabel:`使用配置脚本`

    .. image:: _images/system/windows/PAC/使用自动配置脚本.png

  7. 点击所有面板的 :guilabel:`确定` 按钮退出。

MacOS
^^^^^^^^^^^^^^

1. 在 Mac 上，选取苹果菜单 :guilabel:`系统偏好设置`，然后点按 :guilabel:`网络`。

  .. image:: _images/system/macos/系统偏好设置.png

2. 在列表中选择网络服务（例如，以太网或 Wi-Fi）。

  .. image:: _images/system/macos/网络.png

3. 点按 :guilabel:`高级`，然后点按 :guilabel:`代理`。

  .. image:: _images/system/macos/代理.png

4. 如果您要自动配置代理服务器设置，请选择 :guilabel:`自动发现代理` 以自动发现代理服务器，如果您使用的是自动代理配置 (PAC) 文件，则请选择 :guilabel:`自动代理配置`。如果您选择 :guilabel:`自动代理配置`，则请在 URL 栏输入 PAC 文件的地址。如果需要更多信息，请联系网络管理员。

  .. image:: _images/system/macos/自动代理配置.png

5. 如果您要手动配置代理服务器设置，请执行以下操作：

  .. image:: _images/system/macos/网页代理.png
  .. image:: _images/system/macos/安全网页代理.png

  * 选择一种代理服务器，例如 FTP 代理，然后在右边的栏中键入它的地址和端口号。
  * 如果代理服务器受密码保护，请选择 :guilabel:`代理服务器要求密码` 复选框。在 :guilabel:`用户名称` 和 :guilabel:`密码` 栏中输入您的帐户名称和密码。

.. attention::

    您也可以选取忽略互联网（主机）上的特定电脑和互联网（域）的分段的代理设置，方法是在 :guilabel:`忽略这些主机与域的代理设置` 栏中添加主机或域的地址。如果您想确保直接从主机或域接收信息，而不是接收在代理服务器上缓存的信息，这将很有用。

    若要忽略单个域，请输入域名，比如 apple.com。

    若要忽略一个域中的所有网站，请在域名前使用星号，比如 \*apple.com。

    若要忽略一个域的特定部分，请指定每个部分，比如 store.apple.com。

Ubuntu
^^^^^^^^^^^^^^^

1. 单击位于右侧快速应用程序访问栏顶部的 :guilabel:`设置` 的“小扳手”图标。

  .. image:: _images/system/ubuntu/快速应用程序访问栏.png

2. 在左侧导航栏中，单击 :guilabel:`网络` 选项卡。

  .. image:: _images/system/ubuntu/网络.png

3. 单击网络代理标签附近的齿轮图标。

  .. image:: _images/system/ubuntu/齿轮图标.png

4. 将出现一个对话框，您可以在其中设置代理设置。

  .. image:: _images/system/ubuntu/对话框.png

5. 在相应的文本字段中，输入代理服务器的主机名或IP地址。确保更改端口号以匹配代理服务器。

  .. image:: _images/system/ubuntu/手动代理.png

  .. image:: _images/system/ubuntu/自动代理.png

6. 关闭对话框。您的设置将自动保存。


Linux
^^^^^^^^^^^^^^^

在终端中执行下面的命令：

.. code-block:: bash

  sudo cat << "EOF" > /etc/profile.d/proxy.sh
  http_proxy=http://{{ proxy_username }}:{{ proxy_password }}@{{ proxy_address }}:{{ proxy_port }}
  https_proxy=http://{{ proxy_username }}:{{ proxy_password }}@{{ proxy_address }}:{{ proxy_port }}
  ftp_proxy=http://{{ proxy_username }}:{{ proxy_password }}@{{ proxy_address }}:{{ proxy_port }}

  export http_proxy https_proxy ftp_proxy
  EOF

配置完成后重启主机或在终端中执行下面的命令：

.. code-block:: bash

  sudo source /etc/profile