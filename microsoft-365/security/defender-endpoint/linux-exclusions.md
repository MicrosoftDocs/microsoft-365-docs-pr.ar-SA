---
title: تكوين استثناءات Microsoft Defender لنقطة النهاية على Linux والتحقق من صحتها
description: توفير استثناءات ل Microsoft Defender ل Endpoint على Linux والتحقق من صحتها. يمكن تعيين الاستثناءات للملفات والمجلدات والعمليات.
keywords: microsoft، defender، Microsoft Defender ل Endpoint، linux، الاستثناءات، المسح الضوئي، برنامج الحماية من الفيروسات
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
ms.openlocfilehash: b86cad016af0f7819d69f0156498336652e6292d
ms.sourcegitcommit: dfa9f28a5a5055a9530ec82c7f594808bf28d0dc
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 11/29/2021
ms.locfileid: "63570675"
---
# <a name="configure-and-validate-exclusions-for-microsoft-defender-for-endpoint-on-linux"></a>تكوين استثناءات Microsoft Defender لنقطة النهاية على Linux والتحقق من صحتها

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**

- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

توفر هذه المقالة معلومات حول كيفية تعريف الاستثناءات التي تنطبق على عمليات الفحص عند الطلب، والحماية والمراقبة في الوقت الحقيقي.

> [!IMPORTANT]
> لا تنطبق الاستثناءات الموضحة في هذه المقالة على إمكانيات Defender for Endpoint على Linux الأخرى، بما في ذلك الكشف عن تهديدات نقاط النهاية والرد عليها (الكشف التلقائي والاستجابة على النقط النهائية). لا تزال الملفات التي تستبعدها باستخدام الأساليب الموضحة في هذه المقالة تؤدي إلى تشغيل الكشف التلقائي والاستجابة على النقط النهائية والكشف الأخرى.

يمكنك استبعاد بعض الملفات والمجلدات والعمليات والملفات التي تم فتحها من Defender for Endpoint على عمليات فحص Linux.

يمكن أن تكون الاستثناءات مفيدة لتجنب الاكتشافات غير الصحيحة للملفات أو البرامج الفريدة أو المخصصة لمنظمتك. كما يمكن أن تكون مفيدة لتخفيف مشاكل الأداء التي يسببها Defender for Endpoint على Linux.

> [!WARNING]
> يقلل تحديد الاستثناءات من الحماية التي يوفرها Defender for Endpoint على Linux. يجب عليك دائما تقييم المخاطر المقترنة بتنفيذ الاستثناءات، ويجب استبعاد الملفات التي تثق بها فقط على أنها ليست ضارة.

## <a name="supported-exclusion-types"></a>أنواع الاستثناءات المعتمدة

يعرض الجدول التالي أنواع الاستثناءات التي يدعمها Defender for Endpoint على Linux.

الاستثناء|التعريف|أمثلة
---|---|---
ملحق الملف|جميع الملفات ذات الملحق، في أي مكان على الجهاز|`.test`
ملف|ملف معين تم تعريفه بواسطة المسار الكامل|`/var/log/test.log`<br/>`/var/log/*.log`<br/>`/var/log/install.?.log`
المجلد|كل الملفات الموجودة ضمن المجلد المحدد (بشكل تكراري)|`/var/log/`<br/>`/var/*/`
معالجة|عملية معينة (محددة بواسطة المسار الكامل أو اسم الملف) وجميع الملفات التي يتم فتحها بواسطة|`/bin/cat`<br/>`cat`<br/>`c?t`

> [!IMPORTANT]
> يجب أن تكون المسارات أعلاه ارتباطات صعبة، وليس ارتباطات رمزية، لكي يتم استبعادها بنجاح. يمكنك التحقق مما إذا كان المسار هو ارتباط رمزي عن طريق تشغيل `file <path-name>`.

تدعم استثناءات الملفات والمجلدات و العملية أحرف البدل التالية:

أحرف البدل|الوصف|مثال|تطابقات|غير متطابق
---|---|---|---|---
\*|يطابق أي عدد من الأحرف بما في ذلك بلا (لاحظ أنه عند استخدام حرف البدل هذا داخل مسار سيستبدل مجلدا واحدا فقط)|`/var/\*/\*.log`|`/var/log/system.log`|`/var/log/nested/system.log`
?|يطابق أي حرف مفرد|`file?.log`|`file1.log`<br/>`file2.log`|`file123.log`

## <a name="how-to-configure-the-list-of-exclusions"></a>كيفية تكوين قائمة الاستثناءات

### <a name="from-the-management-console"></a>من وحدة تحكم الإدارة

للحصول على مزيد من المعلومات حول كيفية تكوين الاستثناءات من "مهى" أو "غير قابل للطي" أو وحدة تحكم إدارة أخرى، راجع تعيين تفضيلات [ل Defender for Endpoint على Linux](linux-preferences.md).

### <a name="from-the-command-line"></a>من سطر الأوامر

قم بتشغيل الأمر التالي لرؤية مفاتيح التبديل المتوفرة لإدارة الاستثناءات:

```bash
mdatp exclusion
```

> [!TIP]
> عند تكوين الاستثناءات باستخدام أحرف البدل، قم بإحاطة المعلمة بين علامات اقتباس مزدوجة لمنع الكبل.

أمثلة:

- إضافة استثناء لملحق ملف:

    ```bash
    mdatp exclusion extension add --name .txt
    ```

    ```Output
    Extension exclusion configured successfully
    ```

- إضافة استثناء لملف:

    ```bash
    mdatp exclusion file add --path /var/log/dummy.log
    ```

    ```Output
    File exclusion configured successfully
    ```

- إضافة استثناء لمجلد:

    ```bash
    mdatp exclusion folder add --path /var/log/
    ```

    ```Output
    Folder exclusion configured successfully
    ```

- إضافة استثناء لمجلد ثان:

    ```bash
    mdatp exclusion folder add --path /var/log/
    mdatp exclusion folder add --path /other/folder
    ```

    ```Output
    Folder exclusion configured successfully
    ```

- أضف استثناء لمجلد يحتوي على أحرف بدل:

    ```bash
    mdatp exclusion folder add --path "/var/*/"
    ```

    > [!NOTE]
    > سيستبعد هذا فقط المسارات الموجودة أسفل */var/*، وليس المجلدات الأكثر تداخلا؛ على سبيل المثال، */var/this-subfolder/but-not-this-subfolder*.

    ```bash
    mdatp exclusion folder add --path "/var/"
    ```

    > [!NOTE]
    > سيستبعد هذا كل المسارات التي يكون أصلها */var/*; على سبيل المثال، */var/this-subfolder/and-this-subfolder-as-well*.

    ```Output
    Folder exclusion configured successfully
    ```

- إضافة استثناء لعملية:

    ```bash
    mdatp exclusion process add --name cat
    ```

    ```Output
    Process exclusion configured successfully
    ```

- إضافة استثناء لعملية ثانية:

    ```bash
    mdatp exclusion process add --name cat
    mdatp exclusion process add --name dog
    ```

    ```Output
    Process exclusion configured successfully
    ```

## <a name="validate-exclusions-lists-with-the-eicar-test-file"></a>التحقق من صحة قوائم الاستثناءات باستخدام ملف اختبار EICAR

يمكنك التحقق من أن قوائم الاستثناء تعمل باستخدام `curl` لتنزيل ملف اختباري.

في قصاصة Bash `test.txt` التالية، استبدل بملف يتوافق مع قواعد الاستثناء. على سبيل المثال، إذا قمت باستبعاد `.testing` الملحق، فاستبدل `test.txt` ب `test.testing`. إذا كنت تقوم باختبار مسار، فتأكد من تشغيل الأمر داخل هذا المسار.

```bash
curl -o test.txt https://www.eicar.org/download/eicar.com.txt
```

إذا ذكر Defender for Endpoint على Linux البرامج الضارة، فإن القاعدة لا تعمل. إذا لم يكن هناك تقرير عن وجود برامج ضارة، وكان الملف الذي تم تنزيله موجودا، فإن الاستثناء يعمل. يمكنك فتح الملف للتأكد من أن المحتويات هي نفسها التي تم وصفها في موقع ملف [اختبار EICAR على الويب](http://2016.eicar.org/86-0-Intended-use.html).

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
