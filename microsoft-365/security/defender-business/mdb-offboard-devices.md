---
title: إيقاف تشغيل جهاز من Microsoft Defender for Business
description: تعرف على كيفية إزالة جهاز أو إيقاف تشغيله من Microsoft Defender for Business.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: bd6ea78daa1a19d84efc23c34bdb58704484c0d1
ms.sourcegitcommit: fa90763559239c4c46c5e848939126763879d8e4
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/13/2022
ms.locfileid: "66772412"
---
# <a name="offboard-a-device-from-microsoft-defender-for-business"></a>إيقاف تشغيل جهاز من Microsoft Defender for Business

إذا كنت تريد إيقاف تشغيل جهاز، فاستخدم أحد الإجراءات التالية:

- [إيقاف تشغيل جهاز Windows](#offboard-a-windows-device)
- [إيقاف تشغيل جهاز Mac](#offboard-a-mac)

## <a name="offboard-a-windows-device"></a>إيقاف تشغيل جهاز Windows

1. انتقل إلى مدخل Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) وسجل الدخول.

2. في جزء التنقل، اختر **"إعدادات"**، ثم اختر **"نقاط النهاية**".

3. ضمن **إدارة الأجهزة**، اختر **"إيقاف الإلحاق**".

4. حدد نظام تشغيل، مثل **Windows 10 و11**، ثم ضمن **"Offboard a device**"، في قسم **أسلوب النشر**، اختر **البرنامج النصي المحلي**. 

5. في شاشة التأكيد، راجع المعلومات، ثم اختر **"تنزيل"** للمتابعة.

6. حدد **تنزيل حزمة إيقاف الإلحاق**. نوصي بحفظ حزمة الإلحاق إلى محرك أقراص قابل للإزالة.

7. قم بتشغيل البرنامج النصي على كل جهاز تريد إيقاف تشغيله.

## <a name="offboard-a-mac"></a>إيقاف تشغيل جهاز Mac

1. انتقل إلى **تطبيقات** **الباحث** > . 

2. انقر بزر **الماوس** الأيمن فوق Microsoft Defender for Business، ثم اختر **"نقل إلى سلة المهملات**". <br/>--- أو --- <br/> استخدم الأمر التالي: `sudo '/Library/Application Support/Microsoft/Defender/uninstall/uninstall'`.

> [!IMPORTANT]
> يؤدي إلغاء إلحاق جهاز إلى توقف الأجهزة عن إرسال البيانات إلى Defender for Business. ومع ذلك، يتم الاحتفاظ بالبيانات التي تم تلقيها قبل الإلحاق لمدة تصل إلى ستة (6) أشهر.

## <a name="next-steps"></a>الخطوات التالية

- [استخدام لوحة معلومات إدارة الثغرات الأمنية & المخاطر في Microsoft Defender for Business](mdb-view-tvm-dashboard.md)
- [عرض النهج أو تحريرها في Microsoft Defender for Business](mdb-view-edit-create-policies.md)
- [إدارة الأجهزة في Microsoft Defender for Business](mdb-manage-devices.md)