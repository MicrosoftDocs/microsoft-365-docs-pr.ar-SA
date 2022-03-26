---
title: استخدام سياسات منع فقدان البيانات للتطبيقات السحابية غير الخاصة ب Microsoft
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
description: تعرف على كيفية استخدام سياسات dlp للتطبيقات السحابية غير الخاصة ب Microsoft.
ms.openlocfilehash: b374f9b85d41b6dd6a5281e17347dffd414361da
ms.sourcegitcommit: 1ef176c79a0e6dbb51834fe30807409d4e94847c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 11/19/2021
ms.locfileid: "63569463"
---
# <a name="use-data-loss-prevention-policies-for-non-microsoft-cloud-apps"></a>استخدام سياسات منع فقدان البيانات للتطبيقات السحابية غير الخاصة ب Microsoft

إن سياسات منع فقدان البيانات (DLP) للتطبيقات السحابية غير الخاصة ب Microsoft هي جزء من مجموعة ميزات DLP ل Microsoft 365؛ وباستخدام هذه الميزات، يمكنك اكتشاف العناصر الحساسة وحمايتها عبر Microsoft 365 الخدمات. لمزيد من المعلومات حول كل عروض Microsoft DLP، راجع [التعرف على منع فقدان البيانات](dlp-learn-about-dlp.md).

يمكنك استخدام سياسات DLP لتطبيقات السحابة غير الخاصة ب Microsoft لمراقبة العناصر الحساسة والكشف عنها عند استخدامها ومشاركتها عبر تطبيقات السحابة غير الخاصة ب Microsoft. يوفر لك استخدام هذه النهج إمكانية الرؤية والتحكم التي تحتاجها للتأكد من استخدامها وحمايتها بشكل صحيح، كما يساعد على منع السلوك المجازف الذي قد يعرضها للخطر.

## <a name="before-you-begin"></a>قبل البدء

### <a name="skusubscriptions-licensing"></a>ترخيص SKU/الاشتراكات

قبل البدء في استخدام سياسات DLP للتطبيقات السحابية غير الخاصة ب Microsoft، قم [Microsoft 365](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=1) اشتراكك وأي من الوظائف الإضافية. للوصول إلى هذه الوظيفة واستخدامها، يجب أن يكون لديك أحد هذه الاشتراكات أو الوظائف الإضافية:

- Microsoft 365 E5
- التوافق في Microsoft 365 E5
- الأمان في Microsoft 365 E5

### <a name="permissions"></a>الأذونات
يجب أن يكون المستخدم الذي يقوم بإنشاء نهج DLP هو:

- المسؤول العام
- مسؤول التوافق: تعيين في Azure AD
- مسؤول بيانات التوافق: تعيين في Azure AD

### <a name="prepare-your-defender-for-cloud-apps-environment"></a>إعداد بيئة Defender for Cloud Apps

تستخدم سياسات DLP لتطبيقات السحابة غير الخاصة ب Microsoft قدرات Defender for Cloud Apps DLP. لاستخدامه، يجب تحضير بيئة Defender for Cloud Apps. للحصول على الإرشادات، راجع [تعيين إجراءات الرؤية الفورية والحماية والحوكمة لتطبيقاتك](/cloud-app-security/getting-started-with-cloud-app-security#step-1-set-instant-visibility-protection-and-governance-actions-for-your-apps).

### <a name="connect-a-non-microsoft-cloud-app"></a>الاتصال تطبيق سحابة غير Microsoft

لاستخدام نهج DLP لتطبيق سحابة معين غير Microsoft، يجب أن يكون التطبيق متصلا ب Defender for Cloud Apps. للحصول على معلومات، راجع:

- [الاتصال مربع](/cloud-app-security/connect-box-to-microsoft-cloud-app-security)
- [الاتصال Dropbox](/cloud-app-security/connect-dropbox-to-microsoft-cloud-app-security)
- [الاتصال G-Workspace](/cloud-app-security/connect-google-apps-to-microsoft-cloud-app-security)
- [الاتصال Salesforce](/cloud-app-security/connect-salesforce-to-microsoft-cloud-app-security)
- [الاتصال Cisco Webex](/cloud-app-security/connect-webex-to-microsoft-cloud-app-security)

بعد توصيل تطبيقات السحابة ب Defender for Cloud Apps، يمكنك إنشاء Microsoft 365 DLP لها.

> [!NOTE]
> من الممكن أيضا استخدام Microsoft Defender لتطبيقات السحابة لإنشاء سياسات DLP لتطبيقات Microsoft السحابية. ومع ذلك، من المستحسن استخدام Microsoft 365 لإنشاء سياسات DLP وإدارتها لتطبيقات Microsoft السحابية.

## <a name="create-a-dlp-policy-to-a-non-microsoft-cloud-app"></a>إنشاء نهج DLP لتطبيق سحابة غير Microsoft

عندما تحدد موقع نهج DLP، قم تشغيل **موقع Microsoft Defender لتطبيقات السحابة** .

- لتحديد مثيل أو تطبيق معين، حدد **اختيار مثيل**.
- إذا لم تحدد مثيلا، فإن النهج يستخدم جميع التطبيقات المتصلة في مستأجر Microsoft Defender for Cloud Apps.

   ![المواقع لتطبيق النهج.](../media/1-dlp-non-microsoft-cloud-app-choose-instance.png)

   ![Box-US و Box-General.](../media/2-dlp-non-microsoft-cloud-app-box.png)

يمكنك اختيار إجراءات متنوعة لكل تطبيق سحابة غير معتمد من Microsoft. لكل تطبيق، هناك إجراءات محتملة مختلفة (تعتمد على API لتطبيق السحابة).

![إنشاء قاعدة.](../media/3-dlp-non-microsoft-cloud-app-create-rule.png)

عند إنشاء قاعدة في نهج DLP، يمكنك تحديد إجراء لتطبيقات السحابة غير الخاصة ب Microsoft. لتقييد تطبيقات الأطراف الخارجية، حدد **تقييد تطبيقات الأطراف الخارجية**.

![تقييد تطبيقات  الأطراف الخارجية.](../media/4-dlp-non-microsoft-cloud-app-restrict-third-party-apps.png)

> [!NOTE]
> تستخدم سياسات DLP المطبقة على تطبيقات غير Microsoft Microsoft Microsoft Defender for Cloud Apps. عند إنشاء نهج DLP لتطبيق غير Microsoft، سيتم تلقائيا إنشاء النهج نفسه في Microsoft Defender لتطبيقات السحابة.

للحصول على معلومات حول إنشاء نهج DLP وتكوينها، راجع [إنشاء نهج DLP واختباره](./create-test-tune-dlp-policy.md).

## <a name="see-also"></a>انظر أيضاً

- [إنشاء نهج DLP واختباره](./create-test-tune-dlp-policy.md)
- [بدء استخدام نهج DLP الافتراضي](./get-started-with-the-default-dlp-policy.md)
- [إنشاء نهج DLP من قالب](./create-a-dlp-policy-from-a-template.md)
