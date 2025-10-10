# voron-2.4-R2-350mm Klipper AMS 之 BoxTurtle龟盒多色系统构建
卧龙2.4 R2版本350mm装机，带工具头切刀，BoxTurtle，TN1.0

#  打印机主要组件
## 电器配置
- A/B Z电机：17HS19-2004S1-22B 48mm  
- MCU：带BIGTREETECH TMC2209的BIGTREETECH Manta M8P  
- 电源：350W 24V   
- 核心板: BIGTREETECH CB1  
- 显示器：Mellow高清Fly3D隐藏式接线7寸HDMI触摸屏幕  
- 相机：广告机免驱广角120度+500万像素摄像头模组,62mm*9mm*6.8mm。罗技 C920 HD Pro（暂时没有使用）  
- 自动调平传感器IDM涡流电感TAP：BIGTREETECH Eddy  

## USB 工具头
- 挤出机电机：36BYG1204-A-6QHT  
- 工具头：BIGTREETECH EBB SB 2209 USB (自带共振补偿LIS2DW不需要单独购买),装机小心扩展板螺丝不要短路插排,尽量不要带电拔插,主板和电机需要供地。  
- 热端：新款VORON2.4/0.2散热器V6陶瓷热端挤出头高速打印套件24V60W配件  
- 热端风扇：4010 24V磁悬浮静音  
- 模型冷却风扇：5015 24V离心涡轮  
- 挤出机：Clockwork2(双传感器) 为后期多色提供切刀使用(FilamATrix 工具头切刀改件(VORON))改件,不建议使用远程切刀  
- 传感器：D2F-L、D2F-5L(二选一，去掉加长杆，5.55mm钢珠)  
- SB灯光：Mellow Voron-Stealthburner LED灯珠(GRB 10灯珠)  专用打印文件https://cdn.mellow.klipper.cn/STEP/Stealthburner_LED.step  

## 其他配件
- 打完关机模块断电短路检测： BIGTREETECH Relay （暂时没有使用）  
- XY限位开关：FLY3D打印机配件Voron霍尔效应传感器  
- Z限位开关：Mellow Hartk Sexbolt Z轴限位开关注塑套件适用于Voron2.4三叉戟(也可以使用eddy作为限位器,为了安全我还是喜欢使用物理限位器，如果使用eddy作为限位器应  控制好Z高度不要撞机了。)  
- Z轴光轴：圆轴D切5mm 负公差(精密性)  
- Z轴同步轮皮带:GATES环形带188*4  
- 其他皮带：GATES 2GT高精度低粉尘闭口皮带同步  
- 电源滤波: CW4L2-20A-RG（小壳）[20A端子台导轨式]  
- 电器导轨：C45电气导轨镀彩锌加厚  
- 电器仓风扇: 6020 24V 静音  
- 仓室照明：Mellow 370mm RGB灯条 25灯珠  
- 卡式品字插座：AC-01卡式品字插座 带灯开关保险丝  

## 机械&框架
- 框架：通用voron2.4R2 350mm铝型材 （嘉立创FA）  
- X 直线导轨：HIWIN MG 系列微型直线导轨 - MGN12H  
- Y 型直线导轨:HIWIN MG 系列微型直线导轨 - MGN9H  
- Z 轴直线导轨:HIWIN MG 系列微型直线导轨 - MGN9H  
- 单面3M泡沫胶10mm、厚度1mm&3mm  
- 双面3M VHB  

## 床
- 固态继电器：G3NA-210-D/DC5-24V/10A  
- 加热垫：Keenovo 硅胶交流加热器350x350x220x1000W进口定做VORON2.4 350mm  
- 构建台：Mellow高精度CNC加工超平Voron2.4精铸铝热床板,355x355x8mm  
- PEI：弹簧钢双面PEI喷涂355*355mm+磁贴片  


# BoxTurtle 龟盒多色
- 多色推荐使用龟盒,兔子多色调试繁琐 
- https://github.com/ArmoredTurtle/BoxTurtle
- 龟箱不打印裙子right_rear_skirt.stl,使用下面选配件BTIO扩展裙子。
- 
- AFC选配件：AFC_Bypass直通和AT_Brush毛刷(暂时没用),BTIO扩展板需要。
- https://github.com/ArmoredTurtle/AFC-Accessories 

## 多色电气
- 远程挤出机:10齿的36圆饼电机 (四通道单独使用)  
- LED: 带灯板WS2812-RGB  
- 主板风扇：3010 轴流风扇 5v(使用开创围挡,没用使用风扇)  
- 回料电机：N20减速电机 6v/500RPM  
- 传感器：D2HW-C201H(推荐使用)  
- 线材：24AWG线材（0.2平方） 
- 主板：带TMC2209的 AFC-Lite 主板  

## 缓冲器
- TN1.0 & TN2.0(不使用TN2.0)  
- 推荐使用TN1.0   
- 传感器：D2F-L 2个(TN1.0使用,TN2.0使用霍尔)  

## 封箱
- 使用三方封箱

- 透明亚克力圆盘:3mm厚度x220mm x2  
- PETG板:1.5mm厚度x533mmx384mm x1

#  Orcaslicer切片软件配置
- 起始代码
- M104 S0 ; 阻止 OrcaSlicer 单独发送温度等待
  M140 S0 ; 阻止 OrcaSlicer 单独发送温度等待
  PRINT_START EXTRUDER=[first_layer_temperature] BED=[first_layer_bed_temperature] CHAMBER=[chamber_temperature] TOOL={initial_tool}

- 耗材丝更换(乌龟多色)
  T[next_extruder] PURGE_LENGTH=[flush_length]
  ;{ if toolchange_count == 1 }
  ;SET_AFC_TOOLCHANGES TOOLCHANGES=[total_toolchanges]{endif }
  ;FLUSH_START
  ;EXTERNAL_PURGE {flush_length}
  ;FLUSH_END

- 耗材材料-单挤出机多材料打印机的换色参数全部设置0.

#  其他
## 挤出机设置计算
- 新款VORON2.4/0.2散热器V6陶瓷热端挤出头高速打印套件24V60W配件 计算方式如下：
- https://github.com/liupei404/voron-2.4-R2-350mm/blob/main/image/V6_hotend1.png
- https://github.com/liupei404/voron-2.4-R2-350mm/blob/main/image/V6_hotend2.png
- https://github.com/liupei404/voron-2.4-R2-350mm/blob/main/image/example-cw2-voron2.4_0.2_new%20V6_hotend.png

## 封箱装配
- https://github.com/liupei404/voron-2.4-R2-350mm/tree/main/BoxTurtle 原版龟盒封箱顶盖Mod/Snipaste_2025-01-16_08-45-27.jpg
- 
