---
title: إدارة تجربة الانضمام لمواعيد Teams الظاهرية على المستعرضات
author: lanachin
ms.author: v-lanachin
manager: samanro
audience: ITPro
ms.topic: article
ms.service: microsoft-365-frontline
search.appverid: ''
searchScope:
- Microsoft Teams
- Microsoft Cloud for Healthcare
- Microsoft Cloud for Retail
f1.keywords:
- NOCSH
ms.localizationpriority: high
ms.collection:
- microsoftcloud-healthcare
- microsoftcloud-retail
- m365solution-healthcare
- m365solution-scenario
- m365-frontline
ms.reviewer: hafarmer
description: تعرف على تجربة الانضمام لمواعيد Teams الظاهرية على المستعرضات.
appliesto:
- Microsoft Teams
- Microsoft 365 for frontline workers
ms.openlocfilehash: 869e554ed202f5e2ef24cf75e3dc2338c65de554
ms.sourcegitcommit: 5e5c2c1f7c321b5eb1c5b932c03bdd510005de13
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/15/2022
ms.locfileid: "66823676"
---
# <a name="manage-the-join-experience-for-teams-virtual-appointments-on-browsers"></a>إدارة تجربة الانضمام لمواعيد Teams الظاهرية على المستعرضات

يسهل Microsoft Teams على الأشخاص الانضمام إلى المواعيد الظاهرية دون الحاجة إلى تنزيل Teams. للحصول على تجربة أكثر سلاسة، يمكن للحضور الانضمام إلى مواعيد مثل زيارات الرعاية الصحية والاستشارات المالية من سطح المكتب أو متصفح الهاتف المحمول. لا يحتاج الحضور إلى تثبيت تطبيق Teams على أجهزتهم.

باستخدام الانضمام إلى المستعرض، عندما ينضم أحد الحضور إلى موعد، لا تتم مطالبته بتنزيل Teams. بدلا من ذلك، يفتح Teams في مستعرض، حيث يمكن للحضور تحديد **الانضمام الآن** للانضمام. باستخدام هذه الميزة، ضع في اعتبارك أنه إذا كان Teams مثبتا بالفعل على الجهاز، فسيتم فتح Teams في مستعرض وليس في التطبيق.

تتوفر حاليا الانضمام إلى المستعرض للمواعيد المجدولة من خلال ما يلي:

- [تطبيق Bookings](https://support.microsoft.com/office/what-is-bookings-42d4e852-8e99-4d8f-9b70-d7fc93973cb5)
- موصل Microsoft Teams Electronic Health Record (EHR)

  - التكامل مع [Cerner EHR](ehr-admin-cerner.md)
  - التكامل مع [Epic EHR](ehr-admin-epic.md)

## <a name="set-up-browser-join"></a>إعداد الانضمام إلى المستعرض

### <a name="appointments-scheduled-through-the-bookings-app"></a>المواعيد المجدولة من خلال تطبيق Bookings

يمكن للمجدولين في مؤسستك تشغيل هذه الميزة لأنواع مواعيد معينة وللمواعيد الفردية في تطبيق Bookings.

بعد تشغيل هذه الميزة، سيحتوي البريد الإلكتروني للتأكيد أو نص SMS المرسل إلى الحضور على ارتباط الانضمام إلى الاجتماع الذي يفتح Teams في مستعرض سطح المكتب أو الجوال. للحصول على قائمة المستعرضات المدعومة، راجع [المستعرضات المعتمدة](#supported-browsers).

#### <a name="turn-on-browser-join-for-an-appointment-type"></a>تشغيل الانضمام إلى المستعرض لنوع موعد

في Bookings، انتقل إلى **أنواع** **"إعدادات المواعيد** > "، وحدد [نوع موعد](https://support.microsoft.com/office/create-an-appointment-type-810eac77-6a65-4dc8-964d-c00eadf43887)، ثم قم بتشغيل **"السماح للحضور بالانضمام من مستعرض**". يؤدي القيام بذلك إلى تمكين الانضمام إلى المستعرض لكافة المواعيد من هذا النوع.

:::image type="content" source="media/browser-join-bookings-appointment-type.png" alt-text="لقطة شاشة للسماح للحضور بالانضمام من إعداد مستعرض لأنواع المواعيد في تطبيق Bookings":::

#### <a name="turn-on-browser-join-for-an-individual-appointment"></a>تشغيل الانضمام إلى المستعرض لموعد فردي

في Bookings، حدد **"حجز جديد**"، ثم قم بتشغيل **"السماح للحضور بالانضمام من مستعرض**".

:::image type="content" source="media/browser-join-bookings-form.png" alt-text="لقطة شاشة للسماح للحضور بالانضمام من إعداد مستعرض على نموذج الحجز الجديد في تطبيق Bookings":::

### <a name="appointments-scheduled-through-the-teams-ehr-connector"></a>المواعيد المجدولة من خلال موصل Teams EHR

لا تحتاج أنت أو فريق عملك إلى أي إعداد!

**التكامل مع Cerner EHR**: يدعم موصل Teams EHR المرضى الذين ينضمون إلى المواعيد الظاهرية من خلال ارتباط في الرسالة النصية SMS. في وقت الموعد، يمكن للمرضى الانضمام من خلال الضغط على الارتباط في الرسالة النصية SMS، ويفتح Teams في مستعرض.

**التكامل مع Epic EHR**: يدعم موصل Teams EHR المرضى الذين ينضمون إلى المواعيد الظاهرية من خلال MyChart على الويب والأجهزة المحمولة. في وقت الموعد، يمكن للمرضى بدء الموعد من MyChart باستخدام الزر **"بدء زيارة افتراضية** "، ويفتح Teams في مستعرض.

## <a name="supported-browsers"></a>المستعرضات المدعومة

فيما يلي المستعرضات المدعومة حاليا. نحن ندعم الإصدار الأخير بالإضافة إلى إصدارين سابقين، ما لم تتم الإشارة إلى خلاف ذلك.

|منصه  |كروم |سفاري |Edge (Chromium)|
|---------|:---|:---|:---:|
|الروبوت   | &#x2714; &sup1;      |         |         |
|دائره الرقابه الداخليه    |         | &#x2714; &sup1; &sup2; |         |
|ماك     | &#x2714; | &#x2714;|         |
|بالنسبة لنظام التشغيل    | &#x2714; |   | &#x2714; |
|Ubuntu/Linux     | &#x2714;         |     |         |

&sup1; لا يتم دعم مشاركة الشاشة الصادرة على iOS أو Android.

&sup2; لا يمكن لتطبيقات iOS على Safari تحديد أجهزة الميكروفون والسماعات. على سبيل المثال، أجهزة Bluetooth. هذا تقييد لنظام التشغيل، الذي يتحكم في تحديد الجهاز الافتراضي.

## <a name="things-to-consider"></a>الأمور الواجب وضعها في الاعتبار

يمكن لعضو فريق العمل الذي يقوم بالموعد مشاركة الشاشة الخاصة به من عميل Teams لسطح المكتب أو الجوال أو الويب مع أحد الحضور الذي ينضم من سطح المكتب أو مستعرض الجوال. ومع ذلك، لا يمكن للحضور مشاركة الشاشة الخاصة بهم من مستعرض سطح المكتب أو الجوال.

## <a name="related-articles"></a>المقالات ذات الصلة

- [المواعيد الظاهرية مع Teams وتطبيق Bookings](bookings-virtual-visits.md)
- [إنشاء نوع موعد Bookings](https://support.microsoft.com/office/create-an-appointment-type-810eac77-6a65-4dc8-964d-c00eadf43887)
- [الانضمام إلى موعد Bookings كأحد الحضور](https://support.microsoft.com/office/join-a-bookings-appointment-as-an-attendee-95cea12d-2220-421f-a663-6efb20913c7f)
- [المواعيد الظاهرية مع Teams - التكامل في Cerner EHR](ehr-admin-cerner.md)
- [المواعيد الظاهرية مع Teams - التكامل في Epic EHR](ehr-admin-epic.md)
