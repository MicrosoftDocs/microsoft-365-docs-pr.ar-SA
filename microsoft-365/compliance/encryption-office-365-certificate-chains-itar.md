---
title: Microsoft 365 التشفير - DOD سحابة القطاع الحكومي High
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 10/16/2020
audience: Admin
ms.topic: overview
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.collection:
- M365-security-compliance
- Strat_O365_IP
description: عرض قائمة كاملة بشهادات DOD سحابة القطاع الحكومي الجذر العالي والمهاني (CAs) في Microsoft 365.
ms.openlocfilehash: 5db850f59223238bdd9e749f442caf9eab93ea29
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63571099"
---
# <a name="microsoft-365-encryption-chains---dod-and-gcc-high"></a>Microsoft 365 التشفير - DOD سحابة القطاع الحكومي High

Microsoft 365 عدد من موفري الشهادات المختلفين. يصف ما يلي القائمة الكاملة للشهادات الجذر Microsoft 365 المعروفة التي **قد** يواجهها سحابة القطاع الحكومي العملاء الأعلى عند الوصول إلى Microsoft 365. للحصول على معلومات حول الشهادات التي قد تحتاج إلى تثبيتها في البنية الأساسية الخاصة بك، راجع التخطيط لشهادات [SSL](../enterprise/plan-for-third-party-ssl-certificates.md) الخاصة Microsoft 365.

تنطبق معلومات الشهادة التالية على جميع عملاء **DOD سحابة القطاع الحكومي الأعلى**.

التحديث الأخير: **16/10/2020**

> [!NOTE]
> للحصول على معلومات الشهادة التي تنطبق على العملاء في جميع **أنحاء العالم،** راجع Microsoft 365 [التشفير.](encryption-office-365-certificate-chains.md)

| **نوع الشهادة** | **تنزيل P7b** | **نقاط نهاية CRL** | **نقاط نهاية OCSP** |
| --- | --- | --- | --- | --- |
| شهادات الجذر والمتوسط الموثوق بها بشكل عام | [Microsoft 365 شهادة ITAR (P7B)](https://download.microsoft.com/download/b/3/a/b3ae08a2-516c-46a9-8723-6256e4fd6383/m365_chain_certs_itar20201012.p7b) | crl.entrust.net<br>crl3.digicert.com<br>crl4.digicert.com | ocsp.digicert.com<br>ocsp.entrust.net |

قم بتوسيع الأقسام الجذر والمتوسطة أدناه لمشاهدة تفاصيل إضافية حول موفري الشهادات.

## <a name="microsoft-365-certificate-details"></a>**Microsoft 365 تفاصيل الشهادة**

### <a name="baltimore-cybertrust-root"></a>**جذر Baltimore CyberTrust**

| **الموضوع** | CN=Baltimore CyberTrust Root<br>OU=CyberTrust<br>O=Baltimore<br>C=IE |
| --- | --- |
| **الرقم التسلسلي** | 02:00:00:B9 |
| **طول المفتاح العمومي** | RSA 2048 بت (e 65537) |
| **خوارزمية التوقيع** | sha1RSA |
| **الصلاحية ليس قبل** | 12 مايو 18:46:00 2000 UTC |
| **الصلاحية ليس بعد** | 12 مايو 23:59:00 2025 UTC |
| **معرف مفتاح الموضوع** | e5:9d:59:30:82:47:58:cc:ac:fa:08:54:36:86:7b:3a:b5:04:4d:f0 |
| **الطباعة المصغرة (SHA-1)** | D4DE20D05E66FC53FE1A50882C78DB2852CAE474 |
| **الطباعة المصغرة (SHA-256)** | 16AF57A9F676B0AB126095AA5EBADEF22AB31119D644AC95CD4B93DBF3F26AEB |
| **تثبيت (SHA-256)** | Y9mvm0exBk1JoQ57f9Vm28jKo5lFm/woKcVxrYxu80o= |

### <a name="digicert-cloud-services-ca-1"></a>**DigiCert Cloud Services CA-1**

| **الموضوع** | CN=DigiCert Cloud Services CA-1<br>O=DigiCert Inc<br>C=US |
| --- | --- |
| **مصدر** | CN=DigiCert Global Root CA<br>OU=www.digicert.com<br>O=DigiCert Inc<br>C=US |
| **الرقم التسلسلي** | 01:9E:C1:C6:BD:3F:59:7B:B2:0C:33:38:E5:51:D8:77 |
| **طول المفتاح العمومي** | RSA 2048 بت (e 65537) |
| **خوارزمية التوقيع** | sha256RSA |
| **الصلاحية ليس قبل** | 04 أغسطس 12:00:00 2015 UTC |
| **الصلاحية ليس بعد** | 04 أغسطس 12:00:00 2030 UTC |
| **معرف مفتاح الموضوع** | dd:51:d0:a2:31:73:a9:73:ae:8f:b4:01:7e:5d:8c:57:cb:9f:f0:f7 |
| **معرف مفتاح المرجع** | keyid:03:de:50:35:56:d1:4c:bb:66:f0:a3:e2:1b:1b:c3:97:b2:3d:d1:55 |
| **الطباعة المصغرة (SHA-1)** | 81B68D6CD2F221F8F534E677523BB236BBA1DC56 |
| **الطباعة المصغرة (SHA-256)** | 2F6889961A7CA7067E8BA103C2CF9B9A924F8CA293F11178E23A1978D2F133D3 |
| **تثبيت (SHA-256)** | UgpUVparimk8QCjtWQaUQ7EGrtrykc/L8N66EhFY3VE= |
| **عناوين URL CRL** | http://crl4.digicert.com/DigiCertGlobalRootCA.crl<br>http://crl3.digicert.com/DigiCertGlobalRootCA.crl |
| **عناوين URL ل OCSP** | http://ocsp.digicert.com |

### <a name="digicert-cloud-services-ca-1"></a>**DigiCert Cloud Services CA-1**

| **الموضوع** | CN=DigiCert Cloud Services CA-1<br>O=DigiCert Inc<br>C=US |
| --- | --- |
| **مصدر** | CN=DigiCert Global Root CA, OU=www.digicert.com, O=DigiCert Inc, C=US |
| **الرقم التسلسلي** | 0F:17:1A:48:C6:F2:23:80:92:18:CD:2E:D6:DD:C0:E8 |
| **طول المفتاح العمومي** | RSA 2048 بت |
| **خوارزمية التوقيع** | sha256RSA |
| **الصلاحية ليس قبل** | الخميس، 24 سبتمبر 2020 5:00 م |
| **الصلاحية ليس حتى** | الثلاثاء، 24 سبتمبر 2030 4:59 م |
| **معرف مفتاح الموضوع** | DD51D0A23173A973AE8FB4017E5D8C57CB9FF0F7 |
| **معرف مفتاح المرجع** | KeyID:03:de:50:35:56:d1:4c:bb:66:f0:a3:e2:1b:1b:c3:97:b2:3d:d1:55 |
| **الطباعة المصغرة (SHA-1)** | B3F6B64A07BB9611F47174407841F564FB991F29 |
| **الطباعة المصغرة (SHA-256)** | 5F88694615E4C61686E106B84C3338C6720C535F60D36F61282ED15E1977DDD44 |
| **عناوين URL CRL** | http://crl3.digicert.com/DigiCertGlobalRootCA.crl http://crl4.digicert.com/DigiCertGlobalRootCA.crl |
| **عناوين URL ل OCSP** | http://ocsp.digicert.com |

### <a name="digicert-global-root-ca"></a>**DigiCert Global Root CA**

| **الموضوع** | CN=DigiCert Global Root CA<br>OU=www.digicert.com<br>O=DigiCert Inc<br>C=US |
| --- | --- |
| **الرقم التسلسلي** | 08:3B:E0:56:90:42:46:B1:A1:75:6A:C9:59:91:C7:4A |
| **طول المفتاح العمومي** | RSA 2048 بت (e 65537) |
| **خوارزمية التوقيع** | sha1RSA |
| **الصلاحية ليس قبل** | 10 نوفمبر 00:00:00 2006 UTC |
| **الصلاحية ليس بعد** | 10 نوفمبر 00:00:00 2031 UTC |
| **معرف مفتاح الموضوع** | 03:de:50:35:56:d1:4c:bb:66:f0:a3:e2:1b:1b:c3:97:b2:3d:d1:55 |
| **معرف مفتاح المرجع** | keyid:03:de:50:35:56:d1:4c:bb:66:f0:a3:e2:1b:1b:c3:97:b2:3d:d1:55 |
| **الطباعة المصغرة (SHA-1)** | A8985D3A65E5E5C4B2D7D66D40C6DD2FB19C5436 |
| **الطباعة المصغرة (SHA-256)** | 4348A0E9444C78CB265E058D5E8944B4D84F9662BD26DB257F8934A443C70161 |
| **تثبيت (SHA-256)** | r/mIkG3eEpVdm+u/ko/cwxzOMo1bk4TyHIlByibiA5E= |

### <a name="digicert-global-root-g2"></a>**DigiCert Global Root G2**

| **الموضوع** | CN=DigiCert Global Root G2<br>OU=www.digicert.com<br>O=DigiCert Inc<br>C=US |
| --- | --- |
| **مصدر** | CN=DigiCert Global Root G2, OU=www.digicert.com, O=DigiCert Inc, C=US |
| **الرقم التسلسلي** | 03:3A:F1:E6:A7:11:A9:A0:BB:28:64:B1:1D:09:FA:E5 |
| **طول المفتاح العمومي** | RSA 2048 بت |
| **خوارزمية التوقيع** | sha256RSA |
| **الصلاحية ليس قبل** | الخميس، 1 أغسطس 2013 5:00 صباحا |
| **الصلاحية ليس حتى** | الجمعة، 15 يناير 2038 4:00 صباحا |
| **معرف مفتاح الموضوع** | 4E2254201895E6E36EE60FFAFAB912ED06178F39 |
| **معرف مفتاح المرجع** | KeyID:4e:22:54:20:18:95:e6:e3:6e:e6:0f:fa:b9:12:ed:06:17:8f:39 |
| **الطباعة المصغرة (SHA-1)** | DF3C24F9BFD666761B268073FE06D1CC8D4F82A4 |
| **الطباعة المصغرة (SHA-256)** | CB3CCBB76031E5E0138F8DD39A23F9DE47FFC35E43C1144CEA27D46A5AB1CB5F |

### <a name="digicert-high-assurance-ev-root-ca"></a>**DigiCert High Assurance EV Root CA**

| **الموضوع** | CN=DigiCert High Assurance EV Root CA<br>OU=www.digicert.com<br>O=DigiCert Inc<br>C=US |
| --- | --- |
| **الرقم التسلسلي** | 02:AC:5C:26:6A:0B:40:9B:8F:0B:79:F2:AE:46:25:77 |
| **طول المفتاح العمومي** | RSA 2048 بت (e 65537) |
| **خوارزمية التوقيع** | sha1RSA |
| **الصلاحية ليس قبل** | 10 نوفمبر 00:00:00 2006 UTC |
| **الصلاحية ليس بعد** | 10 نوفمبر 00:00:00 2031 UTC |
| **معرف مفتاح الموضوع** | b1:3e:c3:69:03:f8:bf:47:01:d4:98:26:1a:08:02:ef:63:64:2b:c3 |
| **معرف مفتاح المرجع** | keyid:b1:3e:c3:69:03:f8:bf:47:01:d4:98:26:1a:08:02:ef:63:64:2b:c3 |
| **الطباعة المصغرة (SHA-1)** | 5FB7EE0633E259DBAD0C4C9AE6D38F1A61C7DC25 |
| **الطباعة المصغرة (SHA-256)** | 7431E5F4C3C1CE4690774F0B61E05440883BA9A01ED00BA6ABD7806ED3B118CF |
| **تثبيت (SHA-256)** | WoiWRyIOVNa9ihaBciRSC7XHjliYS9VwUGOIud4PB18= |

### <a name="digicert-sha2-extended-validation-server-ca"></a>**DigiCert SHA2 Extended Validation Server CA**

| **الموضوع** | CN=DigiCert SHA2 Extended Validation Server CA<br>OU=www.digicert.com<br>O=DigiCert Inc<br>C=US |
| --- | --- |
| **الرقم التسلسلي** | 0C:79:A9:44:B0:8C:11:95:20:92:61:5F:E2:6B:1D:83 |
| **طول المفتاح العمومي** | RSA 2048 بت (e 65537) |
| **خوارزمية التوقيع** | sha256RSA |
| **الصلاحية ليس قبل** | 22 أكتوبر 00:00:00 2013 UTC |
| **الصلاحية ليس بعد** | 22 أكتوبر 00:00:00 2028 UTC |
| **معرف مفتاح الموضوع** | 3D:D3:50:A5:D6:A0:AD:EE:F3:4A:60:0A:65:D3:21:D4:F8:F8:D6:0F |
| **معرف مفتاح المرجع** | keyID:b1:3e:c3:69:03:f8:bf:47:01:d4:98:26:1a:08:02:ef:63:64:2b:c3 |
| **الطباعة المصغرة (SHA-1)** | 7E2F3A4F8FE8FA8A5730AECA029696637E986F3F |
| **الطباعة المصغرة (SHA-256)** | 403E062A2653059113285BAF80A0D4AE422C848C9F78FAD01FC94BC5B87FEF1A |

### <a name="digicert-sha2-secure-server-ca"></a>**DigiCert SHA2 Secure Server CA**

| **الموضوع** | CN=DigiCert SHA2 Secure Server CA<br>O=DigiCert Inc<br>C=US |
| --- | --- |
| **مصدر** | CN=DigiCert Global Root CA, OU=www.digicert.com, O=DigiCert Inc, C=US |
| **الرقم التسلسلي** | 01:FD:A3:EB:6E:CA:75:C8:88:43:8B:72:4B:CF:BC:91 |
| **طول المفتاح العمومي** | RSA 2048 بت |
| **خوارزمية التوقيع** | sha256RSA |
| **الصلاحية ليس قبل** | الجمعة، 8 مارس 2013 4:00 صباحا |
| **الصلاحية ليس حتى** | الأربعاء، 8 مارس 2023 4:00 صباحا |
| **معرف مفتاح الموضوع** | 0F80611C823161D52F28E78D4638B42CE1C6D9E2 |
| **معرف مفتاح المرجع** | KeyID:03:de:50:35:56:d1:4c:bb:66:f0:a3:e2:1b:1b:c3:97:b2:3d:d1:55 |
| **الطباعة المصغرة (SHA-1)** | 1FB86B1168EC743154062E8C9CC5B171A4B7CCB4 |
| **الطباعة المصغرة (SHA-256)** | 154C433C491929C5EF686E838E323664A00E6A0D822CCC958FB4DAB03E49A08F |
| **عناوين URL CRL** | http://crl3.digicert.com/DigiCertGlobalRootCA.crl http://crl4.digicert.com/DigiCertGlobalRootCA.crl |
| **عناوين URL ل OCSP** | http://ocsp.digicert.com |

### <a name="digicert-sha2-secure-server-ca"></a>**DigiCert SHA2 Secure Server CA**

| **الموضوع** | CN=DigiCert SHA2 Secure Server CA<br>O=DigiCert Inc<br>C=US |
| --- | --- |
| **مصدر** | CN=DigiCert Global Root CA, OU=www.digicert.com, O=DigiCert Inc, C=US |
| **الرقم التسلسلي** | 02:74:2E:AA:17:CA:8E:21:C7:17:BB:1F:FC:FD:0C:A0 |
| **طول المفتاح العمومي** | RSA 2048 بت |
| **خوارزمية التوقيع** | sha256RSA |
| **الصلاحية ليس قبل** | الثلاثاء، 22 سبتمبر 2020 5:00 م |
| **الصلاحية ليس حتى** | الأحد، 22 سبتمبر 2030 4:59 م |
| **معرف مفتاح الموضوع** | 0F80611C823161D52F28E78D4638B42CE1C6D9E2 |
| **معرف مفتاح المرجع** | KeyID:03:de:50:35:56:d1:4c:bb:66:f0:a3:e2:1b:1b:c3:97:b2:3d:d1:55 |
| **الطباعة المصغرة (SHA-1)** | 626D44E704D1CEABE3BF0D53397464AC8080142C |
| **الطباعة المصغرة (SHA-256)** | C1AD7778796D20BCA65C889A2655021156528BB62FF5FA43E1B8E5A83E3D2EAA |
| **عناوين URL CRL** | http://crl3.digicert.com/DigiCertGlobalRootCA.crl http://crl4.digicert.com/DigiCertGlobalRootCA.crl |
| **عناوين URL ل OCSP** | http://ocsp.digicert.com |

### <a name="digicert-tls-rsa-sha256-2020-ca1"></a>**DigiCert TLS RSA SHA256 2020 CA1**

| **الموضوع** | CN=DigiCert TLS RSA SHA256 2020 CA1<br>O=DigiCert Inc<br>C=US |
| --- | --- |
| **مصدر** | CN=DigiCert Global Root CA, OU=www.digicert.com, O=DigiCert Inc, C=US |
| **الرقم التسلسلي** | 0A:35:08:D5:5C:29:2B:01:7D:F8:AD:65:C0:0F:F7:E4 |
| **طول المفتاح العمومي** | RSA 2048 بت |
| **خوارزمية التوقيع** | sha256RSA |
| **الصلاحية ليس قبل** | الأربعاء، 23 سبتمبر 2020 5:00 م |
| **الصلاحية ليس حتى** | الاثنين، 23 سبتمبر 2030 4:59 م |
| **معرف مفتاح الموضوع** | B76BA2EAA8AA848C79EAB4DA0F98B2C59576B9F4 |
| **معرف مفتاح المرجع** | KeyID:03:de:50:35:56:d1:4c:bb:66:f0:a3:e2:1b:1b:c3:97:b2:3d:d1:55 |
| **الطباعة المصغرة (SHA-1)** | 6938FD4D98BAB03FAADB97B34396831E3780AEA1 |
| **الطباعة المصغرة (SHA-256)** | 25768713D3B459F9382D2A594F85F34709FD2A8930731542A4146FFB246BEC69 |
| **عناوين URL CRL** | http://crl3.digicert.com/DigiCertGlobalRootCA.crl http://crl4.digicert.com/DigiCertGlobalRootCA.crl |
| **عناوين URL ل OCSP** | http://ocsp.digicert.com |

### <a name="entrust-root-certification-authority"></a>**مرجع المصادقة الجذر المعاون**

| **الموضوع** | CN=Entrust Root Certification Authority<br>OU="(c) 2006 Entrust, Inc."<br>يتم تضمين OU=www.entrust.net/CPS بالإشارة<br>OU=see www.entrust.net/legal-terms<br>O=&quot;Entrust, Inc.&quot;<br>C=US |
| --- | --- |
| **الرقم التسلسلي** | 45:6B:50:54 |
| **طول المفتاح العمومي** | RSA 2048 بت (e 65537) |
| **خوارزمية التوقيع** | sha1RSA |
| **الصلاحية ليس قبل** | 27 نوفمبر 12:23:42 2006 UTC |
| **الصلاحية ليس بعد** | 27 نوفمبر 12:53:42 2026 UTC |
| **معرف مفتاح الموضوع** | 68:90:E4:67:A4:A6:53:80:C7:86:66:A4:F1:F7:4B:43:FB:84:BD:6D |
| **معرف مفتاح المرجع** | keyID:68:90:e4:67:a4:a6:53:80:c7:86:66:a4:f1:f7:4b:43:fb:84:bd:6d |
| **الطباعة المصغرة (SHA-1)** | B31EB1B740E36C8402DADC37D44DF5D4674952F9 |
| **الطباعة المصغرة (SHA-256)** | 73C176434F1BC6D5ADF45B0E76E727287C8DE57616C1E6E6141A2B2CBC7D8E4C |

### <a name="entrust-root-certification-authority---g2"></a>**مرجع الاعتماد الجذر المعاون - G2**

| **الموضوع** | CN=Entrust Root Certification Authority - G2<br>OU=&quot;(c) 2009 Entrust, Inc. - للاستخدام المعتمد فقط&quot;<br>OU=see www.entrust.net/legal-terms<br>O=&quot;Entrust, Inc.&quot;<br>C=US |
| --- | --- |
| **الرقم التسلسلي** | 4A:53:8C:28 |
| **طول المفتاح العمومي** | RSA 2048 بت (e 65537) |
| **خوارزمية التوقيع** | sha256RSA |
| **الصلاحية ليس قبل** | يوليو 07 17:25:54 2009 UTC |
| **الصلاحية ليس بعد** | 07 ديسمبر 17:55:54 2030 UTC |
| **معرف مفتاح الموضوع** | 6a:72:26:7a:d0:1e:ef:7d:e7:3b:69:51:d4:6c:8d:9f:90:12:66:ab |
| **الطباعة المصغرة (SHA-1)** | 8CF427FD790C3AD166068DE81E57EFBB932272D4 |
| **الطباعة المصغرة (SHA-256)** | 43DF5774B03E7FEF5FE40D931A7BEDF1BB2E6B42738C4E6D3841103D3AA7F339 |
| **تثبيت (SHA-256)** | du6FkDdMcVQ3u8prumAo6t3i3G27uMP2EOhR8R0at/U= |

### <a name="entrustnet-certification-authority-2048"></a>**Entrust.net المشهادات (2048)**

| **الموضوع** | CN=Entrust.net Certificationy (2048)<br>OU=(c) 1999 Entrust.net Limited<br>OU=www.entrust.net/CPS2048\_ incorp. بواسطة المرف. (حد s liab.)<br>O=Entrust.net |
| --- | --- |
| **الرقم التسلسلي** | 38:63:DE:F8 |
| **طول المفتاح العمومي** | RSA 2048 بت (e 65537) |
| **خوارزمية التوقيع** | sha1RSA |
| **الصلاحية ليس قبل** | 24 ديسمبر 17:50:51 1999 UTC |
| **الصلاحية ليس بعد** | 24 يوليو 14:15:12 2029 UTC |
| **معرف مفتاح الموضوع** | 55:e4:81:d1:11:80:be:d8:89:b9:08:a3:31:f9:a1:24:09:16:b9:70 |
| **الطباعة المصغرة (SHA-1)** | 503006091D97D4F5AE39F7CBE7927D7D652D3431 |
| **الطباعة المصغرة (SHA-256)** | 6DC47172E01CBCB0BF62580D895FE2B8AC9AD4F873801E0C10B9C837D21EB177 |
| **تثبيت (SHA-256)** | HqPF5D7WbC2imDpCpKebHpBnhs6fG1hiFBmgBGOofTg= |

### <a name="entrust-certification-authority---l1c"></a>**المرجع الممصادقة المعاون - L1C**

| **الموضوع** | CN=Entrust Certification Authority - L1C<br>OU=&quot;(c) 2009 Entrust, Inc.&quot;<br>يتم تضمين OU=www.entrust.net/rpa حسب المرجع<br>O=&quot;Entrust, Inc.&quot;<br>C=US |
| --- | --- |
| **مصدر** | CN=Entrust.net Certificationy (2048)<br>OU=(c) 1999 Entrust.net Limited<br>OU=www.entrust.net/CPS2048\_ incorp. بواسطة المرف. (حدود liab.)<br>O=Entrust.net |
| **الرقم التسلسلي** | 4C:0E:8C:39 |
| **طول المفتاح العمومي** | RSA 2048 بت (e 65537) |
| **خوارزمية التوقيع** | sha1RSA |
| **الصلاحية ليس قبل** | 11 نوفمبر 15:40:40 2011 UTC |
| **الصلاحية ليس بعد** | 11 نوفمبر 02:51:17 2021 UTC |
| **معرف مفتاح الموضوع** | 1e:f1:ab:89:06:f8:49:0f:01:33:77:ee:14:7a:ee:19:7c:93:28:4d |
| **معرف مفتاح المرجع** | keyid:55:e4:81:d1:11:80:be:d8:89:b9:08:a3:31:f9:a1:24:09:16:b9:70 |
| **الطباعة المصغرة (SHA-1)** | C53E73073F93CE7895DE7484126BC303DAB9E657 |
| **الطباعة المصغرة (SHA-256)** | 0EE4DAF71A85D842D23F4910FD4C909B7271861931F1D5FEAC868225F52700E2 |
| **تثبيت (SHA-256)** | VFv5NemtodoRftw8KsvFb8AoCWWOJL6bOJS+Ui0bQ94= |
| **عناوين URL CRL** | http://crl.entrust.net/2048ca.crl |
| **عناوين URL ل OCSP** | http://ocsp.entrust.net |

### <a name="entrust-certification-authority---l1e"></a>**المرجع الممصادقة المعاون - L1E**

| **الموضوع** | CN=Entrust Certification Authority - L1E<br>OU=&quot;(c) 2009 Entrust, Inc.&quot;<br>يتم تضمين OU=www.entrust.net/rpa حسب المرجع<br>O=&quot;Entrust, Inc.&quot;<br>C=US |
| --- | --- |
| **مصدر** | CN=Entrust.net Certificationy (2048)<br>OU=(c) 1999 Entrust.net Limited<br>OU=www.entrust.net/CPS2048\_ incorp. بواسطة المرف. (حدود liab.)<br>O=Entrust.net |
| **الرقم التسلسلي** | 4C:0E:C9:18 |
| **طول المفتاح العمومي** | RSA 2048 بت (e 65537) |
| **خوارزمية التوقيع** | sha1RSA |
| **الصلاحية ليس قبل** | 11 نوفمبر 15:40:40 2011 UTC |
| **الصلاحية ليس بعد** | 11 نوفمبر 02:51:17 2021 UTC |
| **معرف مفتاح الموضوع** | 5B:41:8A:B2:C4:43:C1:BD:BF:C8:54:41:55:9D:E0:96:AD:FF:B9:A1 |
| **معرف مفتاح المرجع** | keyid:68:90:e4:67:a4:a6:53:80:c7:86:66:a4:f1:f7:4b:43:fb:84:bd:6d |
| **الطباعة المصغرة (SHA-1)** | 8A000CC056F7D17349F045BEB0319A3B91C9F979 |
| **الطباعة المصغرة (SHA-256)** | 3C7A634E5778A0F731972B702DAE24B2CF2060219F607E69878B164C61A06C41 |
| **عناوين URL CRL** | http://crl.entrust.net/rootca1.crl |
| **عناوين URL ل OCSP** | http://ocsp.entrust.net |

### <a name="entrust-certification-authority---l1k"></a>**المرجع الممصادقة المعاون - L1K**

| **الموضوع** | CN=Entrust Certification Authority - L1K<br>OU=&quot;(c) 2012 Entrust, Inc. - للاستخدام المعتمد فقط&quot;<br>OU=see www.entrust.net/legal-terms<br>O=&quot;Entrust, Inc.&quot;<br>C=US |
| --- | --- |
| **مصدر** | CN=Entrust Root Certification Authority - G2<br>OU=&quot;(c) 2009 Entrust, Inc. - للاستخدام المعتمد فقط&quot;<br>OU=see www.entrust.net/legal-terms<br>O=&quot;Entrust, Inc.&quot;<br>C=US |
| **الرقم التسلسلي** | 0E:E9:4C:C3:00:00:00:00:51:D3:77:85 |
| **طول المفتاح العمومي** | RSA 2048 بت (e 65537) |
| **خوارزمية التوقيع** | sha256RSA |
| **الصلاحية ليس قبل** | 05 أكتوبر 19:13:56 2015 UTC |
| **الصلاحية ليس بعد** | 05 ديسمبر 19:43:56 2030 UTC |
| **معرف مفتاح الموضوع** | 82:a2:70:74:dd:bc:53:3f:cf:7b:d4:f7:cd:7f:a7:60:c6:0a:4c:bf |
| **معرف مفتاح المرجع** | keyid:6a:72:26:7a:d0:1e:ef:7d:e7:3b:69:51:d4:6c:8d:9f:90:12:66:ab |
| **الطباعة المصغرة (SHA-1)** | F21C12F46CDB6B2E16F09F9419CDFF328437B2D7 |
| **الطباعة المصغرة (SHA-256)** | 13EFB39A2F6654E8C67BD04F4C6D4C90CD6CAB5091BCEDC73787F6B77D3D3FE7 |
| **تثبيت (SHA-256)** | 980Ionqp3wkYtN9SZVgMzuWQzJta1nfxNPwTem1X0uc= |
| **عناوين URL CRL** | http://crl.entrust.net/g2ca.crl |
| **عناوين URL ل OCSP** | http://ocsp.entrust.net |

### <a name="entrust-certification-authority---l1m"></a>**المرجع الممصادقة المعاون - L1M**

| **الموضوع** | CN=Entrust Certification authority - L1M, OU=&quot;(c) 2014 Entrust, Inc. - للاستخدام المعتمد فقط&quot;<br>OU=see www.entrust.net/legal-terms<br>O=&quot;Entrust, Inc.&quot;<br>C=US |
| --- | --- |
| **مصدر** | CN=Entrust Root Certification Authority - G2<br>OU=&quot;(c) 2009 Entrust, Inc. - للاستخدام المعتمد فقط&quot;<br>OU=see www.entrust.net/legal-terms<br>O=&quot;Entrust, Inc.&quot;<br>C=US |
| **الرقم التسلسلي** | 61:A1:E7:D2:00:00:00:00:51:D3:66:A6 |
| **طول المفتاح العمومي** | RSA 2048 بت (e 65537) |
| **خوارزمية التوقيع** | sha256RSA |
| **الصلاحية ليس قبل** | 15 ديسمبر 07:25:03 2014 UTC |
| **الصلاحية ليس بعد** | 15 أكتوبر 08:55:03 2030 UTC |
| **معرف مفتاح الموضوع** | C3:F7:D0:B5:2A:30:AD:AF:0D:91:21:70:39:54:DD:BC:89:70:C7:3A |
| **معرف مفتاح المرجع** | keyid:6a:72:26:7a:d0:1e:ef:7d:e7:3b:69:51:d4:6c:8d:9f:90:12:66:ab |
| **الطباعة المصغرة (SHA-1)** | CC136695639065FAB47074D28C55314C66077E90 |
| **الطباعة المصغرة (SHA-256)** | 75C5B3F01FD1F51A2C447AB7C785D72E69FA9C472C08571E7EADF3B8EABAE70C |
| **عناوين URL CRL** | http://crl.entrust.net/g2ca.crl |
| **عناوين URL ل OCSP** | http://ocsp.entrust.net |

### <a name="microsoft-azure-tls-issuing-ca-01"></a>**إصدار CA 01 من Microsoft Azure TLS**

| **الموضوع** | CN=Microsoft Azure TLSاصدر CA 01<br>O=Microsoft Corporation<br>C=US |
| --- | --- |
| **مصدر** | CN=DigiCert Global Root G2, OU=www.digicert.com, O=DigiCert Inc, C=US |
| **الرقم التسلسلي** | 0A:AF:A6:C5:CA:63:C4:51:41:EA:3B:E1:F7:C7:53:17 |
| **طول المفتاح العمومي** | RSA 4096 بت |
| **خوارزمية التوقيع** | sha384RSA |
| **الصلاحية ليس قبل** | الأربعاء، 29 يوليو 2020 5:30 صباحا |
| **الصلاحية ليس حتى** | الخميس، 27 يونيو 2024 4:59 م |
| **معرف مفتاح الموضوع** | 0F205DD7A15795DB92CF2BD0C7C27704CE728076 |
| **معرف مفتاح المرجع** | KeyID:4e:22:54:20:18:95:e6:e3:6e:e6:0f:fa:b9:12:ed:06:17:8f:39 |
| **الطباعة المصغرة (SHA-1)** | 2F2877C5D778C31E0F29C7E371DF5471BD673173 |
| **الطباعة المصغرة (SHA-256)** | 24C7299864E0A2A6964F551C0E8DF2461532FA8C48E4DBBB6080716691F190E5 |
| **عناوين URL CRL** | http://crl3.digicert.com/DigiCertGlobalRootG2.crl http://crl4.digicert.com/DigiCertGlobalRootG2.crl |
| **عناوين URL ل OCSP** | http://ocsp.digicert.com |

### <a name="microsoft-azure-tls-issuing-ca-02"></a>**إصدار CA 02 من Microsoft Azure TLS**

| **الموضوع** | CN=Microsoft Azure TLSاصدر CA 02<br>O=Microsoft Corporation<br>C=US |
| --- | --- |
| **مصدر** | CN=DigiCert Global Root G2, OU=www.digicert.com, O=DigiCert Inc, C=US |
| **الرقم التسلسلي** | 0C:6A:E9:7C:CE:D5:99:83:86:90:A0:0A:9E:A5:32:14 |
| **طول المفتاح العمومي** | RSA 4096 بت |
| **خوارزمية التوقيع** | sha384RSA |
| **الصلاحية ليس قبل** | الأربعاء، 29 يوليو 2020 5:30 صباحا |
| **الصلاحية ليس حتى** | الخميس، 27 يونيو 2024 4:59 م |
| **معرف مفتاح الموضوع** | 00AB91FC216226979AA8791B61419060A96267FD |
| **معرف مفتاح المرجع** | KeyID:4e:22:54:20:18:95:e6:e3:6e:e6:0f:fa:b9:12:ed:06:17:8f:39 |
| **الطباعة المصغرة (SHA-1)** | E7EEA674CA718E3BEFD90858E09F8372AD0AE2AA |
| **الطباعة المصغرة (SHA-256)** | 15A98761EBE011554DA3A46D206B0812CB2EB69AE87AAA11A6DD4CB84ED5142A |
| **عناوين URL CRL** | http://crl3.digicert.com/DigiCertGlobalRootG2.crl http://crl4.digicert.com/DigiCertGlobalRootG2.crl |
| **عناوين URL ل OCSP** | http://ocsp.digicert.com |

### <a name="microsoft-azure-tls-issuing-ca-05"></a>**إصدار CA 05 ل Microsoft Azure TLS**

| **الموضوع** | CN=Microsoft Azure TLSاصدر CA 05<br>O=Microsoft Corporation<br>C=US |
| --- | --- |
| **مصدر** | CN=DigiCert Global Root G2, OU=www.digicert.com, O=DigiCert Inc, C=US |
| **الرقم التسلسلي** | 0D:7B:ED:E9:7D:82:09:96:7A:52:63:1B:8B:DD:18:BD |
| **طول المفتاح العمومي** | RSA 4096 بت |
| **خوارزمية التوقيع** | sha384RSA |
| **الصلاحية ليس قبل** | الأربعاء، 29 يوليو 2020 5:30 صباحا |
| **الصلاحية ليس حتى** | الخميس، 27 يونيو 2024 4:59 م |
| **معرف مفتاح الموضوع** | C7B29C7F1CE3B85AEFE9681AA85D94C126526A68 |
| **معرف مفتاح المرجع** | KeyID:4e:22:54:20:18:95:e6:e3:6e:e6:0f:fa:b9:12:ed:06:17:8f:39 |
| **الطباعة المصغرة (SHA-1)** | 6C3AF02E7F269AA73AFD0EFF2A88A4A1F04ED1E5 |
| **الطباعة المصغرة (SHA-256)** | D6831BA43607F5AC19778D627531562AF55145F191CAB5EFAFA0E0005442B302 |
| **عناوين URL CRL** | http://crl3.digicert.com/DigiCertGlobalRootG2.crl http://crl4.digicert.com/DigiCertGlobalRootG2.crl |
| **عناوين URL ل OCSP** | http://ocsp.digicert.com |

### <a name="microsoft-azure-tls-issuing-ca-06"></a>**إصدار CA 06 ل Microsoft Azure TLS**

| **الموضوع** | CN=Microsoft Azure TLSاصدر CA 06<br>O=Microsoft Corporation<br>C=US |
| --- | --- |
| **مصدر** | CN=DigiCert Global Root G2, OU=www.digicert.com, O=DigiCert Inc, C=US |
| **الرقم التسلسلي** | 02:E7:91:71:FB:80:21:E9:3F:E2:D9:83:83:4C:50:C0 |
| **طول المفتاح العمومي** | RSA 4096 بت |
| **خوارزمية التوقيع** | sha384RSA |
| **الصلاحية ليس قبل** | الأربعاء، 29 يوليو 2020 5:30 صباحا |
| **الصلاحية ليس حتى** | الخميس، 27 يونيو 2024 4:59 م |
| **معرف مفتاح الموضوع** | D5C1673AC2A39DF477525B59123829E65568BBA5 |
| **معرف مفتاح المرجع** | KeyID:4e:22:54:20:18:95:e6:e3:6e:e6:0f:fa:b9:12:ed:06:17:8f:39 |
| **الطباعة المصغرة (SHA-1)** | 30E01761AB97E59A06B41EF20AF6F2DE7EF4F7B0 |
| **الطباعة المصغرة (SHA-256)** | 48FF8B494668C752304B48BFE818758987DEF6582E5F09B921F4B60BB3D6A8DD |
| **عناوين URL CRL** | http://crl3.digicert.com/DigiCertGlobalRootG2.crl http://crl4.digicert.com/DigiCertGlobalRootG2.crl |
| **عناوين URL ل OCSP** | http://ocsp.digicert.com |

### <a name="microsoft-it-tls-ca-1"></a>**Microsoft IT TLS CA 1**

| **الموضوع** | CN=Microsoft IT TLS CA 1<br>OU=Microsoft IT<br>O=Microsoft Corporation<br>L=Redmond<br>S=Washington<br>C=US |
| --- | --- |
| **مصدر** | CN=Baltimore CyberTrust Root<br>OU=CyberTrust<br>O=Baltimore<br>C=IE |
| **الرقم التسلسلي** | 08:B8:7A:50:1B:BE:9C:DA:2D:16:4D:3E:39:51:BF:55 |
| **طول المفتاح العمومي** | RSA 4096 بت (e 65537) |
| **خوارزمية التوقيع** | sha256RSA |
| **الصلاحية ليس قبل** | 20 مايو 12:51:28 2016 UTC |
| **الصلاحية ليس بعد** | 20 مايو 12:51:28 2024 UTC |
| **معرف مفتاح الموضوع** | 58:88:9f:d6:dc:9c:48:22:b7:14:3e:ff:84:88:e8:e6:85:ff:fa:7d |
| **معرف مفتاح المرجع** | keyid:e5:9d:59:30:82:47:58:cc:ac:fa:08:54:36:86:7b:3a:b5:04:4d:f0 |
| **الطباعة المصغرة (SHA-1)** | 417E225037FBFAA4F95761D5AE729E1AEA7E3A42 |
| **الطباعة المصغرة (SHA-256)** | 4FF404F02E2CD00188F15D1C00F4B6D1E38B5A395CF85314EAEBA855B6A64B75 |
| **تثبيت (SHA-256)** | xjXxgkOYlag7jCtR5DreZm9b61iaIhd+J3+b2LiybIw= |
| **عناوين URL CRL** | http://crl3.digicert.com/Omniroot2025.crl |
| **عناوين URL ل OCSP** | http://ocsp.digicert.com |

### <a name="microsoft-it-tls-ca-2"></a>**Microsoft IT TLS CA 2**

| **الموضوع** | CN=Microsoft IT TLS CA 2<br>OU=Microsoft IT<br>O=Microsoft Corporation<br>L=Redmond<br>S=Washington<br>C=US |
| --- | --- |
| **مصدر** | CN=Baltimore CyberTrust Root<br>OU=CyberTrust<br>O=Baltimore<br>C=IE |
| **الرقم التسلسلي** | 0F:2C:10:C9:5B:06:C0:93:7F:B8:D4:49:F8:3E:85:69 |
| **طول المفتاح العمومي** | RSA 4096 بت (e 65537) |
| **خوارزمية التوقيع** | sha256RSA |
| **الصلاحية ليس قبل** | 20 مايو 12:51:57 2016 UTC |
| **الصلاحية ليس بعد** | 20 مايو 12:51:57 2024 UTC |
| **معرف مفتاح الموضوع** | 91:9e:3b:44:6c:3d:57:9c:42:77:2a:34:d7:4f:d1:cc:4a:97:2c:da |
| **معرف مفتاح المرجع** | keyid:e5:9d:59:30:82:47:58:cc:ac:fa:08:54:36:86:7b:3a:b5:04:4d:f0 |
| **الطباعة المصغرة (SHA-1)** | 54D9D20239080C32316ED9FF980A48988F4ADF2D |
| **الطباعة المصغرة (SHA-256)** | 4E107C981B42ACBE41C01067E16D44DB64814D4193E572317EA04B87C79C475F |
| **تثبيت (SHA-256)** | wBdPad95AU7OgLRs0FU/E6ILO1MSCM84kJ9y0H+TT7s= |
| **عناوين URL CRL** | http://crl3.digicert.com/Omniroot2025.crl |
| **عناوين URL ل OCSP** | http://ocsp.digicert.com |

### <a name="microsoft-it-tls-ca-4"></a>**Microsoft IT TLS CA 4**

| **الموضوع** | CN=Microsoft IT TLS CA 4<br>OU=Microsoft IT<br>O=Microsoft Corporation<br>L=Redmond<br>S=Washington<br>C=US |
| --- | --- |
| **مصدر** | CN=Baltimore CyberTrust Root<br>OU=CyberTrust<br>O=Baltimore<br>C=IE |
| **الرقم التسلسلي** | 0B:6A:B3:B0:3E:B1:A9:F6:C4:60:92:6A:A8:CD:FE:B3 |
| **طول المفتاح العمومي** | RSA 4096 بت (e 65537) |
| **خوارزمية التوقيع** | sha256RSA |
| **الصلاحية ليس قبل** | 20 مايو 12:52:38 2016 UTC |
| **الصلاحية ليس بعد** | 20 مايو 12:52:38 2024 UTC |
| **معرف مفتاح الموضوع** | 7a:7b:8c:c1:cf:e7:a0:ca:1c:d4:6b:fa:fb:e1:33:c3:0f:1a:a2:9d |
| **معرف مفتاح المرجع** | keyid:e5:9d:59:30:82:47:58:cc:ac:fa:08:54:36:86:7b:3a:b5:04:4d:f0 |
| **الطباعة المصغرة (SHA-1)** | 8A38755D0996823FE8FA3116A277CE446EAC4E99 |
| **الطباعة المصغرة (SHA-256)** | 5FFAC43E0DDC5B4AF2B696F6BC4DB7E91DF314BB8FE0D0713A0B1A7AD2A68FAC |
| **تثبيت (SHA-256)** | wUY9EOTJmS7Aj4fDVCu/KeE++mV7FgIcbn4WhMz1I2k= |
| **عناوين URL CRL** | http://crl3.digicert.com/Omniroot2025.crl |
| **عناوين URL ل OCSP** | http://ocsp.digicert.com |

### <a name="microsoft-it-tls-ca-5"></a>**Microsoft IT TLS CA 5**

| **الموضوع** | CN=Microsoft IT TLS CA 5<br>OU=Microsoft IT<br>O=Microsoft Corporation<br>L=Redmond<br>S=Washington<br>C=US |
| --- | --- |
| **مصدر** | CN=Baltimore CyberTrust Root<br>OU=CyberTrust<br>O=Baltimore<br>C=IE |
| **الرقم التسلسلي** | 08:88:CD:52:5F:19:24:44:4D:14:A5:82:91:DE:B9:52 |
| **طول المفتاح العمومي** | RSA 4096 بت (e 65537) |
| **خوارزمية التوقيع** | sha256RSA |
| **الصلاحية ليس قبل** | 20 مايو 12:53:03 2016 UTC |
| **الصلاحية ليس بعد** | 20 مايو 12:53:03 2024 UTC |
| **معرف مفتاح الموضوع** | 08:fe:25:9f:74:ea:87:04:c2:bc:bb:8e:a8:38:5f:33:c6:d1:6c:65 |
| **معرف مفتاح المرجع** | keyid:e5:9d:59:30:82:47:58:cc:ac:fa:08:54:36:86:7b:3a:b5:04:4d:f0 |
| **الطباعة المصغرة (SHA-1)** | AD898AC73DF333EB60AC1F5FC6C4B2219DDB79B7 |
| **الطباعة المصغرة (SHA-256)** | F0EE5914ED94C7252D058B4E39808AEE6FA8F62CF0974FB7D6D2A9DF16E3A87F |
| **تثبيت (SHA-256)** | RCbqB+W8nwjznTeP4O6VjqcwdxIgI79eBpnBKRr32gc= |
| **عناوين URL CRL** | http://crl3.digicert.com/Omniroot2025.crl |
| **عناوين URL ل OCSP** | http://ocsp.digicert.com |

### <a name="microsoft-rsa-tls-ca-01"></a>**Microsoft RSA TLS CA 01**

| **الموضوع** | CN=Microsoft RSA TLS CA 01<br>O=Microsoft Corporation<br>C=US |
| --- | --- |
| **مصدر** | CN=Baltimore CyberTrust Root، OU=CyberTrust، O=Baltimore، C=IE |
| **الرقم التسلسلي** | 0F:14:96:5F:20:20:69:99:4F:D5:C7:AC:78:89:41:E2 |
| **طول المفتاح العمومي** | RSA 4096 بت |
| **خوارزمية التوقيع** | sha256RSA |
| **الصلاحية ليس قبل** | الثلاثاء، 21 يوليو 2020 4:00 م |
| **الصلاحية ليس حتى** | الثلاثاء، 8 أكتوبر 2024 12:00 صباحا |
| **معرف مفتاح الموضوع** | B5760C3011CEC792424D4CC75C2CC8A90CE80B64 |
| **معرف مفتاح المرجع** | KeyID:e5:9d:59:30:82:47:58:cc:ac:fa:08:54:36:86:7b:3a:b5:04:4d:f0 |
| **الطباعة المصغرة (SHA-1)** | 703D7A8F0EBF55AAA59F98EAF4A206004EB2516A |
| **الطباعة المصغرة (SHA-256)** | 04EEEA8E50B4775B3C24797262917EE50002EC4C75B56CDF3EE1C18CFCA5BA52 |
| **عناوين URL CRL** | http://crl3.digicert.com/Omniroot2025.crl |
| **عناوين URL ل OCSP** | http://ocsp.digicert.com |

### <a name="microsoft-rsa-tls-ca-02"></a>**Microsoft RSA TLS CA 02**

| **الموضوع** | CN=Microsoft RSA TLS CA 02<br>O=Microsoft Corporation<br>C=US |
| --- | --- |
| **مصدر** | CN=Baltimore CyberTrust Root، OU=CyberTrust، O=Baltimore، C=IE |
| **الرقم التسلسلي** | 0F:A7:47:22:C5:3D:88:C8:0F:58:9E:FB:1F:9D:4A:3A |
| **طول المفتاح العمومي** | RSA 4096 بت |
| **خوارزمية التوقيع** | sha256RSA |
| **الصلاحية ليس قبل** | الثلاثاء، 21 يوليو 2020 4:00 م |
| **الصلاحية ليس حتى** | الثلاثاء، 8 أكتوبر 2024 12:00 صباحا |
| **معرف مفتاح الموضوع** | FF2F7FE106F438F32DED258D98C2FE0EF66CFCFA |
| **معرف مفتاح المرجع** | KeyID:e5:9d:59:30:82:47:58:cc:ac:fa:08:54:36:86:7b:3a:b5:04:4d:f0 |
| **الطباعة المصغرة (SHA-1)** | B0C2D2D13CDD56CDAA6AB6E2C04440BE4A429C75 |
| **الطباعة المصغرة (SHA-256)** | 05E4005DB0C382F3BD66B47729E9011577601BF6F7B287E9A52CED710D258346 |
| **عناوين URL CRL** | http://crl3.digicert.com/Omniroot2025.crl |
| **عناوين URL ل OCSP** | http://ocsp.digicert.com |