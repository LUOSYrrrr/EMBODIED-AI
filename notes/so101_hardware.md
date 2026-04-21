# SO-101 硬件配置

## USB 串口
- Leader (主臂):   /dev/ttyACM0
- Follower (从臂): /dev/ttyACM1

## 相机
- top (俯视):   index 2  (/dev/video2, YUYV 640x480)
- wrist (腕部): index 0  (/dev/video0, YUYV 640x480)

## Robot ID (LeRobot 标定用)
- follower: R12252801  (已在 Mac 标定, 2026-04-10)
- leader:   R12252802  (已在 Mac 标定, 2026-04-10)

标定文件位置:
- Mac:   ~/.cache/huggingface/lerobot/calibration/{robots/so101_follower,teleoperators/so101_leader}/R1225280{1,2}.json
- Linux: ~/.cache/huggingface/lerobot/calibration/{robots/so101_follower,teleoperators/so101_leader}/R1225280{1,2}.json
