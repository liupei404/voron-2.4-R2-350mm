# 校准安装高度
## 确保 Eddy 的安装位置高于喷嘴 2 至 3 毫米

# 固件编译
- [*] Enable extra low-level configuration options 
- Micro-controller Architecture (Raspberry Pi RP2040/RP235x) ---> 
- Processor model (rp2040) ---> 
- Bootloader offset (No bootloader) ---> 
- Flash chip (GENERIC_03H with CLKDIV 4) ---> 
- Communication Interface (USBSERIAL) --->
## 如果不使用 KATAPULT
- Bootloader offset (No bootloader) ---> 
- Flash chip (GENERIC_03H with CLKDIV 4) --->
## 如果使用 KATAPULT（使用此方式需要先进行 5.4 的操作）
- Bootloader offset (16KiB bootloader) --->
## 如果使用 USB 通信 
- Communication Interface (USBSERIAL) --->
## 如果使用 CAN BUS 通信
- Communication interface (CAN bus) ---> 
- (4) CAN RX gpio number 
- (5) CAN TX gpio number 
- (1000000) CAN bus speed

# 校准
##  驱动电流校准
- 将 Eddy 置于热床上方约 20mm 处，LDC_CALIBRATE_DRIVE_CURRENT 
CHIP=btt_eddy
- 将 Eddy 读数映射到喷嘴高度，PROBE_EDDY_CURRENT_CALIBRATE_AUTO CHIP=btt_eddy
### 如果使用手动校准步骤
- G28 X Y 归零
- 清除高度图 BED_MESH_CLEAR
- G0 X175 Y175 F6000 将喷嘴移动到平台中心(350mm平台)
- 开始手动 Z 轴偏移校准 PROBE_EDDY_CURRENT_CALIBRATE CHIP=btt_eddy
## 床面网格校准
- Home 所有轴
- 调平 Z_TILT_ADJUST 或者 QUAD_GANTRY_LEVEL
- 快速的网格扫描 BED_MESH_CALIBRATE METHOD=scan 
SCAN_MODE=rapid

## 温度补偿校准
- Home 所有轴
- G0 Z5 将 Z 轴调整至床面上方 5 毫米
- 执行 SET_IDLE_TIMEOUT TIMEOUT=36000 将机器的 idle timeout 设置长
一点，避免我们升温过程的时候 timeout
- TEMPERATURE_PROBE_CALIBRATE PROBE=btt_eddy TARGET=56 STEP=4(如果要打印高温材料，把温度设置到66以上，不然打印中途会报错无法连接到eddy)
- Eddy 的温度不再上升
- TEMPERATURE_PROBE_NEXT - 可用于在达到步进增量前强制采样新数据
- TEMPERATURE_PROBE_COMPLETE - 可用于在达到目标前完成校准
- ABORT - 可用于终止校准并忽略结果

# 注意：
## 在调试是往往高度混肴导致调试完了报错,和温度补偿温度设置不够，在打印中途停机