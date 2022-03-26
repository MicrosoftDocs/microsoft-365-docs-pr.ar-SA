---
title: التطبيقات المتصلة في Microsoft Defender لنقطة النهاية
ms.reviewer: ''
description: عرض تطبيقات الشركاء المتصلة التي تستخدم بروتوكول OAuth 2.0 القياسي لمصادقة الرموز المميزة وتوفيرها لاستخدامها مع Microsoft Defender ل واجهات برمجة تطبيقات نقطة النهاية.
keywords: الشركاء، التطبيقات،  الأطراف الخارجية، الاتصالات، sentinelone، lookout، bitdefender، corrata، morphisec، paloalto، ziften، هاتف محمول أفضل
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
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 4dd630dd2b35c2fedc0340cd873ff065b2685b41
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/03/2021
ms.locfileid: "63570631"
---
# <a name="connected-applications-in-microsoft-defender-for-endpoint"></a>التطبيقات المتصلة في Microsoft Defender لنقطة النهاية

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

تتكامل التطبيقات المتصلة مع النظام الأساسي Defender for Endpoint باستخدام واجهات برمجة التطبيقات.

تستخدم التطبيقات بروتوكول OAuth 2.0 القياسي لمصادقة الرموز المميزة وتوفيرها للاستخدام مع Microsoft Defender ل واجهات برمجة تطبيقات نقطة النهاية. بالإضافة إلى ذلك، تسمح تطبيقات Azure Active Directory (Azure AD) لمسؤولي المستأجرين بتعيين التحكم الصريح في واجهات برمجة التطبيقات التي يمكن الوصول إليها باستخدام التطبيق المقابل.

ستحتاج إلى اتباع هذه [الخطوات](/microsoft-365/security/defender-endpoint/apis-intro) لاستخدام واجهات برمجة التطبيقات مع التطبيق المتصل.

من قائمة التنقل اليسرى، حدد **الشركاء & واجهات برمجة التطبيقات** (ضمن نقاط **النهاية) >** **المتصلة**.

## <a name="view-connected-application-details"></a>عرض تفاصيل التطبيق المتصلة

توفر صفحة التطبيقات المتصلة معلومات حول تطبيقات Azure AD المتصلة ب Microsoft Defender لنقطة النهاية في مؤسستك. يمكنك مراجعة استخدام التطبيقات المتصلة: آخر مرة تم عرضها وعدد الطلبات في آخر 24 ساعة وطلب الاتجاهات في آخر 30 يوما.

![صورة للتطبيقات المتصلة.](images/connected-apps.png)
 
## <a name="edit-reconfigure-or-delete-a-connected-application"></a>تحرير تطبيق متصل أو إعادة تكوينه أو حذفه

يفتح **الارتباط فتح إعدادات** التطبيق صفحة إدارة تطبيقات Azure AD المقابلة في مدخل Azure. من مدخل Azure، يمكنك إدارة الأذونات أو إعادة تكوين التطبيقات المتصلة أو حذفها.
