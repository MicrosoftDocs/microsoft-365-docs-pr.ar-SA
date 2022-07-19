---
title: تكوين حسابات الأولوية ومراجعتها في Microsoft Defender لـ Office 365
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
ms.date: 3/21/2022
audience: ITPro
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- M365-security-compliance
ms.custom: ''
description: تعرف على كيفية تحديد الأشخاص المهمين في المؤسسة وإضافة علامة حساب الأولوية لتوفير حماية إضافية لهم.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 466061562ba0ccc1a33a9fe6ca58073196f4f7e0
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/29/2022
ms.locfileid: "66857455"
---
# <a name="configure-and-review-priority-accounts-in-microsoft-defender-for-office-365"></a>تكوين حسابات الأولوية ومراجعتها في Microsoft Defender لـ Office 365

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**ينطبق على**
- [خطة 1 وخطة 2 من Microsoft Defender لـ Office 365](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

في كل مؤسسة، هناك أشخاص مهمون، مثل المديرين التنفيذيين أو القادة أو المديرين أو المستخدمين الآخرين الذين لديهم حق الوصول إلى المعلومات الحساسة أو الخاصة أو ذات الأولوية العالية. يمكنك وضع علامة على هؤلاء المستخدمين داخل Microsoft Defender لـ Office 365 كحسابات ذات أولوية، ما يسمح لفرق الأمان بتحديد أولويات تركيزهم على هؤلاء الأفراد المهمين. مع الحماية المميزة للحسابات ذات الأولوية، سيحصل المستخدمون الذين تم وضع علامة عليهم كحسابات ذات أولوية على مستوى أعلى من الحماية من التهديدات.

يتم استهداف الحسابات ذات الأولوية من قبل المهاجمين في كثير من الأحيان ويتم مهاجمتها بشكل عام بتقنيات أكثر تطورا. تركز الحماية المميزة للحسابات ذات الأولوية على مجموعة المستخدمين المحددة هذه وتوفر مستوى أعلى من الحماية باستخدام نماذج التعلم الآلي المحسنة. يوفر هذا التفريق في التعلم ومعالجة الرسائل أعلى مستوى من الحماية لهذه الحسابات ويساعد على الحفاظ على معدل إيجابي خطأ منخفض، حيث يمكن أن يكون لمعدل عال من الإيجابيات الخاطئة تأثير سلبي على هؤلاء المستخدمين.

## <a name="configure-priority-account-protection"></a>تكوين حماية حساب الأولوية

يتم تشغيل حماية حساب الأولوية بشكل افتراضي للمستخدمين الهامين المحددين مسبقا. ومع ذلك، يمكن لمسؤول الأمان في مؤسستك أيضا تشغيل حماية الحساب ذات الأولوية باتباع الخطوات التالية:

1. في مدخل Microsoft 365 Defender، <https://security.microsoft.com>انتقل إلى **حماية حساب أولوية** **التعاون** \> & البريد الإلكتروني **للإعدادات**\>. للانتقال مباشرة إلى صفحة **حماية حساب الأولوية** ، استخدم <https://security.microsoft.com/securitysettings/priorityAccountProtection>.

2. في صفحة **حماية حساب الأولوية** ، قم بتشغيل **حماية حساب الأولوية** (:::image type="icon" source="../../media/scc-toggle-on.png" border="false":::).

    > [!div class="mx-imgBorder"]
    > ![تشغيل حماية الحساب ذات الأولوية.](../../media/mdo-priority-account-protection.png)

> [!NOTE]
> لا نوصي بتعطيل حماية الحساب ذات الأولوية أو إيقاف تشغيلها.

إذا كنت تريد استخدام Exchange Online PowerShell لتشغيل حماية الحساب ذات الأولوية، فقم بالخطوات التالية:

1. [الاتصال Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) وتشغيل الأمر التالي:

   ```powershell
   Set-EmailTenantSettings -EnablePriorityAccountProtection $true
   ```

2. للتحقق من تشغيل حماية الحساب ذات الأولوية، قم بتشغيل الأمر التالي للتحقق من قيمة خاصية EnablePriorityAccountProtection:

   ```powershell
   Get-EmailTenantSettings | Format-List Identity,EnablePriorityAccountProtection
   ```

   القيمة True تعني تشغيل حماية الحساب ذات الأولوية. القيمة False تعني إيقاف تشغيل حماية حساب الأولوية.

### <a name="assign-the-priority-account-tag-to-users"></a>تعيين علامة حساب الأولوية للمستخدمين

يدعم Microsoft Defender لـ Office 365 الحسابات ذات الأولوية كعلامات يمكن استخدامها كعوامل تصفية في التنبيهات والتقارير والحوادث والمزيد.

لمزيد من المعلومات، راجع [علامات المستخدم في Microsoft Defender لـ Office 365](user-tags.md).

## <a name="review-differentiated-protection-from-priority-account-protection"></a>مراجعة الحماية المفاضلة عن حماية الحساب ذات الأولوية

تظهر تأثيرات حماية الحساب ذات الأولوية في الميزات التالية:

- [التنبيهات](alerts.md)
- [نهج التنبيه المخصصة](../../compliance/alert-policies.md#viewing-alerts)
- [مستكشف التهديدات والكشف في الوقت الحقيقي](threat-explorer.md)
- [تقرير المستخدم الذي تم اختراقه](view-email-security-reports.md#compromised-users-report)
- [صفحة كيان البريد الإلكتروني](mdo-email-entity-page.md#other-innovations)
- [تقرير حالة الحماية من التهديدات](view-email-security-reports.md#threat-protection-status-report)
- [تقرير أفضل المرسلين والمستلمين](view-email-security-reports.md#top-senders-and-recipients-report)
- [محاكاة الهجوم](attack-simulation-training.md#target-users)
- [طرق عرض الحملة](campaigns.md)
- [عمليات إرسال مسؤول والمستخدم](admin-submission.md)
- [العزل](quarantine.md)

### <a name="threat-protection-status-report"></a>تقرير حالة الحماية من التهديدات

يعد تقرير **حالة الحماية من التهديدات** طريقة عرض واحدة تجمع معلومات حول المحتوى الضار والبريد الإلكتروني الضار الذي تم اكتشافه وحظره بواسطة Microsoft Defender لـ Office 365.

لعرض التقرير، قم بالخطوات التالية:

1. في مدخل Microsoft 365 Defender، <https://security.microsoft.com>انتقل إلى **تقارير** \> **التعاون** \> & **البريد الإلكتروني & البريد الإلكتروني & البحث** \> عن **حالة الحماية من التهديدات**، ثم انقر فوق **عرض التفاصيل**. للانتقال مباشرة إلى التقرير، استخدم <https://security.microsoft.com/reports/TPSAggregateReportATP>.

2. طريقة العرض الافتراضية هي **عرض البيانات حسب النظرة العامة**. انقر فوق هذه القيمة لتغيير طريقة العرض عن طريق تحديد إحدى القيم التالية:
   - **عرض البيانات حسب التصيد الاحتيالي للبريد الإلكتروني \>**
   - **عرض البيانات حسب البرامج الضارة للبريد الإلكتروني \>**
   - **عرض البيانات بواسطة البريد الإلكتروني \> العشوائي**

3. انقر فوق ![أيقونة عامل التصفية.](../../media/m365-cc-sc-filter-icon.png) **عامل التصفية**.

4. في القائمة المنبثقة " **عوامل التصفية** " التي يتم فتحها، في المقطع " **حسابات الأولوية** "، حدد **"نعم**" أو **"لا** " أو القيمتين معا.

   ![عوامل تصفية حماية الحساب ذات الأولوية في تقرير حالة الحماية من التهديدات.](../../media/priority-account-protection-tps-report.png)

### <a name="threat-explorer"></a>مستكشف المخاطر

يساعد عامل تصفية السياق داخل مستكشف التهديدات في البحث عن رسائل البريد الإلكتروني التي شاركت فيها حماية الحساب ذات الأولوية في الكشف عن الرسالة. يسمح هذا لفرق عمليات الأمان أن تكون قادرة على رؤية القيمة التي توفرها هذه الحماية. لا يزال بإمكانك تصفية الرسائل حسب علامة حساب الأولوية للعثور على كل الرسائل لمجموعة معينة من المستخدمين.

لعرض الحماية الإضافية في مستكشف التهديدات، قم بالخطوات التالية:

1. في مدخل Microsoft 365 Defender، <https://security.microsoft.com>انتقل إلى **مستكشف** التعاون \> **& البريد الإلكتروني**. للانتقال مباشرة إلى صفحة **مستكشف المخاطر** ، استخدم <https://security.microsoft.com/threatexplorer>.

2. حدد **السياق** من القائمة المنسدلة، ثم حدد خانة الاختيار الموجودة بجانب **حماية حساب الأولوية**.

> [!div class="mx-imgBorder"]
> ![عامل تصفية السياق داخل مستكشف المخاطر.](../../media/threat-explorer-context-filter.png)

### <a name="email-entity-page"></a>صفحة كيان البريد الإلكتروني

تتوفر صفحة كيان البريد الإلكتروني في **مستكشف التهديدات**. حدد موضوع رسالة بريد إلكتروني تقوم بالتحقيق فيها. سيتم عرض شريط ذهبي في أعلى القائمة المنبثقة للبريد الإلكتروني لهذا البريد. حدد لعرض الصفحة الجديدة.

ستسمح لك علامات التبويب على طول الجزء العلوي من صفحة الكيان بالتحقق من البريد الإلكتروني بكفاءة. انقر فوق علامة التبويب **"تحليل** ". يتم الآن إدراج حماية الحساب ذات الأولوية ضمن **تفاصيل الكشف عن التهديدات**.

## <a name="more-information"></a>معلومات إضافية

- [علامات المستخدم في Microsoft Defender لـ Office 365](user-tags.md)
- [إدارة الحسابات ذات الأولوية ومراقبتها](../../admin/setup/priority-accounts.md)
