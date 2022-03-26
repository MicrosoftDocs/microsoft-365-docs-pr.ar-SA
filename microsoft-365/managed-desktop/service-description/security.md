---
title: تقنيات الأمان في Microsoft Managed Desktop
description: التقنيات المستخدمة لإدارة أمان الجهاز وهويته والوصول إليه، والأمان على الشبكة، والأمان المعلومات
keywords: سطح المكتب المدار من Microsoft، Microsoft 365، الخدمة، الوثائق
ms.service: m365-md
author: tiaraquan
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.openlocfilehash: 4a6eb73a172ecfb680cbc48367851e40b1a54401
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63566079"
---
# <a name="security-technologies-in-microsoft-managed-desktop"></a>تقنيات الأمان في Microsoft Managed Desktop

<!--Security, also Onboarding doc: data handling/store, privileged account access -->

يستخدم Microsoft Managed Desktop العديد من تقنيات Microsoft للمساعدة على تأمين الأجهزة والبيانات المدارة. بالإضافة إلى ذلك، يستخدم مركز عمليات أمان سطح المكتب المدار من Microsoft [عمليات متنوعة](security-operations.md) مع هذه التقنيات. بشكل خاص:

| معالجة | الوصف |
| ------ | ------ |
| [أمان الجهاز](#device-security)| الأمان والحماية على أجهزة سطح المكتب المدارة من Microsoft. |
| [إدارة الهوية والوصول](#identity-and-access-management) | إدارة الاستخدام الآمن للأجهزة من خلال خدمات هوية Azure Active Directory. |
| [أمان الشبكة](#network-security)| معلومات VPN والحلول والإعدادات المستحسنة لسطح المكتب المدار من Microsoft. |
| [أمان المعلومات](#information-security)| الخدمات المتوفرة الاختيارية لحماية المعلومات الحساسة بشكل أكبر. |

للحصول على معلومات حول تخزين البيانات واستخدامها وممارسات الأمان المستخدمة بواسطة Microsoft Managed Desktop، راجع تطبيقنا على [https://aka.ms/mmd-data](https://aka.ms/mmd-data).

## <a name="device-security"></a>أمان الجهاز

يضمن Microsoft Managed Desktop أن جميع الأجهزة المدارة مؤمنة ومحمية، ويكشف عن التهديدات في أقرب وقت ممكن باستخدام الخدمات التالية:

| الخدمة | الوصف |
| ----- | ----- |
| برنامج الحماية من الفيروسات | برنامج الحماية من الفيروسات من Microsoft Defender تثبيته وتكوينه<br>برنامج الحماية من الفيروسات من Microsoft Defender التعريفات م تاريخا. |
| تشفير كامل الحجم | Windows BitLocker هو حل التشفير الحجمي لأجهزة سطح المكتب المدارة من Microsoft.<br><br>بمجرد تسجيل مؤسسة في الخدمة، سيتم تشفير الأجهزة باستخدام Windows BitLocker مع وحدة نمطية مضمنة من النظام الأساسي للثقة (TPM) لمنع الوصول غير المصرح به إلى البيانات المحلية عندما يكون الجهاز في وضع السكون، أو إيقاف تشغيله.
| المراقبة | يتم استخدام Microsoft Defender ل Endpoint لمراقبة التهديدات الأمنية عبر جميع أجهزة سطح المكتب المدارة من Microsoft. يسمح Defender for Endpoint لعملاء المؤسسات بالكشف عن التهديدات المتقدمة في شبكة الشركة الخاصة بهم، والكشف عنها، والاستجابة لها. لمزيد من المعلومات، راجع [Microsoft Defender لنقطة النهاية.](/windows/threat-protection/windows-defender-atp/windows-defender-advanced-threat-protection) |
| تحديثات نظام التشغيل | يتم دائما تأمين أجهزة سطح المكتب المدارة من Microsoft باستخدام آخر تحديثات الأمان. |
| تأمين تكوين الجهاز | ينفذ Microsoft Managed Desktop خط أساسي أمان Microsoft. لمزيد من المعلومات، [راجع Windows الأمان الأساسية.](/windows/security/threat-protection/windows-security-baselines)|

## <a name="identity-and-access-management"></a>إدارة الهوية والوصول

تحمي إدارة الهوية والوصول أصول الشركة وبيانات الأعمال الهامة. تقوم Microsoft Managed Desktop بتكوين الأجهزة لضمان الاستخدام الآمن مع الهويات المدارة في Azure Active Directory (Azure AD). تقع على عاتق العميل مسؤولية الاحتفاظ بمعلومات دقيقة في مستأجر Azure AD.

| الخدمة | الوصف |
| ----- | ----- |
| مصادقة المقاييس الحيوية | Windows Hello المستخدمين تسجيل الدخول باستخدام وجههم أو رمز PIN، مما يجعل نسيان كلمات المرور أو سرقتها أكثر صعوبة. يتحمل العملاء مسؤولية تنفيذ المتطلبات الأساسية الضرورية ل Active Directory الخاص بهم في الموقع لاستخدام هذه الخدمة في تكوين مختلط. لمزيد من المعلومات، راجع Windows Hello[.](/windows-hardware/design/device-experiences/windows-hello) |
| إذن المستخدم القياسي | لحماية النظام وجعله أكثر أمانا، سيتم تعيين أذونات مستخدم قياسية للمستخدم. يتم تعيين هذا الإذن كجزء من تجربة Windows Autopilot خارج الصندوق.

## <a name="network-security"></a>أمان الشبكة

يتحمل العملاء مسؤولية أمان الشبكة.

| الخدمة | الوصف |
| ----- | ----- |
| VPN | يمتلك العملاء البنية الأساسية ل VPN الخاصة بهم، لضمان عرض موارد محدودة للشركات خارج الإنترانت.<br><br>الحد الأدنى للمتطلبات: يتطلب Microsoft Managed Desktop Windows 10 VPN متوافق ومدعم. إذا كانت مؤسستك بحاجة إلى حل VPN، فهي تحتاج إلى Windows 10 وحزمها ونشرها من خلال Intune. اتصل بناشر البرنامج للحصول على مزيد من المعلومات.<br><br>توصية:<br><ul><li> توصي Microsoft باستخدام حل VPN حديث يمكن نشره بسهولة من خلال Intune لدفع ملفات تعريف VPN. يوفر هذا النهج طريقة سهلة وموثوقة وآمنة دائما للوصول إلى شبكة الشركة. لمزيد من المعلومات، راجع [إعدادات VPN في Intune](/intune/vpn-settings-configure).</li><li>لا توصي Microsoft بإجراء عملاء VPN السميكين أو عملاء VPN الأقدم أثناء استخدام Microsoft Managed Desktop حيث يمكن أن يؤثر ذلك على بيئة المستخدم.</li><li>توصي Microsoft بأن يتم توجيه حركة مرور الويب الصادرة مباشرة إلى الإنترنت دون المرور عبر VPN لتجنب أي مشاكل في الأداء.</li><li>وبشكل مثالي، توصي Microsoft باستخدام وكيل تطبيق Azure Active Directory بدلا من VPN.</li></ul>

## <a name="information-security"></a>أمان المعلومات

يمكنك تكوين هذه الخدمات الاختيارية للمساعدة في حماية الأصول ذات القيمة العالية للشركات.

| الخدمة | الوصف |
| ----- | ----- |
| استرداد البيانات | المعلومات المخزنة في المجلدات الرئيسية على الجهاز يتم إنشاء OneDrive for Business. سطح المكتب المدار من Microsoft غير مسؤول عن البيانات غير المتزامنة مع OneDrive for Business.
| Windows حماية المعلومات | بالنسبة للشركات التي تتطلب مستويات عالية من أمان المعلومات، نوصي Windows [حماية](/windows/threat-protection/windows-information-protection/protect-enterprise-data-using-wip) المعلومات و [Azure Information Protection.](https://www.microsoft.com/cloud-platform/azure-information-protection)
