---
title: عرض Defender لـ Office 365 التقارير
f1.keywords:
- CSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: conceptual
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: e47e838c-d99e-4c0b-b9aa-e66c4fae902f
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: يمكن للمسؤولين معرفة كيفية البحث عن Defender لـ Office 365 المتوفرة في مدخل Microsoft 365 Defender الإلكتروني واستخدامها.
ms.custom:
- seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: bcc77aaac71c8f8b4c3d3635b596a56ac12a3d7d
ms.sourcegitcommit: bcbcbd4ddc72ad2fed629619d23fac5827d072bf
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/29/2022
ms.locfileid: "64507480"
---
# <a name="view-defender-for-office-365-reports-in-the-microsoft-365-defender-portal"></a>عرض Defender لـ Office 365 في مدخل Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**ينطبق على**
- [Microsoft Defender لـ Office 365 الخطة 1 الخطة 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Microsoft Defender لـ Office 365 المؤسسات (على سبيل المثال، Microsoft 365 E5 اشتراكات أو Microsoft Defender لـ Office 365 الخطة 1 أو Microsoft Defender لـ Office 365 الإضافية "الخطة 2") على مجموعة متنوعة من التقارير ذات الصلة ب الأمان. إذا كانت لديك [الأذونات اللازمة](#what-permissions-are-needed-to-view-the-defender-for-office-365-reports)، يمكنك عرض هذه التقارير وتنزيلها في Microsoft 365 Defender المدخل.

## <a name="view-and-download-reports"></a>عرض التقارير وتنزيلها

### <a name="view-reports"></a>عرض التقارير

1. في مدخل Microsoft 365 Defender، <https://security.microsoft.com>انتقل إلى **تقارير** \> البريد الإلكتروني & **البريد** \> الإلكتروني & **التعاون**. انتقل مباشرة إلى صفحة **البريد الإلكتروني & التعاون،** استخدم <https://security.microsoft.com/emailandcollabreport>.

1. اختر التقرير الذي تريد عرضه، ثم حدد **عرض التفاصيل**.  

### <a name="download-reports"></a>تنزيل التقارير

1. في Microsoft 365 Defender في <https://security.microsoft.com>، انتقل إلى **تقارير** >  **& تقارير** \> **التعاون للتنزيل**. الانتقال مباشرة إلى صفحة **التقارير للتنزيل** ، استخدم <https://security.microsoft.com/ReportsForDownload?viewid=custom>.

:::image type="content" source="../../media/email-collaboration-download-reports.png" alt-text="صفحة تقارير & البريد الإلكتروني في مدخل Microsoft 365 Defender الإلكتروني" lightbox="../../media/email-collaboration-download-reports.png":::

> [!NOTE]
>
> يتم وصف تقارير أمان البريد الإلكتروني التي لا Defender لـ Office 365 في عرض تقارير أمان البريد الإلكتروني في Microsoft 365 Defender [المدخل](view-email-security-reports.md).
>
> توجد التقارير المرتبطة بتدفق البريد الآن في Exchange إدارة البريد (EAC). لمزيد من المعلومات حول هذه التقارير، راجع تقارير تدفق البريد [في مركز Exchange الجديد](/exchange/monitoring/mail-flow-reports/mail-flow-reports).

## <a name="safe-attachments-file-types-report"></a>خزينة أنواع ملفات المرفقات

> [!NOTE]
> تم إهمال هذا التقرير. تتوفر المعلومات نفسها في تقرير حالة [الحماية من المخاطر](#threat-protection-status-report).

## <a name="safe-attachments-message-disposition-report"></a>خزينة تقرير تغيير موضع رسالة المرفقات

> [!NOTE]
> تم إهمال هذا التقرير. تتوفر المعلومات نفسها في تقرير حالة [الحماية من المخاطر](#threat-protection-status-report).

## <a name="mail-latency-report"></a>تقرير زمن زمن زمن إرسال البريد

يعرض **لك تقرير زمن** زمن انتهاء البريد طريقة عرض مجمعة لتسليم البريد و زمن زمن إرسال الخدمة الذي تم تجربته داخل مؤسستك. تتأثر أوقات تسليم البريد في الخدمة بعدد من العوامل، وغالبا ما لا يكون وقت التسليم المطلق بالثواني مؤشرا جيدا للنجاح أو المشكلة. قد يعتبر بطء وقت التسليم في يوم واحد متوسط وقت التسليم في يوم آخر، أو العكس بالعكس. يحاول هذا الأمر تأهيل تسليم الرسائل استنادا إلى بيانات إحصائية حول أوقات تسليم الرسائل الأخرى التي تم ملاحظتها.

لا يتم تضمين زمن زمن انتهاء العميل من جانب العميل والشبكات.

لعرض التقرير، افتح <https://security.microsoft.com>مدخل Microsoft 365 Defender في ،  \> انتقل إلى تقارير البريد الإلكتروني & **البريد** \> الإلكتروني & **التعاون**. انتقل مباشرة إلى صفحة **البريد الإلكتروني & التعاون،** استخدم <https://security.microsoft.com/emailandcollabreport>.

في صفحة **البريد & تقارير** التعاون، ابحث عن تقرير زمن إرسال البريد، ثم انقر فوق **عرض التفاصيل**. للذهاب مباشرة إلى التقرير، استخدم <https://security.microsoft.com/mailLatencyReport>.


:::image type="content" source="../../media/mail-latency-report-widget.png" alt-text="عنصر واجهة مستخدم تقرير زمن زمن إرسال البريد على صفحة تقارير & البريد الإلكتروني" lightbox="../../media/mail-latency-report-widget.png":::

في صفحة **تقرير زمن** إرسال البريد، تتوفر علامات التبويب التالية في صفحة تقرير زمن زمن **إرسال** البريد:

- **النسبة المئوية 50**: هذا هو الوسط في أوقات تسليم الرسائل. يمكنك اعتبار هذه القيمة كمتوسط وقت التسليم. يتم تحديد علامة التبويب هذه بشكل افتراضي.
- **النسبة المئوية 90**: يشير ذلك إلى زمن عال لتسليم الرسالة. استغرق 10٪ فقط من الرسائل وقتا أطول من هذه القيمة لتسليمها.
- **النسبة المئوية 99**: يشير ذلك إلى أعلى زمن زمن تسليم للرسالة.

بغض النظر عن علامة التبويب التي تحددها، يعرض المخطط الرسائل المنظمة في الفئات التالية:

- **الإجمالي**
- **التهجير**

عند مرورك فوق فئة في المخطط، يمكنك رؤية تصنيف تفصيلي ل زمن زمن الوصول في كل فئة.

:::image type="content" source="../../media/mail-latency-report-50th-percentile-view.png" alt-text="طريقة عرض القيم المئوية ال 50 للتقرير &quot;زمن إرسال البريد&quot;" lightbox="../../media/mail-latency-report-50th-percentile-view.png":::

إذا نقرت فوق **تصفية**، يمكنك تصفية كل من المخطط جدول التفاصيل حسب القيم التالية:

- **التاريخ (UTC)**: **تاريخ البدء** **وتاريخ الانتهاء**
- **طريقة عرض الرسالة**: إحدى القيم التالية:
  - **كافة الرسائل**
  - **الرسائل المرتوبة**: إحدى القيم التالية:
    - **التوصيل المضمر**: يتضمن الرسائل التي يتم اختبارها بالكامل قبل التسليم.
    - **التشوه غير المتزامن**

عند الانتهاء من تكوين عوامل التصفية، انقر فوق **تطبيق** عوامل التصفية أو إلغاء الأمر أو **مسحها**.

في جدول التفاصيل أسفل المخطط، تتوفر المعلومات التالية:

- **التاريخ (UTC)**
- **زمن زمن التأخر**
- **عدد الرسائل**
- **النسبة المئوية 50**
- **النسبة المئوية 90**
- **النسبة المئوية 99**

على صفحة التقرير الرئيسي، الأيقونة ![تصدير.](../../media/m365-cc-sc-download-icon.png) **[الزر](view-email-security-reports.md#export-report)** "تصدير" متوفر.

## <a name="threat-protection-status-report"></a>تقرير حالة الحماية من المخاطر

تقرير **حالة الحماية من** المخاطر هو طريقة عرض واحدة تجمع معلومات حول المحتوى الضار والبريد الإلكتروني الضار الذي تم اكتشافه وحظره بواسطة [Exchange Online Protection (](exchange-online-protection-overview.md)EOP) Microsoft Defender لـ Office 365. لمزيد من المعلومات، راجع [تقرير حالة الحماية من المخاطر](view-email-security-reports.md#threat-protection-status-report).

## <a name="top-senders-and-recipients-report"></a>تقرير أهم المرسلين والمستلمين

يظهر **تقرير أهم المرسلين** والمستلمين أهم المستلمين ل EOP Defender لـ Office 365 الحماية. لمزيد من المعلومات، راجع [تقرير أهم المرسلين والمستلمين](view-email-security-reports.md#top-senders-and-recipients-report).

## <a name="url-protection-report"></a>تقرير حماية URL

يوفر **تقرير حماية URL** طرق عرض ملخصة واتجاهات للتهديدات التي تم الكشف عنها والإجراءات التي تم اتخاذها على نقرات URL كجزء من خزينة [الارتباطات](safe-links.md). لن ينقر هذا التقرير فوق بيانات من المستخدمين حيث خزينة نهج الارتباطات عندما لا يكون الخيار تعقب نقرات المستخدم محددا.

لعرض التقرير، افتح مدخل Microsoft 365 Defender [،](https://security.microsoft.com) واذهب  \> إلى تقارير البريد الإلكتروني & **البريد** \> الإلكتروني & **تقارير التعاون**. في صفحة **البريد & تقارير التعاون،** ابحث عن **صفحة حماية URL** ، ثم انقر فوق **عرض التفاصيل**. للذهاب مباشرة إلى التقرير، افتح <https://security.microsoft.com/reports/URLProtectionActionReport>.

:::image type="content" source="../../media/url-protection-report-widget.png" alt-text="عنصر واجهة مستخدم تقرير حماية URL على صفحة تقارير & البريد الإلكتروني" lightbox="../../media/url-protection-report-widget.png":::

يتم وصف طرق العرض المتوفرة على صفحة تقرير حماية **URL** في الأقسام التالية.

> [!NOTE]
> هذا تقرير اتجاه *الحماية،* مما يعني أن البيانات تمثل الاتجاهات في مجموعة بيانات أكبر. ونتيجة لذلك، لا تتوفر البيانات الموجودة في المخططات في الوقت الحقيقي هنا، ولكن البيانات الموجودة في جدول التفاصيل متوفرة، لذلك قد ترى تعارضا طفيفا بين الاثنين. يتم تحديث المخططات مرة واحدة كل أربع ساعات وتحتوي على بيانات خلال آخر 90 يوما.

### <a name="view-data-by-url-click-protection-action"></a>إجراء الحماية من النقر فوق URL لعرض البيانات حسب عنوان URL

:::image type="content" source="../../media/url-threat-protection-report-url-click-protection-action-view.png" alt-text="طريقة العرض تحديدا إجراء حماية النقر فوق عنوان URL في تقرير حماية URL" lightbox="../../media/url-threat-protection-report-url-click-protection-action-view.png":::

تظهر **طريقة عرض البيانات حسب URL** طريقة عرض إجراء الحماية بالنقر فوق URL عدد نقرات URL التي ينقر عليها المستخدمون في المؤسسة ونتائج النقر:

- **مسموح به**: النقرات المسموح بها.
- **مسموح به من قبل مسؤول المستأجر**: النقرات المسموح بها في خزينة الارتباطات.
- **تم الحظر**: انقر فوق المحظور.
- **تم حظرها من قبل مسؤول المستأجر**: تم حظر النقرات في خزينة الارتباطات.
- **تم الحظر والنقر عبر**: النقرات المحظورة حيث ينقر المستخدمون عبر عنوان URL المحظور.
- **تم حظره من قبل مسؤول المستأجر والنقر فوقه من خلال**: قام المسؤول بحظر الارتباط، ولكن المستخدم قام بالنقر عبره.
- **النقر خلال أثناء الفحص**: النقرات التي ينقر فيها المستخدمون عبر صفحة الفحص المعلقة إلى عنوان URL.
- **الفحص المعلق**: النقر فوق عناوين URL التي تنتظر قرار الفحص.

تشير النقرة إلى أن المستخدم قد نقر عبر صفحة الحظر إلى موقع ويب الضار (يمكن للمسؤولين تعطيل النقر عبر في خزينة الارتباطات).

إذا نقرت فوق **عوامل التصفية**، يمكنك تعديل التقرير جدول التفاصيل عن طريق تحديد قيمة واحدة أو أكثر من القيم التالية في القائمة المنسوبة التي تظهر:

- **التاريخ (UTC)**: **تاريخ البدء** **وتاريخ الانتهاء**
- **الإجراء**:
  - **مسموح به**
  - **تم الحظر**
  - **مسموح به من قبل مسؤول المستأجر**
  - **تم الحظر والنقر عبر**
  - **تم حظره من قبل مسؤول المستأجر والنقر عبر**
  - **النقر فوقه أثناء الفحص**
  - **فحص معلق**
- **المجالات**: مجالات URL المدرجة في نتائج التقرير.
- **المستلمون**

عند الانتهاء من تكوين عوامل التصفية، انقر فوق **تطبيق** عوامل التصفية أو إلغاء الأمر أو **مسحها**.

يوفر جدول التفاصيل أسفل المخطط طريقة العرض التالية في الوقت الحقيقي لكل النقرات التي حدثت داخل المؤسسة لآخر 7 أيام:

- **انقر فوق الوقت**
- **User**
- **URL**
- **الإجراء**
- **App**

في صفحة التقرير الرئيسي، الأيقونة ![إنشاء جدول.](../../media/m365-cc-sc-create-icon.png) **[إنشاء جدول زمني](view-email-security-reports.md#schedule-report)**، أيقونة ![طلب تقرير.](../../media/m365-cc-sc-download-icon.png) **[طلب تقرير](view-email-security-reports.md#request-report)**، وأيقونة ![التصدير.](../../media/m365-cc-sc-download-icon.png) **[تتوفر](view-email-security-reports.md#export-report)** أزرار التصدير.

### <a name="view-data-by-url-click-by-application"></a>عرض البيانات حسب عنوان URL النقر حسب التطبيق

:::image type="content" source="../../media/url-threat-protection-report-url-click-by-application-view.png" alt-text="طريقة عرض إجراء الحماية للنقر فوق URL في تقرير حماية URL" lightbox="../../media/url-threat-protection-report-url-click-by-application-view.png":::

تعرض **طريقة عرض البيانات بواسطة URL** بالنقر حسب التطبيق عدد نقرات URL حسب التطبيقات التي تدعم خزينة الارتباطات:

- **عميل البريد الإلكتروني**
- **Office مستند**
- **الفرق**

إذا نقرت فوق **عوامل التصفية**، يمكنك تعديل التقرير جدول التفاصيل عن طريق تحديد قيمة واحدة أو أكثر من القيم التالية في القائمة المنسوبة التي تظهر:

- **التاريخ (UTC)**: **تاريخ البدء** **وتاريخ الانتهاء**
- **الكشف**: التطبيقات المتوفرة من المخطط.
- **المجالات**: مجالات URL المدرجة في نتائج التقرير.
- **المستلمون**

عند الانتهاء من تكوين عوامل التصفية، انقر فوق **تطبيق** عوامل التصفية أو إلغاء الأمر أو **مسحها**.

يوفر جدول التفاصيل أسفل المخطط طريقة العرض التالية في الوقت الحقيقي لكل النقرات التي حدثت داخل المؤسسة لآخر 7 أيام:

- **انقر فوق الوقت**
- **User**
- **URL**
- **الإجراء**
- **App**

في صفحة التقرير الرئيسي، الأيقونة ![إنشاء جدول.](../../media/m365-cc-sc-create-icon.png) **[إنشاء جدول زمني](view-email-security-reports.md#schedule-report)**، أيقونة ![طلب تقرير.](../../media/m365-cc-sc-download-icon.png) **[طلب تقرير](view-email-security-reports.md#request-report)**، وأيقونة ![التصدير.](../../media/m365-cc-sc-download-icon.png) **[تتوفر](view-email-security-reports.md#export-report)** أزرار التصدير.

## <a name="additional-reports-to-view"></a>تقارير إضافية لعرضها

بالإضافة إلى التقارير الموضحة في هذه المقالة، تتوفر عدة تقارير أخرى، كما هو موضح في الجدول التالي:

|تقرير|الموضوع|
|---|---|
|**المستكشف** (Microsoft Defender لـ Office 365 2) **أو الكشف في** الوقت الحقيقي (Microsoft Defender لـ Office 365 الخطة 1)|[مستكشف التهديدات (والكشف في الوقت الحقيقي)](threat-explorer.md)|
|تقارير أمان البريد الإلكتروني التي لا تتطلب Defender لـ Office 365|[عرض تقارير أمان البريد الإلكتروني في مدخل Microsoft 365 Defender الإلكتروني](view-email-security-reports.md)|
|تقارير تدفق البريد في Exchange إدارة البريد (EAC)|[تقارير تدفق البريد في مركز إدارة Exchange الجديد](/exchange/monitoring/mail-flow-reports/mail-flow-reports)|

Cmdlets لتقارير PowerShell:

|تقرير|الموضوع|
|---|---|
|أهم المرسلين والمستلمين|[Get-MailTrafficTopReport](/powershell/module/exchange/get-mailtraffictopreport) <p> [Get-MailTrafficSummaryReport](/powershell/module/exchange/get-mailtrafficsummaryreport)|
|أفضل البرامج الضارة|[Get-MailTrafficSummaryReport](/powershell/module/exchange/get-mailtrafficsummaryreport)|
|حركة مرور البريد|[Get-MailTrafficATPReport](/powershell/module/exchange/get-mailtrafficatpreport) <p> [Get-MailDetailATPReport](/powershell/module/exchange/get-maildetailatpreport)|
|الارتباطات الآمنة|[Get-SafeLinksAggregateReport](/powershell/module/exchange/get-safelinksaggregatereport) <p> [Get-SafeLinksDetailReport](/powershell/module/exchange/get-safelinksdetailreport)|
|المستخدمون الذين تم اختراقهم|[Get-CompromisedUserAggregateReport](/powershell/module/exchange/get-compromiseduseraggregatereport) <p> [Get-CompromisedUserDetailReport](/powershell/module/exchange/get-compromiseduserdetailreport)|
|حالة تدفق البريد|[Get-MailflowStatusReport](/powershell/module/exchange/get-mailflowstatusreport)|
|المستخدمون المنتحلون|[Get-SpoofMailReport](/powershell/module/exchange/get-spoofmailreport)|

## <a name="what-permissions-are-needed-to-view-the-defender-for-office-365-reports"></a>ما هي الأذونات المطلوبة لعرض Defender لـ Office 365 التقارير؟

لعرض التقارير الموضحة في هذه المقالة واستخدامها، يجب أن تكون عضوا في إحدى مجموعات الدور التالية في مدخل Microsoft 365 Defender:

- **إدارة المؤسسة**
- **مسؤول الأمان**
- **قارئ الأمان**
- **القارئ العام**

لمزيد من المعلومات، راجع [الأذونات في Microsoft 365 Defender المدخل](permissions-microsoft-365-security-center.md).

**ملاحظة**: تؤدي إضافة مستخدمين إلى دور Azure Active Directory المناظر في مركز مسؤولي Microsoft 365 إلى منح المستخدمين الأذونات المطلوبة في مدخل Microsoft 365 Defender والأذونات للميزات الأخرى  في Microsoft 365. لمزيد من المعلومات، راجع [حول أدوار المسؤولين](../../admin/add-users/about-admin-roles.md).

## <a name="what-if-the-reports-arent-showing-data"></a>ماذا لو لم تعرض التقارير البيانات؟

إذا لم تكن ترى البيانات في تقارير Defender لـ Office 365، فتحقق مرة أخرى من إعداد سياساتك بشكل صحيح. يجب أن يكون [لدى مؤسستك خزينة الارتباطات](set-up-safe-links-policies.md) خزينة الارتباطات [](set-up-safe-attachments-policies.md) المحددة لكي Defender لـ Office 365 حماية المرفقات في مكانها. راجع أيضا [الحماية من البريد العشوائي والبرامج الضارة](anti-spam-and-anti-malware-protection.md).

## <a name="related-topics"></a>المواضيع ذات الصلة

[تقارير ذكية ورؤى في مدخل Microsoft 365 Defender](reports-and-insights-in-security-and-compliance.md)

[أدوار Azure AD المضمنة](/azure/active-directory/roles/permissions-reference)
