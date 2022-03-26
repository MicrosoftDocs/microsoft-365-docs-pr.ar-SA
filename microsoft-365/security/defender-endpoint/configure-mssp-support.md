---
title: تكوين دعم موفر خدمة الأمان المدار
description: اتخاذ الخطوات اللازمة لتكوين تكامل MSSP مع Microsoft Defender لنقطة النهاية
keywords: موفر خدمة الأمان المدار، mssp، تكوين، تكامل
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 1a9a7e24bc08338549a78fcf9e9b2756701cd83f
ms.sourcegitcommit: dd6514ae173f1c821d4ec25298145df6cb232e2e
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 01/19/2022
ms.locfileid: "63573339"
---
# <a name="configure-managed-security-service-provider-integration"></a>تكوين تكامل موفر خدمة الأمان المدار

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-mssp-support-abovefoldlink)

[!include[Prerelease information](../../includes/prerelease.md)]

ستحتاج إلى اتخاذ خطوات التكوين التالية لتمكين تكامل موفر خدمة الأمان المدار (MSSP).

> [!NOTE]
> تستخدم المصطلحات التالية في هذه المقالة للتمييز بين موفر الخدمة ومستهلك الخدمة:
>
> - MSSPs: مؤسسات الأمان التي تعرض مراقبة أجهزة الأمان وإدارتها في مؤسسة.
> - عملاء MSSP: المؤسسات التي تشرك خدمات MSSPs.

سيتيح التكامل ل MSSPs اتخاذ الإجراءات التالية:

- الوصول إلى مدخل عميل MSSP Microsoft 365 Defender
- الحصول على إعلامات البريد الإلكتروني، و
- إحضار التنبيهات من خلال أدوات إدارة الأحداث ومعلومات الأمان (SIEM)

قبل أن يستطيع MSSPs اتخاذ هذه الإجراءات، يجب على عميل MSSP منح حق الوصول إلى مستأجر Defender for Endpoint بحيث يمكن ل MSSP الوصول إلى المدخل.

عادة، يتخذ عملاء MSSP خطوات التكوين الأولية لمنح MSSPs حق الوصول إلى Windows Defender Security Central. بعد منح حق الوصول، يمكن القيام بخطوات تكوين أخرى إما بواسطة عميل MSSP أو MSSP.

بشكل عام، يجب اتخاذ خطوات التكوين التالية:

- **منح MSSP حق الوصول إلى Microsoft 365 Defender**

  يجب أن يقوم عميل MSSP بهذا الإجراء. وهو يمنح MSSP حق الوصول إلى مستأجر Defender for Endpoint الخاص ب عميل MSSP.

- **تكوين إعلامات التنبيهات المرسلة إلى MSSPs**

  يمكن اتخاذ هذا الإجراء بواسطة عميل MSSP أو MSSP. يتيح ذلك ل MSSPs معرفة التنبيهات التي يحتاجون إلى معالجتها للعميل MSSP.

- **إحضار تنبيهات من مستأجر عميل MSSP إلى نظام SIEM**

  يتم اتخاذ هذا الإجراء بواسطة MSSP. فهي تسمح ل MSSPs بإحضار التنبيهات في أدوات SIEM.

- **إحضار تنبيهات من مستأجر عميل MSSP باستخدام واجهات برمجة التطبيقات**

  يتم اتخاذ هذا الإجراء بواسطة MSSP. وهو يسمح ل MSSPs بإحضار التنبيهات باستخدام واجهات برمجة التطبيقات.

## <a name="multi-tenant-access-for-mssps"></a>الوصول متعدد المستأجرين ل MSSPs

للحصول على معلومات حول كيفية تنفيذ وصول مفوض متعدد المستأجرين، راجع الوصول متعدد [المستأجرين لموفري خدمات الأمان المدارة](https://techcommunity.microsoft.com/t5/microsoft-defender-atp/multi-tenant-access-for-managed-security-service-providers/ba-p/1533440).

## <a name="related-topics"></a>المواضيع ذات الصلة

- [منح MSSP حق الوصول إلى المدخل](grant-mssp-access.md)
- [الوصول إلى مدخل عميل MSSP](access-mssp-portal.md)
- [تكوين إعلامات التنبيهات](configure-mssp-notifications.md)
- [إحضار التنبيهات من مستأجر العملاء](fetch-alerts-mssp.md)
