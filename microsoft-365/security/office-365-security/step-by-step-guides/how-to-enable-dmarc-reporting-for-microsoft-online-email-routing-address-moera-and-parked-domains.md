---
title: كيفية تمكين DMARC Reporting لعنوان توجيه البريد الإلكتروني ل Microsoft Online (MOERA) والمجالات التي تم إيقافها
description: خطوات تكوين DMARC ل MOERA والمجالات المتوقفة.
search.product: ''
search.appverid: ''
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-guidance-templates
ms.topic: how-to
ms.technology: mdo
ms.openlocfilehash: dbe994ee0cba90f37acf7dcbd92c3b0d81d673a3
ms.sourcegitcommit: a209c9f86a7b4340a426c4cfed2d36a388c71124
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/15/2022
ms.locfileid: "66857571"
---
# <a name="how-to-enable-dmarc-reporting-for-microsoft-online-email-routing-address-moera-and-parked-domains"></a>كيفية تمكين DMARC Reporting لعنوان توجيه البريد الإلكتروني ل Microsoft Online (MOERA) والمجالات التي تم إيقافها

تتمثل أفضل الممارسات لحماية أمان البريد الإلكتروني للمجال في حماية نفسك من الانتحال باستخدام مصادقة الرسائل وإعداد التقارير والمطابقة المستندة إلى المجال (DMARC). إذا لم تقم بالفعل بتمكين DMARC لمجالاتك، فيجب أن تكون هذه هي الخطوة الأولى، المفصلة هنا: [مصادقة الرسائل المستندة إلى المجال وإعداد التقارير والتوافق (DMARC)](/microsoft-365/security/office-365-security/use-dmarc-to-validate-email)

تم تصميم هذا الدليل لمساعدتك على تكوين DMARC للمجالات غير المغطاة في الدليل أعلاه، ويعرف أيضا باسم عنوان توجيه البريد الإلكتروني (MOERA) ل Microsoft Online contosocorp.onmicrosoft.com والمجالات التي قد لا تستخدمها للبريد الإلكتروني حتى الآن، ولكن يمكن للمهاجمين الاستفادة منها حتى تتم حمايتها.

## <a name="what-youll-need"></a>ما ستحتاج إليه

- مركز مسؤولي Microsoft 365 والوصول إلى موفر DNS الذي يستضيف مجالاتك
- أذونات كافية مسؤول عمومية لإجراء التغييرات المناسبة في مركز مسؤول Microsoft 365
- 10 دقائق لإكمال الخطوات التالية

## <a name="activate-dmarc-for-moera-domain"></a>تنشيط DMARC لمجال MOERA

1. تسجيل الدخول إلى [مركز مسؤول Microsoft 365](https://admin.microsoft.com).
1. في شريط التنقل الأيسر، حدد **"إظهار الكل**".
1. قم بتوسيع الإعدادات واضغط **على المجالات**.
1. حدد مجال المستأجر (contoso.onmicrosoft.com).
1. في الصفحة التي يتم تحميلها، حدد **سجلات DNS**.
1. حدد **+ إضافة سجل**.
1. ستظهر قائمة منبثقة على اليمين، تأكد من أن النوع المحدد هو **TXT (نص).**
1. إضافة _dmarc كاسم TXT.
1. أضف قيمة DMARC المحددة.
1. اضغط **على Save**.

## <a name="active-dmarc-for-parked-domains"></a>DMARC نشط للمجالات التي تم إيقافها

1. تحقق مما إذا كان SPF قد تم تكوينه بالفعل لمجالك الذي تم إيقافه، باتباع هذا الدليل: [إعداد SPF للمساعدة في منع الانتحال - Office 365 | Microsoftova dokumentacija](/microsoft-365/security/office-365-security/set-up-spf-in-office-365-to-help-prevent-spoofing#how-to-handle-subdomains)
1. اتصل بموفر مجال DNS.
1. اطلب إضافة سجل DMARC txt هذا مع عناوين `v=DMARC1; p=reject; rua=mailto:d@rua.contoso.com;ruf=mailto:d@ruf.contoso.com`البريد الإلكتروني المناسبة.

## <a name="next-steps"></a>الخطوات التالية

انتظر حتى يتم نشر تغييرات DNS وحاول تزييف المجالات التي تم تكوينها. تحقق مما إذا كانت المحاولة محظورة استنادا إلى سجل DMARC، وتتلقى تقرير DMARC.

## <a name="more-information"></a>مزيد من المعلومات

[إعداد SPF للمساعدة في منع تزييف هوية - Office 365 | ](/microsoft-365/security/office-365-security/set-up-spf-in-office-365-to-help-prevent-spoofing)
 Microsoftova dokumentacija [استخدام DMARC للتحقق من صحة البريد الإلكتروني، خطوات الإعداد - Office 365 | Microsoftova dokumentacija](/microsoft-365/security/office-365-security/use-dmarc-to-validate-email)
