# 中兴 F7607P 万兆光猫工具包

配套文章：[中兴 F7607P 开 Telnet、改码与固件升级](https://xiaozou123.cn/zte-f7607p-telnet-firmware/)

F7607P 是 XG-PON 的万兆网关，工具分两块：通用的开 T 与改码，以及把联通/移动版刷成电信版的更新工具。仓库只放工具，固件与 `kernel_CT.bin`、`framework_CT.bin` 在 Releases。

## 目录

- `telecom_flash_tool/`：中兴 7607P 电信版固件更新工具，SecureCRT 定制外壳，`Bin/` 里带 `hash.txt` 与 MyHash 校验器
- `common/`：ZTelnet、zte_factroymode、ztecfg、factorymode_crack、tftpd64

## 刷写前

- 用 `upgradetest getver` 看当前版本，跨版本刷写风险最大
- `Bin/hash.txt` 是配套校验值，改过名的固件对不上就会失败
- 刷写过程中断电，设备可能起不来

## 文件与 SHA256

| 文件 | 字节 |
|---|---|
| `common/ZTelnet v1.0.5.exe` | 9,729,169 |
| `common/factorymode_crack.exe` | 872,448 |
| `common/tftpd64.exe` | 343,040 |
| `common/zte_factroymode.exe` | 9,840,829 |
| `common/ztecfg.exe` | 7,037,223 |
| `common/说明.txt` | 436 |
| `telecom_flash_tool/App/ClientConfigUI65U.dll` | 888,320 |
| `telecom_flash_tool/App/CommonUI65U.dll` | 260,608 |
| `telecom_flash_tool/App/Config/ButtonBar.ini` | 135 |
| `telecom_flash_tool/App/Config/Color Schemes.ini` | 1,885 |
| `telecom_flash_tool/App/Config/Global.ini` | 9,910 |
| `telecom_flash_tool/App/Config/SCRTMenuToolbar.ini` | 5,588 |
| `telecom_flash_tool/App/Config/Sessions/Default.ini` | 8,806 |
| `telecom_flash_tool/App/ConnectDialog65U.dll` | 435,200 |
| `telecom_flash_tool/App/MFC90ENU.dll` | 54,272 |
| `telecom_flash_tool/App/Microsoft.VC80.CRT.manifest` | 1,869 |
| `telecom_flash_tool/App/Microsoft.VC90.CRT.manifest` | 1,860 |
| `telecom_flash_tool/App/Microsoft.VC90.MFC.manifest` | 2,357 |
| `telecom_flash_tool/App/Microsoft.VC90.MFCLOC.manifest` | 5,377 |
| `telecom_flash_tool/App/Ont.dll` | 3,391,488 |
| `telecom_flash_tool/App/Telnet.dll` | 206,336 |
| `telecom_flash_tool/App/mfc90u.dll` | 3,780,424 |
| `telecom_flash_tool/App/msvcp80.dll` | 548,864 |
| `telecom_flash_tool/App/msvcp90.dll` | 569,664 |
| `telecom_flash_tool/App/msvcr80.dll` | 626,688 |
| `telecom_flash_tool/App/msvcr90.dll` | 653,120 |
| `telecom_flash_tool/Bin/Hash计算器/MyHash.exe` | 623,104 |
| `telecom_flash_tool/Bin/Hash计算器/MyHash.ini` | 169 |
| `telecom_flash_tool/Bin/Hash计算器/MyHashExt.dll` | 305,664 |
| `telecom_flash_tool/Bin/Telecom_V2.0.0P1N11.png` | 30,839 |
| `telecom_flash_tool/Bin/hash.txt` | 180 |
| `telecom_flash_tool/中兴7607P电信版固件更新工具.exe` | 3,121,152 |

```
c6b0fc3056864024ab0b153cc1f8aabd2d60ef4d61a3abde19adf1d122b5743f  common/ZTelnet v1.0.5.exe
e5fa3ca8a74a768c58abe7a0e552bbd66276353804604cbaa6c2479b95b9d702  common/factorymode_crack.exe
2f5de838cf3079723f1697e5fac2f75fad4b98cd81b165f87cdfa99ded22d801  common/tftpd64.exe
7fae6d52429eca484d75f51d9d3a2fcb03b790a8cd40c6885685b7d8e34926b8  common/zte_factroymode.exe
a14be5d00516fc8ca950e97347e4f6e3f535f354254542f746739407aa9e3f46  common/ztecfg.exe
c9d0ab665ce2e10bfec90bb6d898aff47aacaa7b76b307ef45216522a6f4606e  common/说明.txt
eb9f413eec1c77ae168d320ad58591fa249af6fd0778a90193cd6e3c01a7c692  telecom_flash_tool/App/ClientConfigUI65U.dll
fe4d63d26005e0a24b90a3939b9606aecd5e17971bbcf7e7100e316f731ab8bb  telecom_flash_tool/App/CommonUI65U.dll
496cb3c8a6677a93d9821f0346fb2adb9152ef959f23d224607833ed63a304ba  telecom_flash_tool/App/Config/ButtonBar.ini
3f77b3c7fe57a9d645fe6f5fe92b134404318bb2466452bd6f22c24d82862696  telecom_flash_tool/App/Config/Color Schemes.ini
aa6a0df19b678af43196ed3b0007f3280eb91f1a26c5182b8bb9bc2c5e494f3f  telecom_flash_tool/App/Config/Global.ini
dc0ae456286dd151102652ef3166ede5d1c1e81bec6dbdd9b7b2f893d5567303  telecom_flash_tool/App/Config/SCRTMenuToolbar.ini
94ca771b694153fe44d05eec42cb202f70d967264cb60bc8f1219fb60664a0de  telecom_flash_tool/App/Config/Sessions/Default.ini
bf639208e62fc7bf683f11cebdeea7e123b60e2f8ef2f8f5e1d4846b988a4cc7  telecom_flash_tool/App/ConnectDialog65U.dll
a3e2c202e556791dee9d18962ca6780761b415313bcd104c2e621ba4089801a4  telecom_flash_tool/App/MFC90ENU.dll
17ad1a64ba1c382abf89341b40950f9b31f95015c6b0d3e25925bfebc1b53eb5  telecom_flash_tool/App/Microsoft.VC80.CRT.manifest
03d0776812368478ce60e8160ec3c6938782db1832f5cb53b7842e5840f9dbc5  telecom_flash_tool/App/Microsoft.VC90.CRT.manifest
1fed2074ab9f90d9fccc5a49b6aa42c917674c2b5c7b1bb93fb67b0e0c944818  telecom_flash_tool/App/Microsoft.VC90.MFC.manifest
81e13dc44e21fca2b095e82c34294c199d37428f32de36d5ffa6cd3b54f88d7b  telecom_flash_tool/App/Microsoft.VC90.MFCLOC.manifest
0b1482ceb46cf387f02dcc8f39678e324f3ac9cab8254361b87277057d3a1062  telecom_flash_tool/App/Ont.dll
8d3a082d5cfa57f01cbd143e7bfff97d47ae5d99714ac450895afd8a2214772e  telecom_flash_tool/App/Telnet.dll
314ef0e1c636ac553c0e09f992b34573da4a89accb759bda27335e8125c08e35  telecom_flash_tool/App/mfc90u.dll
2026f3c4f830dff6883b88e2647272a52a132f25eb42c0d423e36b3f65a94d08  telecom_flash_tool/App/msvcp80.dll
4608beedd8cf9c3fc5ab03716b4ab6f01c7b7d65a7c072af04f514ffb0e02d01  telecom_flash_tool/App/msvcp90.dll
02bdde38e4c6bd795a092d496b8d6060cdbe71e22ef4d7a204e3050c1be44fa9  telecom_flash_tool/App/msvcr80.dll
e16bc9b66642151de612ee045c2810ca6146975015bd9679a354567f56da2099  telecom_flash_tool/App/msvcr90.dll
d509de10a38ee4d96b7f8a6461ba2630762ce238763fa0e0aec7df590f00d0b6  telecom_flash_tool/Bin/Hash计算器/MyHash.exe
0b5345c52088adf72efe4a8e799fe4f09e65480c4571c03ed5562d66578f7d01  telecom_flash_tool/Bin/Hash计算器/MyHash.ini
c1556480bf3e26d53c8d349abb7d534c5b6e441f7cece408d18d0009545a19a1  telecom_flash_tool/Bin/Hash计算器/MyHashExt.dll
40407e73b01744cebbac7721e64bb85dd7ccf8ba98f1620751a32d6c4604f622  telecom_flash_tool/Bin/Telecom_V2.0.0P1N11.png
22b1b8be37b2fc4f38fec53a6e180c88656153d18e9621c3d75f9430fea24fbe  telecom_flash_tool/Bin/hash.txt
c30da875d71cb4db60baec79ba7a40ed7b3e929eac9a7b40aedfd6d5ca5fafb0  telecom_flash_tool/中兴7607P电信版固件更新工具.exe
```

## 免责声明

工具与固件均来自公开维修资料，仅供自有设备维修与学习使用。刷机有风险，操作前先备份，后果自负。
