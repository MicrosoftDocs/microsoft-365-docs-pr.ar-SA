---
title: التطبيقات المتصلة في Microsoft Defender لنقطة النهاية
ms.reviewer: ''
description: عرض تطبيقات الشركاء المتصلة التي تستخدم بروتوكول OAuth 2.0 القياسي لمصادقة الرموز المميزة وتوفيرها للاستخدام مع Microsoft Defender لنقطة النهاية برمجة التطبيقات.
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
ms.openlocfilehash: 9e15103f4366d0717af9cec44d516b4b16a7160a
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/25/2022
ms.locfileid: "64475554"
---
# <a name="connected-applications-in-microsoft-defender-for-endpoint"></a>التطبيقات المتصلة في Microsoft Defender لنقطة النهاية

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

تتكامل التطبيقات المتصلة مع النظام الأساسي Defender for Endpoint باستخدام واجهات برمجة التطبيقات.

تستخدم التطبيقات بروتوكول OAuth 2.0 القياسي لمصادقة الرموز المميزة وتوفيرها للاستخدام مع Microsoft Defender لنقطة النهاية برمجة التطبيقات. بالإضافة إلى ذلك، تسمح تطبيقات Azure Active Directory (Azure AD) لمسؤولي المستأجرين بتعيين التحكم الصريح في واجهات برمجة التطبيقات التي يمكن الوصول إليها باستخدام التطبيق المقابل.

ستحتاج إلى اتباع هذه [الخطوات](/microsoft-365/security/defender-endpoint/apis-intro) لاستخدام واجهات برمجة التطبيقات مع التطبيق المتصل.

من قائمة التنقل اليسرى، حدد **الشركاء & واجهات برمجة التطبيقات** (ضمن نقاط **النهاية) >** **المتصلة**.

## <a name="view-connected-application-details"></a>عرض تفاصيل التطبيق المتصلة

توفر صفحة التطبيقات المتصلة معلومات حول تطبيقات Azure AD المتصلة Microsoft Defender لنقطة النهاية في مؤسستك. يمكنك مراجعة استخدام التطبيقات المتصلة: آخر مرة تم عرضها وعدد الطلبات في آخر 24 ساعة وطلب الاتجاهات في آخر 30 يوما.

:::image type="content" source="images/connected-apps.png" alt-text="التطبيقات المتصلة" lightbox="images/connected-apps.png":::
 
## <a name="edit-reconfigure-or-delete-a-connected-application"></a>تحرير تطبيق متصل أو إعادة تكوينه أو حذفه

يفتح **الارتباط فتح إعدادات** التطبيق صفحة إدارة تطبيقات Azure AD المقابلة في مدخل Azure. من مدخل Azure، يمكنك إدارة الأذونات أو إعادة تكوين التطبيقات المتصلة أو حذفها.
