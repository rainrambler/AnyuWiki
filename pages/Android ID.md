- 从 [[Android 10]] 开始，应用必须具有 READ_PRIVILEGED_PHONE_STATE 特许权限才能访问设备的不可重置标识符（包括 [[IMEI]] 和序列号）。
- Build.getSerial()
- TelephonyManager
  .getImei()
  .getDeviceId()
  .getMeid()
  getSimSerialNumber()
  .getSubscriberId()
- https://source.android.google.cn/security/enhancements/enhancements10
- 注意：从 [[Google Play]] 商店安装的第三方应用无法声明特许权限。