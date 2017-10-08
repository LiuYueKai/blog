在命令行中执行如下代码：

## 首先执行如下命令确保可用（此步骤只是验证，可以略过）：
/Applications/FarBox.app/Contents/MacOS/FarBox

## 执行如下命令之后就可以额用了
sudo mv /Applications/FarBox.app/Contents/MacOS/FarBox /Applications/FarBox.app/Contents/MacOS/_FarBox
echo '#!/bin/bash' >> /Applications/FarBox.app/Contents/MacOS/FarBox
echo '/Applications/FarBox.app/Contents/MacOS/_FarBox' >> /Applications/FarBox.app/Contents/MacOS/FarBox
sudo chmod +x /Applications/FarBox.app/Contents/MacOS/FarBox

