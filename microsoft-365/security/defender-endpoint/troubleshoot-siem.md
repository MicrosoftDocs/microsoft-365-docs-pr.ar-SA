---
title: استكشاف مشاكل تكامل أداة SIEM وإصلاحها في Microsoft Defender لنقطة النهاية
description: استكشاف المشاكل التي قد تنشأ عند استخدام أدوات SIEM مع Microsoft Defender ل Endpoint وإصلاحها.
keywords: استكشاف الأخطاء وإصلاحها، siem، سرية العميل، سرية
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
ms.topic: troubleshooting
ms.technology: mde
ms.openlocfilehash: b6ed0342183734d9b4feb1c20a6c4059b77e64d6
ms.sourcegitcommit: 986ea76ecaceb5fe6b9616e553003e3c5b0df2e7
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 01/25/2022
ms.locfileid: "63570691"
---
# <a name="troubleshoot-siem-tool-integration-issues"></a>استكشاف مشاكل تكامل أداة SIEM وإصلاحها

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-pullalerts-abovefoldlink)

قد تحتاج إلى استكشاف المشاكل وإصلاحها أثناء سحب الاكتشافات في أدوات SIEM.

توفر هذه الصفحة خطوات مفصلة لاستعلام المشاكل التي قد تواجهها وإصلاحها.

## <a name="learn-how-to-get-a-new-client-secret"></a>تعرف على كيفية الحصول على سر عميل جديد

إذا تنتهي صلاحية سرية العميل أو إذا قمت في غير موضع النسخة المتوفرة عند تمكين تطبيق أداة SIEM، فسوف تحتاج إلى الحصول على سر جديد.

1. قم بتسجيل الدخول إلى [مدخل إدارة Azure](https://portal.azure.com).

2. حدد **Microsoft Azure Active Directory**.

3. حدد المستأجر الخاص بك.

4. انقر **فوق تسجيلات التطبيق**. ثم في قائمة التطبيقات، حدد التطبيق.

5. حدد **الشهادات & "** أسرار العميل"، وانقر فوق "سري عميل جديد"، ثم قم بتوفير وصف وحدد مدة الصلاحية.

6. انقر فوق **حفظ**. يتم عرض القيمة الأساسية.

7. انسخ القيمة واحفظها في مكان آمن.

## <a name="error-when-getting-a-refresh-access-token"></a>خطأ عند الحصول على رمز وصول تحديث مميز

إذا واجهت خطأ عند محاولة الحصول على رمز تحديث مميز عند استخدام API لذكاء المخاطر أو أدوات SIEM، ستحتاج إلى إضافة عنوان URL للرد للتطبيق ذي الصلة في Azure Active Directory.

1. قم بتسجيل الدخول إلى [مدخل إدارة Azure](https://ms.portal.azure.com).

2. حدد **Microsoft Azure Active Directory**.

3. حدد المستأجر الخاص بك.

4. انقر **فوق تسجيلات التطبيق**. ثم في قائمة التطبيقات، حدد التطبيق.

5. أضف عنوان URL التالي:
   - بالنسبة إلى الاتحاد الأوروبي: `https://winatpmanagement-eu.securitycenter.windows.com/UserAuthenticationCallback`
   - بالنسبة للمملكة المتحدة: `https://winatpmanagement-uk.securitycenter.windows.com/UserAuthenticationCallback`
   - بالنسبة للولايات المتحدة:  `https://winatpmanagement-us.securitycenter.windows.com/UserAuthenticationCallback`.

6. انقر فوق **حفظ**.

## <a name="error-while-enabling-the-siem-connector-application"></a>خطأ أثناء تمكين تطبيق موصل SIEM

إذا واجهت خطأ عند محاولة تمكين تطبيق موصل SIEM، فتحقق من إعدادات حظر النوافذ المنبثقة في المستعرض. قد يتم حظر النافذة الجديدة التي يتم فتحها عند تمكين الإمكانية.

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-troubleshootsiem-belowfoldlink)

## <a name="related-topics"></a>المواضيع ذات الصلة

- [سحب الاكتشافات إلى أدوات SIEM](configure-siem.md)

