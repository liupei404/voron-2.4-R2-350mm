## 热端值

# 设置热端特定值
AFC 的一些值非常依赖于您的热端

热端类型的建议起始值（更多内容将在后面添加）如下。 和 在 中，并且 在 中。对于 ，如果已定义，请使用第二个值;否则，请使用 第一个值。
如果您使用 ram 缓冲区作为工具头传感器，则可能需要增加此值。
tool_stntool_stn_unloadAFC/AFC_Hardware.cfgvariable_retract_lengthvariable_pushback_lengthAFC/AFC_Macro_Vars.cfgtool_stnpin_tool_end

以下是 FilamATrix/Clockwork 2 上的 Voron2.4/ 0.2 新款V6 热端的示例图：


## 热端特定值

新款V6 
tool_stn： 59 （如果未定义） / 36 （如果已定义）pin_tool_endpin_tool_end
tool_stn_unload: 106
variable_retract_length: 26.1
variable_pushback_length: 20
