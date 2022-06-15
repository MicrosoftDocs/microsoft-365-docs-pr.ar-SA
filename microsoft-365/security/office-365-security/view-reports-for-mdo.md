---
title: عرض تقارير Defender لـ Office 365
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
description: يمكن للمسؤولين معرفة كيفية العثور على تقارير Defender لـ Office 365 المتوفرة في مدخل Microsoft 365 Defender واستخدامها.
ms.custom:
- seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 551d2f0f2da872ff24da2bd0d691eea775894c08
ms.sourcegitcommit: 3b194dd6f9ce531ae1b33d617ab45990d48bd3d0
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/15/2022
ms.locfileid: "66102559"
---
# <a name="view-defender-for-office-365-reports-in-the-microsoft-365-defender-portal"></a>عرض تقارير Defender لـ Office 365 في مدخل Microsoft 365 Defender

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**ينطبق على**
- [خطة 1 وخطة 2 من Microsoft Defender لـ Office 365](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Microsoft Defender لـ Office 365 المؤسسات (على سبيل المثال، Microsoft 365 E5 الاشتراكات أو Microsoft Defender لـ Office 365 الخطة 1 أو تحتوي Microsoft Defender لـ Office 365 الوظائف الإضافية للخطة 2) على مجموعة متنوعة من التقارير المتعلقة بالأمان. إذا كان لديك [الأذونات اللازمة](#what-permissions-are-needed-to-view-the-defender-for-office-365-reports)، يمكنك عرض هذه التقارير وتنزيلها في مدخل Microsoft 365 Defender.

## <a name="view-and-download-reports"></a>عرض التقارير وتنزيلها

### <a name="view-reports"></a>عرض التقارير

1. في مدخل Microsoft 365 Defender، <https://security.microsoft.com>انتقل إلى **تقارير** \> **التعاون** \> **& البريد الإلكتروني & التقارير**. للانتقال مباشرة إلى صفحة **تقارير التعاون & البريد الإلكتروني** ، استخدم <https://security.microsoft.com/emailandcollabreport>.

1. اختر التقرير الذي تريد عرضه، ثم حدد **"عرض التفاصيل**".

### <a name="download-reports"></a>تنزيل التقارير

في مدخل Microsoft 365 Defender، <https://security.microsoft.com>انتقل إلى **تقارير** > **التعاون** \> & **البريد الإلكتروني للتقارير للتنزيل**. للانتقال مباشرة إلى صفحة **"التقارير" للتنزيل** ، استخدم <https://security.microsoft.com/ReportsForDownload?viewid=custom>.

:::image type="content" source="../../media/email-collaboration-download-reports.png" alt-text="صفحة تقارير التعاون & البريد الإلكتروني في مدخل Microsoft 365 Defender" lightbox="../../media/email-collaboration-download-reports.png":::

> [!NOTE]
>
> يتم وصف تقارير أمان البريد الإلكتروني التي لا تتطلب Defender لـ Office 365 في [عرض تقارير أمان البريد الإلكتروني في مدخل Microsoft 365 Defender](view-email-security-reports.md).
>
> التقارير المتعلقة بتدفق البريد موجودة الآن في مركز إدارة Exchange (EAC). لمزيد من المعلومات حول هذه التقارير، راجع [تقارير تدفق البريد في مركز إدارة Exchange الجديد](/exchange/monitoring/mail-flow-reports/mail-flow-reports).

## <a name="safe-attachments-file-types-report"></a>تقرير أنواع ملفات خزينة المرفقات

> [!NOTE]
> تم إهمال هذا التقرير. تتوفر المعلومات نفسها في [تقرير حالة الحماية من التهديدات](#threat-protection-status-report).

## <a name="safe-attachments-message-disposition-report"></a>تقرير الترتيب لرسالة خزينة المرفقات

> [!NOTE]
> تم إهمال هذا التقرير. تتوفر المعلومات نفسها في [تقرير حالة الحماية من التهديدات](#threat-protection-status-report).

## <a name="mail-latency-report"></a>تقرير زمن انتقال البريد

يعرض **لك تقرير زمن انتقال البريد** طريقة عرض مجمعة لزمن انتقال تسليم البريد والتنقل في مؤسستك. تتأثر أوقات تسليم البريد في الخدمة بعدد من العوامل، وغالبا ما لا يكون وقت التسليم المطلق بالثوان مؤشرا جيدا للنجاح أو مشكلة. قد يعتبر وقت التسليم البطيء في يوم واحد متوسط وقت التسليم في يوم آخر، أو العكس بالعكس. يحاول هذا تأهيل تسليم الرسائل استنادا إلى بيانات إحصائية حول أوقات التسليم الملاحظة للرسائل الأخرى.

لا يتم تضمين جانب العميل وزمن انتقال الشبكة.

لعرض التقرير، افتح مدخل Microsoft 365 Defender في <https://security.microsoft.com>تقارير  \> **التعاون** \> & **& البريد الإلكتروني & التقارير**. للانتقال مباشرة إلى صفحة **تقارير التعاون & البريد الإلكتروني** ، استخدم <https://security.microsoft.com/emailandcollabreport>.

في صفحة **تقارير التعاون & البريد الإلكتروني** ، ابحث عن **تقرير زمن انتقال البريد** ثم انقر فوق **"عرض التفاصيل**". للانتقال مباشرة إلى التقرير، استخدم <https://security.microsoft.com/mailLatencyReport>.

:::image type="content" source="../../media/mail-latency-report-widget.png" alt-text="عنصر واجهة مستخدم تقرير زمن انتقال البريد في صفحة تقارير التعاون & البريد الإلكتروني" lightbox="../../media/mail-latency-report-widget.png":::

في صفحة **تقرير زمن انتقال البريد** ، تتوفر علامات التبويب التالية في صفحة **تقرير زمن انتقال البريد** :

- **القيمة المئوية 50**: هذا هو الوسط لأوقات تسليم الرسائل. يمكنك اعتبار هذه القيمة متوسط وقت التسليم. يتم تحديد علامة التبويب هذه بشكل افتراضي.
- **القيمة المئوية 90**: يشير ذلك إلى زمن انتقال عال لتسليم الرسائل. استغرق 10٪ فقط من الرسائل وقتا أطول من هذه القيمة لتسليمها.
- **القيمة المئوية 99**: يشير هذا إلى أعلى زمن انتقال لتسليم الرسائل.

بغض النظر عن علامة التبويب التي تحددها، يعرض المخطط الرسائل المنظمة في الفئات التالية:

- **العام**
- **التفجير**

عند تمرير الماوس فوق فئة في المخطط، يمكنك رؤية تصنيف تفصيلي لزمن الانتقال في كل فئة.

:::image type="content" source="../../media/mail-latency-report-50th-percentile-view.png" alt-text="طريقة عرض النسبة المئوية 50 لتقرير زمن انتقال البريد" lightbox="../../media/mail-latency-report-50th-percentile-view.png":::

إذا نقرت فوق **"تصفية**"، يمكنك تصفية كل من المخطط وجدول التفاصيل حسب القيم التالية:

- **التاريخ (UTC)**: **تاريخ البدء** **وتاريخ الانتهاء**
- **طريقة عرض الرسالة**: إحدى القيم التالية:
  - **كافة الرسائل**
  - **الرسائل التي تم معالجتها**: إحدى القيم التالية:
    - **التضمين المضمن**: يتضمن الرسائل التي يتم اختبارها بالكامل قبل التسليم.
    - **معالجة غير متزامنة**

عند الانتهاء من تكوين عوامل التصفية، انقر فوق **تطبيق** **عوامل التصفية** أو **إلغاؤها** أو مسحها.

في جدول التفاصيل أسفل المخطط، تتوفر المعلومات التالية:

- **التاريخ (UTC)**
- **الكمون**
- **عدد الرسائل**
- **القيمة المئوية 50**
- **القيمة المئوية 90**
- **القيمة المئوية 99**

في صفحة التقرير الرئيسية، أيقونة !["تصدير".](../../media/m365-cc-sc-download-icon.png) الزر **["تصدير](view-email-security-reports.md#export-report)**" متوفر.

## <a name="threat-protection-status-report"></a>تقرير حالة الحماية من التهديدات

تقرير **حالة الحماية من التهديدات** هو طريقة عرض واحدة تجمع معلومات حول المحتوى الضار والبريد الإلكتروني الضار الذي تم اكتشافه وحظره بواسطة [Exchange Online Protection](exchange-online-protection-overview.md) (EOP) Microsoft Defender لـ Office 365. لمزيد من المعلومات، راجع [تقرير حالة الحماية من التهديدات](view-email-security-reports.md#threat-protection-status-report).

## <a name="top-senders-and-recipients-report"></a>تقرير أفضل المرسلين والمستلمين

يعرض تقرير **أفضل المرسلين والمستلمين** أفضل المستلمين لميزات EOP وحماية Defender لـ Office 365. لمزيد من المعلومات، راجع [تقرير أفضل المرسلين والمستلمين](view-email-security-reports.md#top-senders-and-recipients-report).

## <a name="url-protection-report"></a>تقرير حماية URL

يوفر **تقرير حماية URL** طرق عرض موجزة واتجاهية للتهديدات التي تم اكتشافها والإجراءات المتخذة عند النقر فوق URL كجزء من [خزينة الارتباطات](safe-links.md). لن يحتوي هذا التقرير على بيانات النقر من المستخدمين حيث تم تطبيق نهج الارتباطات خزينة عند عدم تحديد الخيار **"تعقب نقرات المستخدم**".

لعرض التقرير، افتح [مدخل Microsoft 365 Defender](https://security.microsoft.com)، **وانتقل إلى** \> تقارير **التعاون** \> **& البريد الإلكتروني & البريد الإلكتروني للتقارير**. في صفحة **تقارير التعاون & البريد الإلكتروني** ، ابحث عن **صفحة حماية عنوان URL** ثم انقر فوق **"عرض التفاصيل**". للانتقال مباشرة إلى التقرير، افتح <https://security.microsoft.com/reports/URLProtectionActionReport>.

:::image type="content" source="../../media/url-protection-report-widget.png" alt-text="عنصر واجهة مستخدم تقرير حماية URL في صفحة تقارير التعاون & البريد الإلكتروني" lightbox="../../media/url-protection-report-widget.png":::

يتم وصف طرق العرض المتوفرة على صفحة تقرير **حماية URL** في المقاطع التالية.

> [!NOTE]
> هذا *هو تقرير اتجاه الحماية*، ما يعني أن البيانات تمثل الاتجاهات في مجموعة بيانات أكبر. ونتيجة لذلك، لا تتوفر البيانات الموجودة في المخططات في الوقت الحقيقي هنا، ولكن البيانات الموجودة في جدول التفاصيل متوفرة، لذلك قد ترى اختلافا طفيفا بين الاثنين. يتم تحديث المخططات مرة واحدة كل أربع ساعات وتحتوي على بيانات لآخر 90 يوما.

### <a name="view-data-by-url-click-protection-action"></a>عرض البيانات حسب إجراء الحماية من النقر فوق URL

:::image type="content" source="../../media/url-threat-protection-report-url-click-protection-action-view.png" alt-text="طريقة العرض وهي إجراء الحماية من النقر فوق URL في تقرير حماية عنوان URL" lightbox="../../media/url-threat-protection-report-url-click-protection-action-view.png":::

تعرض طريقة **عرض الإجراء "عرض البيانات حسب عنوان URL للحماية** " عدد نقرات URL التي يقوم بها المستخدمون في المؤسسة ونتائج النقر:

- **مسموح به**: النقرات مسموح بها.
- **مسموح به من قبل مسؤول المستأجر**: النقرات المسموح بها في نهج الارتباطات خزينة.
- **محظور**: انقر فوق محظور.
- **محظور من قبل مسؤول المستأجر**: النقرات المحظورة في نهج الارتباطات خزينة.
- **تم حظره والنقر فوقه**: نقرات محظورة حيث ينقر المستخدمون عبر عنوان URL المحظور.
- **تم حظره من قبل مسؤول المستأجر والنقر فوقه**: قام مسؤول بحظر الارتباط، ولكن المستخدم قام بالنقر عبره.
- **تم النقر خلال الفحص**: النقر فوق المكان الذي ينقر فيه المستخدمون عبر صفحة الفحص المعلقة إلى عنوان URL.
- **الفحص المعلق**: النقر فوق عناوين URL التي تنتظر حكم الفحص.

تشير النقرة إلى أن المستخدم قد نقر عبر صفحة الحظر إلى موقع ويب الضار (يمكن للمسؤولين تعطيل النقر عبر نهج الارتباطات خزينة).

إذا نقرت فوق **عوامل التصفية**، يمكنك تعديل التقرير وجدول التفاصيل عن طريق تحديد قيمة واحدة أو أكثر من القيم التالية في القائمة المنبثقة التي تظهر:

- **التاريخ (UTC)**: **تاريخ البدء** **وتاريخ الانتهاء**
- **الإجراء**:
  - **يسمح**
  - **حظر**
  - **مسموح به من قبل مسؤول المستأجر**
  - **تم الحظر والنقر عبر**
  - **تم الحظر من قبل مسؤول المستأجر والنقر عبر**
  - **تم النقر خلال أثناء الفحص**
  - **فحص معلق**
- **المجالات**: مجالات URL المدرجة في نتائج التقرير.
- **المستلمين**

عند الانتهاء من تكوين عوامل التصفية، انقر فوق **تطبيق** **عوامل التصفية** أو **إلغاؤها** أو مسحها.

يوفر جدول التفاصيل أسفل المخطط طريقة العرض التالية في الوقت الفعلي تقريبا لجميع النقرات التي حدثت داخل المؤسسة خلال آخر 7 أيام:

- **انقر فوق الوقت**
- **User**
- **URL**
- **العمل**
- **App**

في صفحة التقرير الرئيسية، أيقونة !["إنشاء جدول".](../../media/m365-cc-sc-create-icon.png) **[إنشاء جدول،](view-email-security-reports.md#schedule-report)**![ أيقونة تقرير الطلب.](../../media/m365-cc-sc-download-icon.png) **[تقرير الطلب](view-email-security-reports.md#request-report)**، وأيقونة ![التصدير.](../../media/m365-cc-sc-download-icon.png) أزرار **[التصدير](view-email-security-reports.md#export-report)** متوفرة.

### <a name="view-data-by-url-click-by-application"></a>عرض البيانات حسب URL النقر حسب التطبيق

:::image type="content" source="../../media/url-threat-protection-report-url-click-by-application-view.png" alt-text="طريقة عرض إجراء الحماية للنقر فوق URL في تقرير حماية عنوان URL" lightbox="../../media/url-threat-protection-report-url-click-by-application-view.png":::

تعرض **طريقة عرض البيانات حسب URL التي يتم النقر فوقها حسب** طريقة عرض التطبيق عدد نقرات URL بواسطة التطبيقات التي تدعم ارتباطات خزينة:

- **عميل البريد الإلكتروني**
- **مستند Office**
- **الفرق**

إذا نقرت فوق **عوامل التصفية**، يمكنك تعديل التقرير وجدول التفاصيل عن طريق تحديد قيمة واحدة أو أكثر من القيم التالية في القائمة المنبثقة التي تظهر:

- **التاريخ (UTC)**: **تاريخ البدء** **وتاريخ الانتهاء**
- **الكشف**: التطبيقات المتوفرة من المخطط.
- **المجالات**: مجالات URL المدرجة في نتائج التقرير.
- **المستلمين**

عند الانتهاء من تكوين عوامل التصفية، انقر فوق **تطبيق** **عوامل التصفية** أو **إلغاؤها** أو مسحها.

يوفر جدول التفاصيل أسفل المخطط طريقة العرض التالية في الوقت الفعلي تقريبا لجميع النقرات التي حدثت داخل المؤسسة خلال آخر 7 أيام:

- **انقر فوق الوقت**
- **User**
- **URL**
- **العمل**
- **App**

في صفحة التقرير الرئيسية، أيقونة !["إنشاء جدول".](../../media/m365-cc-sc-create-icon.png) **[إنشاء جدول،](view-email-security-reports.md#schedule-report)**![ أيقونة تقرير الطلب.](../../media/m365-cc-sc-download-icon.png) **[تقرير الطلب](view-email-security-reports.md#request-report)**، وأيقونة ![التصدير.](../../media/m365-cc-sc-download-icon.png) أزرار **[التصدير](view-email-security-reports.md#export-report)** متوفرة.

## <a name="additional-reports-to-view"></a>تقارير إضافية لعرضها

بالإضافة إلى التقارير الموضحة في هذه المقالة، تتوفر عدة تقارير أخرى، كما هو موضح في الجدول التالي:

|تقرير|الموضوع|
|---|---|
|**المستكشف** (Microsoft Defender لـ Office 365 الخطة 2) أو **عمليات الكشف في الوقت الحقيقي** (Microsoft Defender لـ Office 365 الخطة 1)|[مستكشف التهديدات (والكشف في الوقت الحقيقي)](threat-explorer.md)|
|تقارير أمان البريد الإلكتروني التي لا تتطلب Defender لـ Office 365|[عرض تقارير أمان البريد الإلكتروني في مدخل Microsoft 365 Defender](view-email-security-reports.md)|
|تقارير تدفق البريد في مركز إدارة Exchange (EAC)|[تقارير تدفق البريد في مركز إدارة Exchange الجديد](/exchange/monitoring/mail-flow-reports/mail-flow-reports)|

أوامر cmdlets الخاصة بتقارير PowerShell:

|تقرير|الموضوع|
|---|---|
|أفضل المرسلين والمستلمين|[Get-MailTrafficSummaryReport](/powershell/module/exchange/get-mailtrafficsummaryreport)|
|أهم البرامج الضارة|[Get-MailTrafficSummaryReport](/powershell/module/exchange/get-mailtrafficsummaryreport)|
|نسبة استخدام البريد|[Get-MailTrafficATPReport](/powershell/module/exchange/get-mailtrafficatpreport) <p> [Get-MailDetailATPReport](/powershell/module/exchange/get-maildetailatpreport)|
|الارتباطات الآمنة|[Get-SafeLinksAggregateReport](/powershell/module/exchange/get-safelinksaggregatereport) <p> [Get-SafeLinksDetailReport](/powershell/module/exchange/get-safelinksdetailreport)|
|المستخدمون المخترقون|[Get-CompromisedUserAggregateReport](/powershell/module/exchange/get-compromiseduseraggregatereport) <p> [Get-CompromisedUserDetailReport](/powershell/module/exchange/get-compromiseduserdetailreport)|
|حالة تدفق البريد|[Get-MailflowStatusReport](/powershell/module/exchange/get-mailflowstatusreport)|
|المستخدمون المخادعين|[Get-SpoofMailReport](/powershell/module/exchange/get-spoofmailreport)|

## <a name="what-permissions-are-needed-to-view-the-defender-for-office-365-reports"></a>ما هي الأذونات المطلوبة لعرض تقارير Defender لـ Office 365؟

لعرض التقارير الموضحة في هذه المقالة واستخدامها، يجب أن تكون عضوا في إحدى مجموعات الأدوار التالية في مدخل Microsoft 365 Defender:

- **إدارة المؤسسة**
- **مسؤول الأمان**
- **قارئ الأمان**
- **القارئ العمومي**

لمزيد من المعلومات، راجع [الأذونات في مدخل Microsoft 365 Defender](permissions-microsoft-365-security-center.md).

**ملاحظة**: إضافة مستخدمين إلى دور Azure Active Directory المقابل في مركز مسؤولي Microsoft 365 يمنح المستخدمين الأذونات المطلوبة في مدخل Microsoft 365 Defender _والأذونات_ للميزات الأخرى في Microsoft 365. لمزيد من المعلومات، راجع [حول أدوار المسؤولين](../../admin/add-users/about-admin-roles.md).

## <a name="what-if-the-reports-arent-showing-data"></a>ماذا لو لم تعرض التقارير البيانات؟

إذا لم تتمكن من رؤية البيانات في تقارير Defender لـ Office 365، فتحقق مرة أخرى من إعداد النهج بشكل صحيح. يجب أن يكون لدى مؤسستك [نهج ارتباطات خزينة](set-up-safe-links-policies.md) [ونهج مرفقات خزينة](set-up-safe-attachments-policies.md) محددة من أجل حماية Defender لـ Office 365. راجع أيضا [الحماية من البريد العشوائي](anti-spam-protection.md) [والحماية من البرامج الضارة](anti-malware-protection.md).

## <a name="related-topics"></a>المواضيع ذات الصلة

[التقارير الذكية والرؤى في مدخل Microsoft 365 Defender](reports-and-insights-in-security-and-compliance.md)

[Azure AD الأدوار المضمنة](/azure/active-directory/roles/permissions-reference)
