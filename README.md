### 主題
將自己設計的簡易機器人放到迷宮裡面，結合之前上課教過的內容，紀錄地圖。

在最後面備註的地方，有紀錄一些自己遇到的問題以及解決方法

### 步驟
## 1*
下載好檔案至home\user\catkin_ws\src，先執行第一個指令

`roslaunch myrobot_1100411_description gazebo.launch`

確認gazebo正常開啟，可看到機器人和簡易迷宮的圖

## 2
執行

`rviz`

打開rviz之後，到左下角的Add新增RobotModel，點選OK

左側Global Options的Fixed Frame更改為base_link

## 3*
執行

`roslaunch myrobot_1100411_description mapping.launch`

## 4
回到rviz的頁面，左側Global Options的Fixed Frame更改為map

到左下角的Add新增Map，點選OK

Map的Topic改成/map

## 5
到左下角的Add新增LaserScan，點選OK

LaserScan的Topic改成/scan，Size改成0.05

## 6
執行

`rosrun teleop_twist_keyboard teleop_twist_keyboard.py`

就可以開始掃描

## 7*
執行

`rosrun map_server map_saver -f myrobot_map`

最後使用以下指令就可以看到紀錄的地圖了

`eog myrobot_map.pgm`

## 備註

## 1
如果在執行步驟一的時候遇到錯誤

`xacro: substitution args not supported: No module named 'rospkg'`

可能是因為電腦有安裝Anaconda，導致路徑錯誤，才會找不到

在刪除Anaconda之後，重開就可以正常執行了

## 2
如果在執行步驟三的時候遇到錯誤

`RROR: cannot launch node of type [gmapping/slam_gmapping]: can't locate node [slam_gmapping] in package [gmapping]`

這個問題很常出現，不知道具體的錯誤原因，但遇到的時候重開幾次就又正常了

## 3
最後無法開啟圖片的話，可能是因為還沒有安裝

依序執行這兩個指令，就可以正常開啟了

`sudo apt update`

`sudo apt install eog`
