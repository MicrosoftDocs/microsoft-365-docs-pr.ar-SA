---
title: إدارة Microsoft Defender لنقطة النهاية باستخدام كائنات نهج المجموعة
description: تعرف على كيفية إدارة Microsoft Defender لنقطة النهاية باستخدام كائنات نهج المجموعة
keywords: ما بعد الترحيل، والإدارة، والعمليات، والصيانة، والاستخدام، وPowerShell، Microsoft Defender لنقطة النهاية، وedr
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: deniseb
author: denisebmsft
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-scenario
ms.topic: article
ms.reviewer: chventou
ms.openlocfilehash: 6a5df2cee1230050267f926297c1b00e47fb0ec3
ms.sourcegitcommit: 35f167725bec5fd4fe131781a53d96b060cf232d
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/03/2022
ms.locfileid: "65874041"
---
# <a name="manage-microsoft-defender-for-endpoint-with-group-policy-objects"></a>إدارة Microsoft Defender لنقطة النهاية باستخدام كائنات نهج المجموعة

**ينطبق على:**
- [الخطة 1 من Microsoft Defender لنقطة النهاية](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

> [!NOTE]
> نوصي باستخدام [إدارة نقاط النهاية من Microsoft](/mem) لإدارة ميزات الحماية من التهديدات في مؤسستك للأجهزة (يشار إليها أيضا بنقاط النهاية). تتضمن إدارة نقاط النهاية [Microsoft Intune](/mem/intune/fundamentals/what-is-intune) و [Microsoft Endpoint Configuration Manager](/mem/configmgr/core/understand/introduction). **[تعرف على المزيد حول إدارة نقاط النهاية](/mem/endpoint-manager-overview)**.

يمكنك استخدام كائنات نهج المجموعة في Azure خدمات مجال Active Directory لإدارة بعض الإعدادات في Microsoft Defender لنقطة النهاية.

## <a name="configure-microsoft-defender-for-endpoint-with-group-policy-objects"></a>تكوين Microsoft Defender لنقطة النهاية باستخدام كائنات نهج المجموعة

> [!NOTE]
> إذا كنت تستخدم [حل Microsoft Defender لنقطة النهاية الموحد الجديد ل Windows Server 2012 R2 و2016](/microsoft-365/security/defender-endpoint/configure-server-endpoints#new-functionality-in-the-modern-unified-solution-for-windows-server-2012-r2-and-2016-preview)، فالرجاء التأكد من أنك تستخدم أحدث ملفات ADMX في متجرك المركزي للوصول إلى خيارات نهج Microsoft Defender لنقطة النهاية الصحيحة. الرجاء الرجوع [إلى كيفية إنشاء المخزن المركزي وإدارته للقوالب الإدارية نهج المجموعة في Windows](/troubleshoot/windows-client/group-policy/create-and-manage-central-store) وتنزيل أحدث الملفات **لاستخدامها مع Windows 10**. 

يسرد الجدول التالي المهام المختلفة التي يمكنك تنفيذها لتكوين Microsoft Defender لنقطة النهاية باستخدام كائنات نهج المجموعة.

|المهمه|الموارد لمعرفة المزيد|
|---|---|
|**إدارة الإعدادات الخاصة بكائنات المستخدم والكمبيوتر** <br/><br/> *تخصيص عناصر نهج المجموعة المضمنة، أو إنشاء كائنات نهج المجموعة مخصصة ووحدات تنظيمية لتتناسب مع احتياجاتك التنظيمية.*|[إدارة نهج المجموعة في مجال مدار خدمات مجال Active Directory Azure](/azure/active-directory-domain-services/manage-group-policy)|
|**تكوين برنامج الحماية من الفيروسات من Microsoft Defender** <br/><br/> *تكوين ميزات الحماية من الفيروسات & القدرات، بما في ذلك إعدادات النهج والاستثناءات والمعالجة والمسح الضوئي المجدول على أجهزة مؤسستك (يشار إليها أيضا بنقاط النهاية).*|[استخدام إعدادات نهج المجموعة لتكوين برنامج الحماية من الفيروسات من Microsoft Defender وإدارتها](/windows/security/threat-protection/microsoft-defender-antivirus/use-group-policy-microsoft-defender-antivirus) <br/><br/> [استخدام نهج المجموعة لتمكين الحماية المقدمة من السحابة](/windows/security/threat-protection/microsoft-defender-antivirus/enable-cloud-protection-microsoft-defender-antivirus#use-group-policy-to-enable-cloud-delivered-protection)|
|**إدارة قواعد تقليل الأجزاء المعرضة للهجوم في مؤسستك** <br/><br/> *يمكنك تخصيص قواعد تقليل الأجزاء المعرضة للهجوم عن طريق استبعاد الملفات & المجلدات، أو عن طريق إضافة نص مخصص إلى تنبيهات الإعلامات التي تظهر على أجهزة المستخدمين.*|[تخصيص قواعد تقليل الأجزاء المعرضة للهجوم باستخدام كائنات نهج المجموعة](/microsoft-365/security/defender-endpoint/attack-surface-reduction-rules-deployment-implement)|
|**إدارة إعدادات الحماية من الاستغلال** <br/><br/> *يمكنك تخصيص إعدادات الحماية من الاستغلال، واستيراد ملف تكوين، ثم استخدام نهج المجموعة لنشر ملف التكوين هذا.*|[تخصيص إعدادات الحماية من الاستغلال](/microsoft-365/security/defender-endpoint/customize-exploit-protection) <br/><br/> [استيراد تكوينات الحماية من الاستغلال وتصديرها ونشرها](/microsoft-365/security/defender-endpoint/import-export-exploit-protection-emet-xml) <br/><br/> [استخدام نهج المجموعة لتوزيع التكوين](/microsoft-365/security/defender-endpoint/import-export-exploit-protection-emet-xml#use-group-policy-to-distribute-the-configuration)|
|**تمكين Network Protection** للمساعدة في منع الموظفين من استخدام التطبيقات التي تحتوي على محتوى ضار على الإنترنت <br/><br/> *نوصي باستخدام [وضع التدقيق](/microsoft-365/security/defender-endpoint/evaluate-network-protection) في البداية لحماية الشبكة في بيئة اختبار لمعرفة التطبيقات التي سيتم حظرها قبل طرحها.*|[تشغيل حماية الشبكة باستخدام نهج المجموعة](/microsoft-365/security/defender-endpoint/enable-network-protection#group-policy)|
|**تكوين الوصول المتحكم به إلى المجلد** للحماية من برامج الفدية الضارة <br/><br/> *يشار أيضا إلى [الوصول إلى المجلدات الخاضعة](/microsoft-365/security/defender-endpoint/controlled-folders) للرقابة باسم الحماية من البرامج الضارة.*|[تمكين الوصول إلى المجلدات التي يتم التحكم فيها باستخدام نهج المجموعة](/microsoft-365/security/defender-endpoint/enable-controlled-folders#group-policy)|
|**تكوين Microsoft Defender SmartScreen** للحماية من المواقع والملفات الضارة على الإنترنت.|[تكوين إعدادات إدارة أجهزة Microsoft Defender SmartScreen نهج المجموعة والأجهزة المحمولة (MDM) باستخدام نهج المجموعة](/windows/security/threat-protection/microsoft-defender-smartscreen/microsoft-defender-smartscreen-available-settings#group-policy-settings)|
|**تكوين التشفير وBitLocker** لحماية المعلومات على أجهزة مؤسستك التي تعمل Windows|[إعدادات نهج المجموعة BitLocker](/windows/security/information-protection/bitlocker/bitlocker-group-policy-settings)|
|**تكوين حماية بيانات اعتماد Microsoft Defender** للحماية من هجمات سرقة بيانات الاعتماد|[تمكين Credential Guard لـ Windows Defender باستخدام نهج المجموعة](/windows/security/identity-protection/credential-guard/credential-guard-manage#enable-windows-defender-credential-guard-by-using-group-policy)|

## <a name="configure-your-microsoft-365-defender-portal"></a>تكوين مدخل Microsoft 365 Defender

إذا لم تكن قد فعلت ذلك بالفعل، فقم بتكوين مدخل Microsoft 365 Defender لعرض التنبيهات، وتكوين ميزات الحماية من التهديدات، وعرض معلومات مفصلة حول الوضع الأمني العام لمؤسستك. راجع [Microsoft 365 Defender](/microsoft-365/security/defender/microsoft-365-defender). يمكنك أيضا تكوين ما إذا كان يمكن للمستخدمين النهائيين رؤيتها وما هي الميزات في مدخل Microsoft 365 Defender.

- [نظرة عامة على Microsoft 365 Defender](/microsoft-365/security/defender-endpoint/use)
- [حماية نقطة النهاية: Microsoft 365 Defender](/mem/intune/protect/endpoint-protection-windows-10#microsoft-defender-security-center)

## <a name="next-steps"></a>الخطوات التالية

- [الحصول على نظرة عامة على إدارة المخاطر والثغرات الأمنية](/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt)
- [تفضل بزيارة لوحة معلومات عمليات أمان مدخل Microsoft 365 Defender](/microsoft-365/security/defender-endpoint/security-operations-dashboard)
- [إدارة Microsoft Defender لنقطة النهاية باستخدام Intune](manage-mde-post-migration-intune.md)
