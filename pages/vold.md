- Vold(volume Daemon)，即Volume守护进程，用来管理[[Android]]中存储类的热拔插事件，处于Kernel和Framework之间，是两个层级连接的桥梁。
- Vold主要是接收[[Kernel]]的uevent消息，然后通过NM([[NetLinkManager]])和VM([[VolumeManager]])处理，将消息传递到Framework的SM([[StorageManager]])，最后SM会将数据存储下来，消息通知到在SM注册的服务和App。
- 在init.rc中有start vold的命令会被init解析到，而start对应的函数do_start(const BuiltinArguments& args)；即启动对应的service。