---
title: kms 激活
date: 2021-02-08 14:46:16
tags:
  - kms
  - windows
  - office
categories:
top:
---

使用 KMS 激活 Windows 及 Office .

<!-- more -->

## Windows

```shell
slmgr /upk
slmgr /ipk XXXX-XXXX-XXXX-XXXX //Windows版本密钥
slmgr /skms kms.server.ip:port //KMS服务器地址 默认端口1688
slmgr /ato
slmgr /dlv
```

```shell
slmgr /ckms  //清除系统KMS信息
slmgr /rearm //重置计算机的授权状态
```

### Office x86

```shell
cd \Program Files (x86)\Microsoft Office\Office16
cscript ospp.vbs /sethst:kms.server.ip:port
cscript ospp.vbs /inpkey:xxxxx-xxxxx-xxxxx-xxxxx-xxxxx
cscript ospp.vbs /act
cscript ospp.vbs /dstatusall
```

### Office x86_64

```shell
cd \Program Files\Microsoft Office\Office16
cscript ospp.vbs /sethst:kms.server.ip:port
cscript ospp.vbs /inpkey:xxxxx-xxxxx-xxxxx-xxxxx-xxxxx
cscript ospp.vbs /act
cscript ospp.vbs /dstatusall
```

## GVLK keys

> [Appendix A: KMS Client Setup Keys](https://docs.microsoft.com/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj612867(v=ws.11))
>
> Windows: https://docs.microsoft.com/en-us/windows-server/get-started/kmsclientkeys
> Office 2013: https://technet.microsoft.com/en-us/library/dn385360.aspx
> Office 2016 & 2019: https://technet.microsoft.com/en-us/library/dn385360(v=office.16).aspx

## Windows Server 2016

| Operating system edition       | KMS Client Setup Key          |
| :----------------------------- | :---------------------------- |
| Windows Server 2016 Datacenter | CB7KF-BWN84-R7R2Y-793K2-8XDDG |
| Windows Server 2016 Standard   | WC2BQ-8NRM3-FDDYY-2BFGV-KHKQY |
| Windows Server 2016 Essentials | JCKRF-N37P4-C2D82-9YXRT-4M63B |

## Windows 10

| Operating system edition          | KMS Client Setup Key          |
| :-------------------------------- | :---------------------------- |
| Windows 10 Professional           | W269N-WFGWX-YVC9B-4J6C9-T83GX |
| Windows 10 Professional N         | MH37W-N47XK-V7XM9-C7227-GCQG9 |
| Windows 10 Enterprise             | NPPR9-FWDCX-D2C8J-H872K-2YT43 |
| Windows 10 Enterprise N           | DPH2V-TTNVB-4X9Q3-TJR4H-KHJW4 |
| Windows 10 Education              | NW6C2-QMPVW-D7KKK-3GKT6-VCFB2 |
| Windows 10 Education N            | 2WH4N-8QGBV-H22JP-CT43Q-MDWWJ |
| Windows 10 Enterprise 2015 LTSB   | WNMTR-4C88C-JK8YV-HQ7T2-76DF9 |
| Windows 10 Enterprise 2015 LTSB N | 2F77B-TNFGY-69QQF-B8YKP-D69TJ |
| Windows 10 Enterprise 2016 LTSB   | DCPHK-NFMTC-H88MJ-PFHPY-QJ4BJ |
| Windows 10 Enterprise 2016 LTSB N | QFFDN-GRT3P-VKWWX-X7T3R-8B639 |

## Windows Server 2012 R2 and Windows 8.1

| Operating system edition               | KMS Client Setup Key          |
| :------------------------------------- | :---------------------------- |
| Windows 8.1 Professional               | GCRJD-8NW9H-F2CDX-CCM8D-9D6T9 |
| Windows 8.1 Professional N             | HMCNV-VVBFX-7HMBH-CTY9B-B4FXY |
| Windows 8.1 Enterprise                 | MHF9N-XY6XB-WVXMC-BTDCT-MKKG7 |
| Windows 8.1 Enterprise N               | TT4HM-HN7YT-62K67-RGRQJ-JFFXW |
| Windows Server 2012 R2 Server Standard | D2N9P-3P6X9-2R39C-7RTCD-MDVJX |
| Windows Server 2012 R2 Datacenter      | W3GGN-FT8W3-Y4M27-J84CP-Q3VJ9 |
| Windows Server 2012 R2 Essentials      | KNC87-3J2TX-XB4WP-VCPJV-M4FWM |

## Windows Server 2012 and Windows 8

| Operating system edition                | KMS Client Setup Key          |
| :-------------------------------------- | :---------------------------- |
| Windows 8 Professional                  | NG4HW-VH26C-733KW-K6F98-J8CK4 |
| Windows 8 Professional N                | XCVCF-2NXM9-723PB-MHCB7-2RYQQ |
| Windows 8 Enterprise                    | 32JNW-9KQ84-P47T8-D8GGY-CWCK7 |
| Windows 8 Enterprise N                  | JMNMF-RHW7P-DMY6X-RF3DR-X2BQT |
| Windows Server 2012                     | BN3D2-R7TKB-3YPBD-8DRP2-27GG4 |
| Windows Server 2012 N                   | 8N2M2-HWPGY-7PGT9-HGDD8-GVGGY |
| Windows Server 2012 Single Language     | 2WN2H-YGCQR-KFX6K-CD6TF-84YXQ |
| Windows Server 2012 Country Specific    | 4K36P-JN4VD-GDC6V-KDT89-DYFKP |
| Windows Server 2012 Server Standard     | XC9B7-NBPP2-83J2H-RHMBY-92BT4 |
| Windows Server 2012 MultiPoint Standard | HM7DN-YVMH3-46JC3-XYTG7-CYQJJ |
| Windows Server 2012 MultiPoint Premium  | XNH6W-2V9GX-RGJ4K-Y8X6F-QGJ2G |
| Windows Server 2012 Datacenter          | 48HP8-DN98B-MYWDG-T2DCC-8W83P |

## Windows 7 and Windows Server 2008 R2

| Operating system edition                         | KMS Client Setup Key          |
| :----------------------------------------------- | :---------------------------- |
| Windows 7 Professional                           | FJ82H-XT6CR-J8D7P-XQJJ2-GPDD4 |
| Windows 7 Professional N                         | MRPKT-YTG23-K7D7T-X2JMM-QY7MG |
| Windows 7 Professional E                         | W82YF-2Q76Y-63HXB-FGJG9-GF7QX |
| Windows 7 Enterprise                             | 33PXH-7Y6KF-2VJC9-XBBR8-HVTHH |
| Windows 7 Enterprise N                           | YDRBP-3D83W-TY26F-D46B2-XCKRJ |
| Windows 7 Enterprise E                           | C29WB-22CC8-VJ326-GHFJW-H9DH4 |
| Windows Server 2008 R2 Web                       | 6TPJF-RBVHG-WBW2R-86QPH-6RTM4 |
| Windows Server 2008 R2 HPC edition               | TT8MH-CG224-D3D7Q-498W2-9QCTX |
| Windows Server 2008 R2 Standard                  | YC6KT-GKW9T-YTKYR-T4X34-R7VHC |
| Windows Server 2008 R2 Enterprise                | 489J6-VHDMP-X63PK-3K798-CPX3Y |
| Windows Server 2008 R2 Datacenter                | 74YFP-3QFB3-KQT8W-PMXWJ-7M648 |
| Windows Server 2008 R2 for Itanium-based Systems | GT63C-RJFQ3-4GMB6-BRFB9-CB83V |

## Windows Vista and Windows Server 2008

| Operating system edition                       | KMS Client Setup Key          |
| :--------------------------------------------- | :---------------------------- |
| Windows Vista Business                         | YFKBB-PQJJV-G996G-VWGXY-2V3X8 |
| Windows Vista Business N                       | HMBQG-8H2RH-C77VX-27R82-VMQBT |
| Windows Vista Enterprise                       | VKK3X-68KWM-X2YGT-QR4M6-4BWMV |
| Windows Vista Enterprise N                     | VTC42-BM838-43QHV-84HX6-XJXKV |
| Windows Web Server 2008                        | WYR28-R7TFJ-3X2YQ-YCY4H-M249D |
| Windows Server 2008 Standard                   | TM24T-X9RMF-VWXK6-X8JC9-BFGM2 |
| Windows Server 2008 Standard without Hyper-V   | W7VD6-7JFBR-RX26B-YKQ3Y-6FFFJ |
| Windows Server 2008 Enterprise                 | YQGMW-MPWTJ-34KDK-48M3W-X4Q6V |
| Windows Server 2008 Enterprise without Hyper-V | 39BXF-X8Q23-P2WWT-38T2F-G3FPG |
| Windows Server 2008 HPC                        | RCTX3-KWVHP-BR6TB-RB6DM-6X7HP |
| Windows Server 2008 Datacenter                 | 7M67G-PC374-GR742-YH8V4-TCBY3 |
| Windows Server 2008 Datacenter without Hyper-V | 22XQ2-VRXRG-P8D42-K34TD-G3QQC |
| Windows Server 2008 for Itanium-Based Systems  | 4DWFP-JF3DJ-B7DTH-78FJB-PDRHK |