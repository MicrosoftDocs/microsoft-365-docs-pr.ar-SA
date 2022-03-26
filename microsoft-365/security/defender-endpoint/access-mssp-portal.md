---
title: الوصول إلى مدخل Microsoft 365 Defender MSSP
description: الوصول إلى مدخل Microsoft 365 Defender MSSP
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
ms.openlocfilehash: b1c133048e6600d553f0530e135ebfc2c441dd84
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63570166"
---
# <a name="access-the-microsoft-365-defender-mssp-customer-portal"></a>الوصول إلى مدخل Microsoft 365 Defender MSSP

**ينطبق على:**
- [ خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [ خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-mssp-support-abovefoldlink)

> [!NOTE]
> يتم توجيه مجموعة الخطوات هذه نحو MSSP.

بشكل افتراضي، يمكن لعملاء MSSP الوصول إلى Microsoft 365 Defender المستأجر الخاص بهم من خلال عنوان URL التالي: `https://security.microsoft.com/`.

ومع ذلك، ستحتاج MSSPs إلى استخدام عنوان URL خاص ب المستأجر في التنسيق التالي:  `https://security.microsoft.com?tid=customer_tenant_id` للوصول إلى مدخل عميل MSSP.

بشكل عام، يجب إضافة MSSPs إلى كل واحد من Azure AD الخاص ب عميل MSSP الذي ينوى إدارته.

استخدم الخطوات التالية للحصول على "معر ة مستأجر عميل MSSP" ثم استخدم المستعرض للوصول إلى عنوان URL الخاص ب المستأجر:

1. ك MSSP، سجل دخولك إلى Azure AD باستخدام بيانات الاعتماد الخاصة بك.

2. قم بتبديل الدليل إلى مستأجر عميل MSSP.

3. حدد **Azure Active Directory > خصائص.** ستجد "المعرف المستأجر" في الحقل "المعرف الدليل".

4. يمكنك الوصول إلى مدخل عميل MSSP `customer_tenant_id` عن طريق استبدال القيمة في عنوان URL التالي: `https://security.microsoft.com/?tid=customer_tenant_id`.

## <a name="related-topics"></a>المواضيع ذات الصلة

- [منح MSSP حق الوصول إلى المدخل](grant-mssp-access.md)
- [تكوين إعلامات التنبيهات](configure-mssp-notifications.md)
- [إحضار التنبيهات من مستأجر العملاء](fetch-alerts-mssp.md)
