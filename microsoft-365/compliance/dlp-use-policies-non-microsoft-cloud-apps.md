---
title: استخدام نهج DLP لتطبيقات السحابة غير الخاصة ب Microsoft
f1.keywords:
- CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: article
f1_keywords:
- ms.o365.cc.DLPLandingPage
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MET150
ms.custom:
- seo-marvel-apr2020
description: تعرف على كيفية استخدام نهج dlp لتطبيقات السحابة غير الخاصة ب Microsoft.
ms.openlocfilehash: a50849b53819a7c5872c3ec8cb279ffa8d14e27f
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/06/2022
ms.locfileid: "66634369"
---
# <a name="use-data-loss-prevention-policies-for-non-microsoft-cloud-apps"></a>استخدام نهج منع فقدان البيانات لتطبيقات السحابة غير التابعة ل Microsoft

يمكنك تحديد نهج DLP Microsoft Defender for Cloud Apps لمراقبة العناصر الحساسة ومشاركتها عبر تطبيقات السحابة غير التابعة ل Microsoft واكتشافها واتخاذ إجراءات بشأنها.

## <a name="before-you-begin"></a>قبل البدء

### <a name="skusubscriptions-licensing"></a>ترخيص SKU/الاشتراكات

قبل البدء في استخدام نهج DLP، تأكد من [اشتراكك في Microsoft 365](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=1) وأي وظائف إضافية. للوصول إلى هذه الوظيفة واستخدامها، يجب أن يكون لديك أحد هذه الاشتراكات أو الوظائف الإضافية:

- Microsoft 365 E5
- التوافق في Microsoft 365 E5
- الأمان في Microsoft 365 E5

### <a name="permissions"></a>الأذونات
يجب أن يكون المستخدم الذي يقوم بإنشاء نهج DLP:

- المسؤول العام
- مسؤول التوافق: التعيين في Azure AD
- مسؤول بيانات التوافق: التعيين في Azure AD

### <a name="prepare-your-defender-for-cloud-apps-environment"></a>إعداد بيئة Defender for Cloud Apps

قبل تكوين نهج DLP التي تم تحديد نطاقها إلى Microsoft Defender for Cloud Apps، يجب إعداد Defender لبيئة تطبيقات السحابة. للحصول على الإرشادات، راجع [التشغيل السريع: بدء استخدام Microsoft Defender for Cloud Apps](/defender-cloud-apps/get-started).

### <a name="connect-a-non-microsoft-cloud-app"></a>توصيل تطبيق سحابي غير خاص ب Microsoft

لاستخدام نهج DLP الذي تم تحديد نطاقه إلى تطبيق سحابي معين غير Microsoft، يجب أن يكون التطبيق متصلا ب Defender for Cloud Apps. للحصول على معلومات، راجع:

- [مربع الاتصال](/defender-cloud-apps/connect-box)
- [توصيل Dropbox](/defender-cloud-apps/connect-dropbox)
- [الاتصال بمساحة عمل Google](/defender-cloud-apps/connect-google-workspace)
- [الاتصال ب Salesforce](/defender-cloud-apps/connect-salesforce)
- [الاتصال ب Cisco Webex](/defender-cloud-apps/connect-webex)

بعد توصيل تطبيقات السحابة ب Defender for Cloud Apps، يمكنك إنشاء نهج DLP لها.

## <a name="create-a-dlp-policy-scoped-to-a-non-microsoft-cloud-app"></a>إنشاء نهج DLP محدد النطاق لتطبيق سحابة غير Microsoft

راجع [إنشاء نهج DLP واختباره وضبطه](create-test-tune-dlp-policy.md) للإجراءات لإنشاء نهج DLP. ضع هذه النقاط في الاعتبار أثناء تكوين نهجك.

- حدد تشغيل موقع **Microsoft Defender for Cloud Apps**.
- لتحديد تطبيق أو مثيل معين، حدد **"اختيار مثيل**". إذا لم تحدد مثيلا، فسيتم تحديد نطاق النهج لجميع التطبيقات المتصلة في مستأجر Microsoft Defender for Cloud Apps.
- يمكنك التحديد من بين عدد من **الإجراءات** لفرضها على تطبيقات الجهات الخارجية. لتقييد تطبيقات الجهات الخارجية، حدد **"تقييد تطبيقات الجهات الخارجية** " ثم حدد الإجراءات المحددة.

![قائمة بالإجراءات التي يجب فرضها على تطبيقات السحابة المتصلة](../media/dlp-non-microsoft-cloud-app-restrict-third-party-apps.png)

> [!NOTE]
> عند إنشاء نهج DLP الذي تم تحديد نطاقه إلى Microsoft Defender for Cloud Apps، سيتم إنشاء النهج نفسه تلقائيا في Microsoft Defender for Cloud Apps.

## <a name="see-also"></a>انظر أيضاً

- [إنشاء اختبار وضبط نهج DLP](./create-test-tune-dlp-policy.md)
- [بدء استخدام نهج DLP الافتراضي](./get-started-with-the-default-dlp-policy.md)
- [إنشاء نهج DLP من قالب](./create-a-dlp-policy-from-a-template.md)
