---
title: تكامل Microsoft Defender لنقطة النهاية مع حلول Microsoft الأخرى
description: تعرف على كيفية تكامل Microsoft Defender لنقطة النهاية مع حلول Microsoft الأخرى، بما في ذلك Microsoft Defender for Identity وMicrosoft Defender for Cloud.
author: mjcaparas
ms.author: macapara
ms.prod: m365-security
keywords: microsoft 365 Defender، والوصول المشروط، وoffice، Microsoft Defender لنقطة النهاية، وmicrosoft Defender للهوية، وmicrosoft Defender ل office، وMicrosoft Defender for Cloud، وأمان تطبيق microsoft السحابي، وazure sentinel
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 24244fa9b0cbb9ed452c8b09b6a108055ac6f770
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/29/2022
ms.locfileid: "66489393"
---
# <a name="microsoft-defender-for-endpoint-and-other-microsoft-solutions"></a>Microsoft Defender لنقطة النهاية وحلول Microsoft الأخرى

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:**
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

## <a name="integrate-with-other-microsoft-solutions"></a>التكامل مع حلول Microsoft الأخرى

Microsoft Defender لنقطة النهاية يتكامل مباشرة مع حلول Microsoft المختلفة.

### <a name="microsoft-defender-for-cloud"></a>Microsoft Defender للسحابة

يوفر Microsoft Defender لنقطة النهاية حلا شاملا لحماية الخادم، بما في ذلك قدرات الكشف عن نقاط النهاية والاستجابة لها (EDR) على خوادم Windows.

### <a name="microsoft-sentinel"></a>Microsoft Sentinel

يتيح لك موصل Microsoft Defender لنقطة النهاية دفق التنبيهات من Microsoft Defender لنقطة النهاية إلى Microsoft Sentinel. سيمكنك هذا من تحليل أحداث الأمان بشكل أكثر شمولا عبر مؤسستك وإنشاء أدلة مبادئ للاستجابة الفعالة والفورية.

### <a name="azure-information-protection"></a>Azure حماية البيانات

لقد تجاوزنا مؤخرا تكامل azure حماية البيانات حيث تتضمن قدرات DLP لنقطة النهاية حلا محسنا للاكتشاف والحماية للبيانات الحساسة المخزنة على أجهزة نقطة النهاية التي تسهل رؤية وتكاملا أكبر بين الحلول. تم الإعلان عن ذلك في [المدونة](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/protecting-sensitive-information-on-devices/ba-p/2143555) التالية. نوصي العملاء بالانتقال إلى استخدام DLP لنقطة النهاية.

### <a name="conditional-access"></a>الوصول المشروط

يتم دمج درجة مخاطر الجهاز الديناميكية Microsoft Defender لنقطة النهاية في تقييم الوصول المشروط، ما يضمن أن الأجهزة الآمنة فقط لديها حق الوصول إلى الموارد.

### <a name="microsoft-defender-for-cloud-apps"></a>Microsoft Defender for Cloud Apps

Microsoft Defender for Cloud Apps الاستفادة من إشارات Microsoft Defender لنقطة النهاية للسماح بالرؤية المباشرة في استخدام تطبيق السحابة بما في ذلك استخدام خدمات السحابة غير المدعومة (Shadow IT) من الجميع Microsoft Defender لنقطة النهاية الأجهزة المراقبة.

### <a name="microsoft-defender-for-identity"></a>Microsoft Defender للهوية

الأنشطة المشبوهة هي عمليات تعمل ضمن سياق المستخدم. يوفر التكامل بين Microsoft Defender لنقطة النهاية Microsoft Defender for Identity مرونة إجراء تحقيق الأمان السيبراني عبر الأنشطة والهويات.

### <a name="microsoft-defender-for-office"></a>Microsoft Defender ل Office

يساعد [Defender لـ Office 365](/office365/securitycompliance/office-365-atp) على حماية مؤسستك من البرامج الضارة في رسائل البريد الإلكتروني أو الملفات من خلال الارتباطات الآمنة والمرفقات الآمنة ومكافحة التصيد الاحتيالي المتقدمة وقدرات التحليل الذكي للانتحال. يتيح التكامل بين Microsoft Defender لـ Office 365 Microsoft Defender لنقطة النهاية للمحللين الأمنيين الانتقال إلى المصدر للتحقيق في نقطة الدخول للهجوم. من خلال مشاركة التحليل الذكي للمخاطر، يمكن احتواء الهجمات وحظرها.

> [!NOTE]
> يتم عرض بيانات Defender لـ Office 365 للأحداث خلال آخر 30 يوما. بالنسبة للتنبيهات، يتم عرض بيانات Defender لـ Office 365 استنادا إلى وقت النشاط الأول. بعد ذلك، لم تعد البيانات متوفرة في Defender لـ Office 365.

### <a name="skype-for-business"></a>Skype for Business

يوفر تكامل Skype for Business طريقة للمحللين للتواصل مع مستخدم أو مالك جهاز يحتمل أن يكون معرضا للخطر من خلال زر بسيط من المدخل.

## <a name="microsoft-365-defender"></a>Microsoft 365 Defender

مع Microsoft 365 Defender، Microsoft Defender لنقطة النهاية، ومختلف حلول أمان Microsoft تشكل مجموعة دفاع موحدة لما قبل الخرق وما بعده تتكامل أصلا عبر نقطة النهاية والهوية والبريد الإلكتروني والتطبيقات للكشف عن الهجمات المتطورة ومنعها والتحقيق فيها والاستجابة لها تلقائيا.

[تعرف على المزيد حول Microsoft 365 Defender](/microsoft-365/security/defender/microsoft-365-defender)

## <a name="related-topics"></a>المواضيع ذات الصلة

- [تكوين التكامل والميزات المتقدمة الأخرى](advanced-features.md)
- [نظرة عامة على Microsoft 365 Defender](/microsoft-365/security/defender/microsoft-365-defender)
- [تمكين Microsoft 365 Defender](/microsoft-365/security/defender/m365d-enable)
- [حماية المستخدمين والبيانات والأجهزة باستخدام الوصول المشروط](conditional-access.md)
