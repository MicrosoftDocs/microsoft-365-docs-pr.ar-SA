---
title: إدارة السماح في قائمة السماح/الحظر للمستأجر
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MET150manage-tenant-allows.md
ms.collection:
- M365-security-compliance
description: يمكن للمسؤولين التعرف على كيفية تكوين السماح في قائمة السماح/الحظر للمستأجر في مدخل الأمان.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 3823290e9f239b14e4bf97fe1ae8ef7020561697
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63583374"
---
# <a name="add-allows-in-the-tenant-allowblock-list"></a>السماح بإضافة في قائمة السماح/الحظر للمستأجر

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**ينطبق على**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender Office 365 الخطة 1 الخطة 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

لا يمكن للمسؤولين إضافة السماح مباشرة إلى قائمة السماح/الحظر للمستأجر. بدلا من ذلك، يمكنك استخدام عملية إرسال المسؤول لإرسال الرسالة التي تم حظرها بحيث تضاف عناوين URL والملفات و/أو المرسلين المناظرين إلى قائمة السماح/الحظر للمستأجر. إذا لم يحدث أي كتلة من الملف أو URL أو المرسل، لن يتم إنشاء السماح. في معظم الحالات التي تم فيها تحديد الرسالة على أنها إيجابية خاطئة تم حظرها بشكل غير صحيح، يتم الاحتفاظ ب السماح طالما لزم الأمر لإعطاء وقت النظام للسماح لهم بشكل طبيعي.

> [!IMPORTANT]
> نظرا لأن Microsoft تدير السماح لك أو المرسل أو URL أو الملف الذي لا حاجة إليه أو يعتبر سيئا، سيتم إزالته. وذلك لحماية بيئتك ومنع تكوين السماح بشكل خاطئ. في الحالات التي قد لا توافق فيها على ذلك، قد تكون هناك حاجة إلى حالات دعم للمساعدة في تحديد سبب اعتبار الرسالة سيئة.

## <a name="add-sender-allows-using-the-submissions-portal"></a>إضافة مرسل يسمح باستخدام مدخل الواجبات المرسلة 

السماح للمرسلين (أو المجالات) على صفحة **"الواجبات** المرسلة" في Microsoft 365 Defender. 

1. في Microsoft 365 Defender في <https://security.microsoft.com>، انتقل إلى **إجراءات & الإرسالات**\>. أو، انتقل مباشرة إلى صفحة **"الواجبات** المرسلة"، استخدم <https://security.microsoft.com/reportsubmission>.

2. في صفحة **الواجبات** المرسلة، تحقق من  تحديد علامة التبويب رسائل البريد الإلكتروني، ثم انقر فوق ![إرسال إلى Microsoft لأيقونة التحليل.](../../media/m365-cc-sc-create-icon.png) **إرسال إلى Microsoft للتحليل**.

3. استخدم قائمة **إرسال إلى Microsoft للمراجعة** من خلال إرسال رسالة عن طريق إضافة "معروف رسالة الشبكة" أو تحميل ملف البريد الإلكتروني. 

4. في **المقطع تحديد سبب إرسال إلى Microsoft** ، حدد يجب ألا يكون قد تم **حظره (خطأ موجب)**. 

5. قم تشغيل **السماح بالرسائل مثل هذا** الخيار. 

6. من القائمة **المنسدل إزالة** بعد، حدد المدة التي تريد أن يعمل بها خيار السماح.

7. عند الانتهاء، انقر فوق الزر **إرسال** .

> [!div class="mx-imgBorder"]
> ![إرسال البرامج الضارة إلى Microsoft لتحليلها على سبيل المثال.](../../media/admin-submission-allow-messages.png)

## <a name="add-url-allows-using-the-submissions-portal"></a>تسمح "إضافة عنوان URL" باستخدام مدخل "الواجبات المرسلة"

السماح عناوين URL على صفحة **"** الواجبات المرسلة" في Microsoft 365 Defender.

1. في Microsoft 365 Defender في <https://security.microsoft.com>، انتقل إلى **إجراءات & الإرسالات**\>. أو، انتقل مباشرة إلى صفحة **"الواجبات** المرسلة"، استخدم <https://security.microsoft.com/reportsubmission>.

2. في صفحة **الواجبات** المرسلة، حدد علامة التبويب **عناوين URL** ، ثم انقر فوق ![إرسال إلى Microsoft لأيقونة التحليل.](../../media/m365-cc-sc-create-icon.png) **إرسال إلى Microsoft للتحليل**.

3. استخدم **الأمر إرسال إلى Microsoft للمراجعة** لإرسال رسالة عن طريق إضافة عنوان URL.

4. في **المقطع تحديد سبب إرسال إلى Microsoft** ، حدد يجب ألا يكون قد تم **حظره (خطأ موجب)**.

5. قم تشغيل **السماح عناوين URL بهذا** الخيار.

6. من القائمة **المنسدل** إزالة بعد، حدد المدة التي تريد أن يعمل بها خيار السماح.

7. عند الانتهاء، انقر فوق الزر **إرسال** .

> [!div class="mx-imgBorder"]
> ![إرسال عنوان URL للتحليل.](../../media/submit-url-for-analysis.png)

## <a name="add-file-allows-using-the-submissions-portal"></a>يسمح "إضافة ملف" باستخدام مدخل "الواجبات المرسلة"

السماح للملفات على **صفحة "الواجبات** المرسلة" في Microsoft 365 Defender.

في Microsoft 365 Defender في <https://security.microsoft.com>، انتقل إلى **إجراءات & الإرسالات**\>. أو، انتقل مباشرة إلى صفحة **"الواجبات** المرسلة"، استخدم <https://security.microsoft.com/reportsubmission>.

2. في صفحة **الواجبات** المرسلة، حدد علامة **التبويب مرفقات** البريد الإلكتروني، ثم انقر فوق ![إرسال إلى Microsoft لأيقونة التحليل.](../../media/m365-cc-sc-create-icon.png) **إرسال إلى Microsoft للتحليل**.

3. استخدم **الأمر إرسال إلى Microsoft للمراجعة** لإرسال رسالة عن طريق إضافة الملف أو الملفات.

4. في **المقطع تحديد سبب إرسال إلى Microsoft** ، حدد يجب ألا يكون قد تم **حظره (خطأ موجب)**.

5. قم تشغيل **الخيار السماح لملفات مثل هذا** الخيار.

6. من القائمة **المنسدل** إزالة بعد، حدد المدة التي تريد أن يعمل بها خيار السماح.

7. عند الانتهاء، انقر فوق الزر **إرسال** .

> [!div class="mx-imgBorder"]
> ![إرسال البريد الإلكتروني للتحليل.](../../media/submit-email-for-analysis.png)


## <a name="create-spoofed-sender-allow-entries-using-microsoft-365-defender"></a>إنشاء إدخالات السماح للمرسلين المنتحلين باستخدام Microsoft 365 Defender

> [!NOTE]
> 
> - يتم السماح _فقط_ بالجمع بين المستخدم المهزوف والبنية الأساسية المرسلة كما هو محدد في زوج المجالات أو حظرها من التهزف.
> - عندما تقوم بتكوين إدخال السماح أو الحظر لزوج مجال، لن تظهر الرسائل الواردة من زوج المجال هذا في تحليلات المعلومات المنتحلة.
> - لا تنتهي صلاحية إدخالات المرسلين المزحلين أبدا.
> - يدعم التهزأ كل من السماح والحظر. يدعم URL السماح فقط.

1. في مدخل Microsoft 365 Defender، <https://security.microsoft.com>انتقل إلى البريد **&** \>  \>  \> البريد الإلكتروني ونهج التعاون & قواعد المخاطر لنهج المستأجر السماح **/الحظر القوائم** في **المقطع القواعد**. أو، انتقل مباشرة إلى صفحة **قوائم السماح/** الحظر للمستأجر، استخدم <https://security.microsoft.com/tenantAllowBlockList>.

2. في صفحة **قائمة السماح/** الحظر للمستأجر، **حدد علامة التبويب** انتحال، ثم انقر فوق ![إضافة أيقونة.](../../media/m365-cc-sc-create-icon.png) **إضافة**.

3. في **قائمة إضافة أزواج مجالات** جديدة التي تظهر، قم بتكوين الإعدادات التالية:
   - **إضافة أزواج مجالات جديدة باستخدام أحرف البدل**: أدخل زوج مجال واحد لكل سطر، بحد أقصى 20. للحصول على تفاصيل حول بناء جملة إدخالات المرسلين المنتحلين، راجع [إدارة قائمة السماح/الحظر](tenant-allow-block-list.md) للمستأجر.
   - **انتحال النوع**: حدد إحدى القيم التالية:
     - **داخلي**: يكون المرسل المنتحل في مجال ينتمي إلى مؤسستك ( [مجال مقبول](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains)).
     - **خارجي**: المرسل المهزوف في مجال خارجي.
   - **الإجراء**: حدد **السماح** أو **الحظر**.

4. عند الانتهاء، انقر فوق **إضافة**.

## <a name="add-spoofed-sender-allow-entries-using-powershell"></a>إضافة إدخالات السماح للمرسلين المنتحلين باستخدام PowerShell

لإضافة إدخالات المرسلين المنتحلين في قائمة الحظر/السماح [بالمستأجر في Exchange Online PowerShell](/exchange/connect-to-exchange-online-powershell)، استخدم بناء الجملة التالي:

```powershell
New-TenantAllowBlockListSpoofItems -SpoofedUser <Domain | EmailAddress | *> -SendingInfrastructure <Domain | IPAddress/24> -SpoofType <External | Internal> -Action <Allow | Block>
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمات، راجع [New-TenantAllowBlockListSpoofItems](/powershell/module/exchange/new-tenantallowblocklistspoofitems).

## <a name="related-articles"></a>المقالات ذات الصلة

- [إرسالات المسؤول](admin-submission.md)
- [الإبلاغ عن الإيجابيات الخاطئة والسلبيات الخاطئة](report-false-positives-and-false-negatives.md)
