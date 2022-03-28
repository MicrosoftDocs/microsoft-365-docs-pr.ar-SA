---
title: تكوين استثناءات Microsoft Defender لنقطة النهاية على Mac والتحقق من صحتها
description: توفير استثناءات ل Microsoft Defender لنقطة النهاية على Mac والتحقق من صحتها. يمكن تعيين الاستثناءات للملفات والمجلدات والعمليات.
keywords: microsoft، defender، Microsoft Defender ل Endpoint، mac، الاستثناءات، المسح الضوئي، برنامج الحماية من الفيروسات
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: a069e3dd3ef99f094f96318277e077c56b7cb974
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/12/2022
ms.locfileid: "63575749"
---
# <a name="configure-and-validate-exclusions-for-microsoft-defender-for-endpoint-on-macos"></a>تكوين استثناءات Microsoft Defender ل Endpoint والتحقق من صحتها على macOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

توفر هذه المقالة معلومات حول كيفية تعريف الاستثناءات التي تنطبق على عمليات الفحص عند الطلب، والحماية والمراقبة في الوقت الحقيقي.

> [!IMPORTANT]
> لا تنطبق الاستثناءات الموضحة في هذه المقالة على إمكانيات Defender for Endpoint على Mac الأخرى، بما في ذلك الكشف عن تهديدات نقاط النهاية والرد عليها (الكشف التلقائي والاستجابة على النقط النهائية). لا تزال الملفات التي تستبعدها باستخدام الأساليب الموضحة في هذه المقالة تؤدي إلى تشغيل الكشف التلقائي والاستجابة على النقط النهائية والكشف الأخرى.

يمكنك استبعاد بعض الملفات والمجلدات والعمليات والملفات التي تم فتحها من Defender for Endpoint على Mac.

يمكن أن تكون الاستثناءات مفيدة لتجنب الاكتشافات غير الصحيحة للملفات أو البرامج الفريدة أو المخصصة لمنظمتك. ويمكن أن تكون مفيدة أيضا لتخفيف مشاكل الأداء التي تسببها Defender for Endpoint على Mac.

> [!WARNING]
> يقلل تحديد الاستثناءات من الحماية التي يوفرها Defender for Endpoint على Mac. يجب عليك دائما تقييم المخاطر المقترنة بتنفيذ الاستثناءات، ويجب استبعاد الملفات التي تثق بها فقط على أنها ليست ضارة.

## <a name="supported-exclusion-types"></a>أنواع الاستثناءات المعتمدة

يعرض الجدول التالي أنواع الاستثناءات التي يدعمها Defender for Endpoint على Mac.

الاستثناء|التعريف|أمثلة
---|---|---
ملحق الملف|جميع الملفات ذات الملحق، في أي مكان على الجهاز|`.test`
ملف|ملف معين تم تعريفه بواسطة المسار الكامل|`/var/log/test.log` <p> `/var/log/*.log` <p> `/var/log/install.?.log`
المجلد|كل الملفات الموجودة ضمن المجلد المحدد (بشكل تكراري)|`/var/log/` <p> `/var/*/`
معالجة|عملية معينة (محددة بواسطة المسار الكامل أو اسم الملف) وجميع الملفات التي يتم فتحها بواسطة|`/bin/cat` <p> `cat` <p> `c?t`

تدعم استثناءات الملفات والمجلدات و العملية أحرف البدل التالية:

أحرف البدل|الوصف|مثال|تطابقات|غير متطابق
---|---|---|---|---
\*|يطابق أي عدد من الأحرف بما في ذلك بلا (لاحظ أنه عند استخدام حرف البدل هذا داخل مسار سيستبدل مجلدا واحدا فقط)|`/var/*/*.log`|`/var/log/system.log`|`/var/log/nested/system.log`
?|يطابق أي حرف مفرد|`file?.log`|`file1.log` <p> `file2.log`|`file123.log`

> [!NOTE]
> يحاول المنتج حل الارتباطات الثابتة عند تقييم الاستثناءات. لا تعمل دقة الارتباط الثابت عندما يحتوي الاستثناء على أحرف بدل أو لا يكون الملف الهدف ( `Data` على مستوى الصوت) موجودا.

## <a name="how-to-configure-the-list-of-exclusions"></a>كيفية تكوين قائمة الاستثناءات

### <a name="from-the-management-console"></a>من وحدة تحكم الإدارة

لمزيد من المعلومات حول كيفية تكوين الاستثناءات من JAMF أو Intune أو وحدة تحكم إدارة أخرى، راجع تعيين تفضيلات [ل Defender for Endpoint على Mac](mac-preferences.md).

### <a name="from-the-user-interface"></a>من واجهة المستخدم

افتح تطبيق Defender لنقطة النهاية وانتقل إلى **إدارة الإعدادات** \> **إضافة استثناء** أو إزالته...، كما هو موضح في لقطة الشاشة التالية:

![لقطة شاشة لإدارة الاستثناءات.](images/mdatp-37-exclusions.png)

حدد نوع الاستثناء الذي تريد إضافته واتبع المطالبات.

## <a name="validate-exclusions-lists-with-the-eicar-test-file"></a>التحقق من صحة قوائم الاستثناءات باستخدام ملف اختبار EICAR

يمكنك التحقق من أن قوائم الاستثناء تعمل باستخدام `curl` لتنزيل ملف اختباري.

في قصاصة Bash `test.txt` التالية، استبدل بملف يتوافق مع قواعد الاستثناء. على سبيل المثال، إذا قمت باستبعاد `.testing` الملحق، فاستبدل `test.txt` ب `test.testing`. إذا كنت تقوم باختبار مسار، فتأكد من تشغيل الأمر داخل هذا المسار.

```bash
curl -o test.txt https://www.eicar.org/download/eicar.com.txt
```

إذا ذكر Defender for Endpoint على Mac البرامج الضارة، فإن القاعدة لا تعمل. إذا لم يكن هناك تقرير عن وجود برامج ضارة، وكان الملف الذي تم تنزيله موجودا، فإن الاستثناء يعمل. يمكنك فتح الملف للتأكد من أن المحتويات هي نفسها التي تم وصفها في موقع ملف [اختبار EICAR على الويب](http://2016.eicar.org/86-0-Intended-use.html).

إذا لم يكن لديك اتصال بالإنترنت، يمكنك إنشاء ملف اختبار EICAR الخاص بك. اكتب سلسلة EICAR إلى ملف نصي جديد باستخدام الأمر Bash التالي:

```bash
echo 'X5O!P%@AP[4\PZX54(P^)7CC)7}$EICAR-STANDARD-ANTIVIRUS-TEST-FILE!$H+H*' > test.txt
```

يمكنك أيضا نسخ السلسلة إلى ملف نصي فارغ ومحاولة حفظها باسم الملف أو في المجلد الذي تحاول استبعاده.

## <a name="allow-threats"></a>السماح للتهديدات

بالإضافة إلى استبعاد محتوى معين من المسح الضوئي، يمكنك أيضا تكوين المنتج من دون الكشف عن بعض فئات التهديدات (المحددة بواسطة اسم التهديد). يجب توخي الحذر عند استخدام هذه الوظيفة، حيث يمكن أن تترك جهازك بدون حماية.

لإضافة اسم خطر إلى القائمة المسموح بها، قم بتنفيذ الأمر التالي:

```bash
mdatp threat allowed add --name [threat-name]
```

يمكن الحصول على اسم التهديد المقترن بالكشف على جهازك باستخدام الأمر التالي:

```bash
mdatp threat list
```

على سبيل المثال `EICAR-Test-File (not a virus)` ، لإضافة (اسم التهديد المقترن بالكشف عن EICAR) إلى القائمة المسموح بها، قم بتنفيذ الأمر التالي:

```bash
mdatp threat allowed add --name "EICAR-Test-File (not a virus)"
```
