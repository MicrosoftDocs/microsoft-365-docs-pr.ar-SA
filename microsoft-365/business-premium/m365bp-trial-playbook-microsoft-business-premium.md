---
title: دليل المبادئ التجريبي Microsoft Defender for Business Premium
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: Admin
ms.topic: conceptual
ms.collection: m365-security-compliance
ms.localizationpriority: high
ms.date: 07/19/2022
ms.prod: m365-security
search.appverid:
- MOE150
- MET150
description: تحقيق أقصى استفادة من الإصدار التجريبي Microsoft 365 Business Premium. جرب بعض من الإنتاجية الرئيسية وقدرات الأمان.
ms.openlocfilehash: fd1871d6902fa7d39a755ea8d7d857baabff2413
ms.sourcegitcommit: c1eaea74c8ffce2f9f477c9469342e88e4a70c14
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/20/2022
ms.locfileid: "66894888"
---
# <a name="trial-playbook-microsoft-business-premium"></a>دليل المبادئ التجريبي: Microsoft Business Premium

مرحبا بك في دليل المبادئ التجريبي ل Microsoft Business Premium. سيساعدك دليل المبادئ هذا على تحقيق أقصى استفادة من الإصدار التجريبي المجاني لمدة 30 يوما من خلال مواجهة كيفية زيادة Microsoft 365 Business Premium الإنتاجية والمساعدة في حماية مؤسستك بقدرات أمان متقدمة. باستخدام توصيات Microsoft، تعرف على كيفية إعداد ميزات الحماية من التهديدات، وتحليل التهديدات المكتشفة، والاستجابة للهجمات الإلكترونية.

## <a name="set-up-the-microsoft-365-business-premium-trial"></a>إعداد الإصدار التجريبي Microsoft 365 Business Premium

عند [بدء تشغيل إصدار تجريبي أو شراء Microsoft 365 Business Premium](get-microsoft-365-business-premium.md)، فإن خطوتك الأولى هي إعداد كل شيء.

> [!TIP]
> احفظ دليل المبادئ هذا في المفضلة في المستعرض. عندما تنقلك الارتباطات الموجودة في دليل المبادئ بعيدا عن هذا الموقع، ما عليك سوى العودة إلى دليل المبادئ هذا للمتابعة.

أولا، [قم بإعداد الإصدار التجريبي الخاص بك](../business-premium/m365bp-setup.md)!

بعد بدء الإصدار التجريبي وإكمال عملية الإعداد، قد يستغرق سريان التغييرات ما يصل إلى ساعتين.

تتضمن Microsoft 365 Business Premium [نهج أمان مسبقة الإعداد](/security/office-365-security/preset-security-policies.md) يمكنك استخدامها في بيئتك. تمثل هذه النهج ملف تعريف حماية أساس مناسب لمعظم المستخدمين. تتضمن الحماية القياسية ما يلي:

- [الارتباطات الآمنة](../security/office-365-security/safe-links.md) [والمرفقات الآمنة](../security/office-365-security/safe-attachments.md) ونهج [مكافحة التصيد الاحتيالي](../security/office-365-security/anti-phishing-protection.md) التي يتم تحديد نطاقها للمستأجر بأكمله أو المجموعة الفرعية للمستخدمين الذين قد تكون اخترتهم أثناء عملية إعداد الإصدار التجريبي. (اشتراكك التجريبي هو لما يصل إلى 25 مستخدما.)

- حماية تطبيقات الإنتاجية، مثل [SharePoint](/sharepoint/introduction) [وOneDrive](/onedrive/one-drive-quickstart-small-business) [وتطبيقات Office](/deployoffice/about-microsoft-365-apps) [وMicrosoft Teams](/microsoftteams/teams-overview).

## <a name="add-a-domain"></a>إضافة مجال

عند محاولة شراء Microsoft 365 Business Premium أو شرائه، يتوفر لديك خيار استخدام مجال تملكه، أو شراء مجال أثناء عملية التسجيل.

> [!NOTE]
> إذا اشتريت مجالا جديدا عند التسجيل، يتم إعداد مجالك بالكامل ويمكنك الانتقال إلى إضافة مستخدمين وتعيين التراخيص. انتقل إلى مركز الإدارة ([https://admin.microsoft.com](https://admin.microsoft.com)).

1. من قائمة مركز الإدارة، اختر **"إعداد** " لبدء تشغيل المعالج.

2. حدد **إعداد البريد الإلكتروني باستخدام مجال مخصص** ، ثم **استخدم مجالا تملكه بالفعل** مثل `contoso.com`.

3. اتبع باقي الخطوات في المعالج لإكمال العملية.

   > [!Important]
   > إذا اشتريت مجالا أثناء التسجيل، فلن ترى الخطوة **"إضافة مجال"** هنا. انتقل إلى **إضافة مستخدمين** بدلا من ذلك.

4. اتبع الخطوات الواردة في المعالج [لإنشاء سجلات DNS لدى أي موفر استضافة DNS Office 365](/microsoft-365/admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider) يتحقق من ملكيتك للمجال. إذا كنت تعرف مضيف المجال، فراجع [إضافة مجال إلى Microsoft 365](/microsoft-365/admin/setup/add-domain).

5. إذا كان موفر الاستضافة هو GoDaddy أو مضيف آخر ممكن مع اتصال المجال، فإن العملية سهلة وستتم مطالبتك تلقائيا بتسجيل الدخول والسماح ل Microsoft بالمصادقة بالنيابة عنك.

## <a name="onboard-and-protect-devices"></a>إلحاق الأجهزة وحمايتها

> [!NOTE]
> القدرة على إلحاق نقاط النهاية التي تعمل بنظام Windows Server أو Linux Server قيد المعاينة الآن! راجع [الأجهزة الملحقة Microsoft Defender for Business](../security/defender-business/mdb-onboard-devices.md).

1. انتقل إلى مدخل Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) وسجل الدخول.

2. تشغيل [معالج الإعداد](../security/defender-business/mdb-use-wizard.md).

3. [إلحاق الأجهزة](../security/defender-business/mdb-onboard-devices.md).

4. [راجع نهج الأمان الخاصة بك](../security/defender-business/mdb-configure-security-settings.md).

## <a name="use-office-apps-on-devices"></a>استخدام تطبيقات Office على الأجهزة

1. أولا، ستحتاج إلى [تثبيت Office](m365bp-install-office-apps.md).

2. انتقل إلى office.com [وسجل الدخول](https://support.microsoft.com/office/get-started-at-office-com-91a4ec74-67fe-4a84-a268-f6bdf3da1804).

3. إنشاء مستند Office، مثل [مستند Word](https://support.microsoft.com/office/basic-tasks-in-word-87b3243c-b0bf-4a29-82aa-09a681999fdc).

4. [مشاركة مستند](https://support.microsoft.com/office/share-your-documents-651e1cb9-9a51-46dc-8d32-bdb7d928eedd) مع أحد أعضاء الفريق.

## <a name="start-using-the-microsoft-365-defender-portal"></a>بدء استخدام مدخل Microsoft 365 Defender 

1. الوصول إلى مدخل Microsoft 365 Defender في [https://security.microsoft.com](https://security.microsoft.com).

2. خذ بعض الوقت للتعرف على [المدخل](../security/defender-business/mdb-get-started.md).

3. الآن، [قم بتقييم وضعك الأمني](../security/defender/microsoft-secure-score.md).

4. تعرف على [كيفية الاستجابة لحادث أمني](../security/defender-business/mdb-respond-mitigate-threats.md).

5. وأخيرا، [راجع إجراءات المعالجة](../security/defender-business/mdb-review-remediation-actions.md).

## <a name="see-also"></a>راجع أيضًا

- [&mdash; Microsoft 365 Business Premium الأمان عبر الإنترنت للشركات الصغيرة](index.md)