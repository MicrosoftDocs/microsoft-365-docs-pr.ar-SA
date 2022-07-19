---
title: 'تحسين تدفق البريد باستخدام MTA-STS '
f1.keywords:
- NOCSH
ms.author: v-bshilpa
author: Benny-54
manager: serdars
audience: Admin
ms.topic: overview
ms.service: O365-seccomp
ms.localizationpriority: high
ms.assetid: ''
ms.collection:
- M365-security-compliance
- m365solution-mip
- m365initiative-compliance
description: تعرف على كيفية تحسين تدفق البريد باستخدام MTA-STS.
ms.openlocfilehash: 735cce96c61a2083b8f0785ace49a5b199790989
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/14/2022
ms.locfileid: "66857293"
---
# <a name="enhancing-mail-flow-with-mta-sts"></a>تحسين تدفق البريد باستخدام MTA-STS

تتم إضافة دعم معيار [SMTP MTA Strict Transport Security](https://datatracker.ietf.org/doc/html/rfc8461) (MTA-STS) إلى Exchange Online. تم تطوير المعيار لضمان استخدام TLS دائما للاتصالات بين خوادم البريد الإلكتروني. كما يوفر طريقة لإرسال الخوادم للتحقق من أن الخادم المتلقي لديه شهادة موثوق بها. إذا لم يتم عرض TLS أو لم تكن الشهادة صالحة، يرفض المرسل تسليم الرسائل. تعمل عمليات الفحص الجديدة هذه على تحسين الأمان العام ل SMTP والحماية من هجمات الإنسان في الوسط.

يمكن تقسيم MTA-STS إلى سيناريوهين: الحماية الواردة والصادرة. تغطي الواردة حماية المجالات المستضافة في Exchange Online مع MTA-STS والصادرة عمليات التحقق من صحة MTA-STS التي يتم إجراؤها بواسطة Exchange Online عند إرسال رسائل البريد الإلكتروني إلى المجالات المحمية ب MTA-STS.

## <a name="outbound-protection"></a>الحماية الصادرة

يتم التحقق من صحة جميع الرسائل المرسلة الصادرة من Exchange Online إلى مستلمي MTA-STS المحميين مع عمليات التحقق من الأمان الإضافية هذه التي تم تعيينها بواسطة معيار MTA-STS. لا يوجد شيء يحتاج المسؤولون إلى القيام به لتطبيقه. تحترم عملية التنفيذ الصادرة رغبات مالكي مجال المستلمين عبر نهج MTA-STS الخاص بهم. تشكل MTA-STS جزءا من البنية الأساسية للأمان Exchange Online، وبالتالي فهي تعمل دائما (مثل ميزات SMTP الأساسية الأخرى).

## <a name="inbound-protection"></a>الحماية الواردة

يمكن لمالكي المجالات اتخاذ إجراء لحماية رسائل البريد الإلكتروني المرسلة إلى مجالاتهم باستخدام MTA-STS، إذا كان سجل MX يشير إلى Exchange Online. إذا كان سجل MX يشير إلى خدمة وسيطة تابعة لجهة خارجية، فستحتاج إلى التحقق من استيفاء متطلبات MTA-STS من قبلهم واتباع تعليماتهم.

بمجرد إعداد MTA-STS لمجالك، ستقوم أي رسائل مرسلة من المرسلين الذين يدعمون MTA-STS بإجراء عمليات التحقق التي تم وضعها بواسطة المعيار لضمان اتصال آمن. إذا كنت تتلقى رسالة بريد إلكتروني من مرسل لا يدعم MTA-STS، فسيستمر تسليم البريد الإلكتروني دون حماية إضافية. وبالمثل، لا يوجد تعطيل للرسائل إذا كنت لا تستخدم MTA-STS حتى الآن ولكن المرسل يدعم ذلك. السيناريو الوحيد الذي لا يتم فيه تسليم الرسائل هو عندما يستخدم كلا الجانبين التحقق من صحة MTA-STS وMTA-STS.

## <a name="how-to-adopt-mta-sts"></a>كيفية اعتماد MTA-STS

يسمح MTA-STS لمجال بالإعلان عن دعم TLS وإبلاغ سجل MX وشهادة الوجهة التي يجب توقعها. كما يشير إلى ما يجب أن يفعله خادم الإرسال إذا كانت هناك مشكلة. يتم ذلك من خلال مزيج من سجل DNS TXT وملف نهج يتم نشره كصفحة ويب HTTPS. يقدم النهج المحمي ب HTTPS حماية أمنية أخرى يجب على المهاجمين التغلب عليها.

يشير سجل MTA-STS TXT للمجال إلى دعم MTA-STS للمرسل، وبعد ذلك يتم استرداد نهج MTA-STS المستند إلى HTTPS للمجال من قبل المرسل. سجل TXT التالي هو مثال يعلن عن دعم MTA-STS:

`_mta-sts.contoso.com. 3600 IN TXT v=STSv1; id=20220101000000Z;`

يجب أن يكون نهج MTA-STS الخاص بالمجال موجودا في عنوان URL معرف مسبقا تتم استضافته بواسطة البنية الأساسية للويب للمجال. بناء جملة URL هو `https://mta-sts.<domain name>/.well-known/mta-sts.txt`. على سبيل المثال، تم العثور على نهج Microsoft.com في: <https://mta-sts.microsoft.com/.well-known/mta-sts.txt>.

```text
version: STSv1
mode: enforce
mx: *.mail.protection.outlook.com
max_age: 604800
```

يمكن لأي عميل تشير سجلات MX الخاصة به مباشرة إلى Exchange Online تحديده في نهجه الخاص، بنفس القيم الموضحة أعلاه في نهج microsoft.com. المعلومات الفريدة المطلوبة في النهج هي سجل MX الذي يشير إلى Exchange Online (`*`.mail.protection.outlook.com)، ويتم مشاركة الشهادة نفسها من قبل جميع العملاء Exchange Online. من الممكن نشر النهج الخاص بك في وضع *الاختبار* للتأكد من أنه صالح قبل تغييره *لفرض الوضع* . هناك أدوات تحقق من الصحة تابعة لجهة خارجية يمكنها التحقق من التكوين الخاص بك.

هذه النهج ليست شيئا يمكن Exchange Online استضافته نيابة عن العملاء ويجب على العملاء الاستفادة من خدمة استضافة الويب التي يستخدمونها. يجب حماية النهج بواسطة HTTPS مع شهادة للملحق `mta-sts.<domain name>`الفرعي. هناك بدائل لاستضافة نهج بما في ذلك [هذا الحل](https://github.com/jpawlowski/mta-sts.template) الذي يستخدم GitHub Pages لاستضافة ذلك.

بمجرد إنشاء سجل مجال DNS TXT وإتاحة ملف النهج في عنوان URL HTTPS المطلوب، ستتم حماية المجال بواسطة MTA-STS. تتوفر تفاصيل حول MTA-STS في [RFC 8461](https://datatracker.ietf.org/doc/html/rfc8461).
