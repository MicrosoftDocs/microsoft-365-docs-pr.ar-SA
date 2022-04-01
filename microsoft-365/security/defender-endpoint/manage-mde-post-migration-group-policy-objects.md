---
title: إدارة Microsoft Defender لنقطة النهاية باستخدام كائنات نهج المجموعة
description: تعرف على كيفية إدارة Microsoft Defender لنقطة النهاية باستخدام كائنات نهج المجموعة
keywords: بعد الترحيل، والإدارة، والعمليات، والصيانة، والاستخدام، و PowerShell، و Microsoft Defender ل Endpoint، وedr
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
ms.date: 11/29/2021
ms.reviewer: chventou
ms.openlocfilehash: 2155c72d7008bf3669a1908b3fd866877eb36a7c
ms.sourcegitcommit: 4c207a9bdbb6c8ba372ae37907ccefca031a49f8
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/09/2022
ms.locfileid: "63580001"
---
# <a name="manage-microsoft-defender-for-endpoint-with-group-policy-objects"></a>إدارة Microsoft Defender لنقطة النهاية باستخدام كائنات نهج المجموعة

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

> [!NOTE]
> نوصي [باستخدام إدارة نقاط النهاية من Microsoft لإدارة](/mem) ميزات الحماية من المخاطر في مؤسستك للأجهزة (يشار إليها أيضا بنقاط النهاية). إدارة نقاط النهاية [تتضمن Microsoft Intune](/mem/intune/fundamentals/what-is-intune) [Microsoft Endpoint Configuration Manager.](/mem/configmgr/core/understand/introduction) **[تعرف على المزيد حول إدارة نقاط النهاية](/mem/endpoint-manager-overview)**.

يمكنك استخدام "كائنات نهج المجموعة" في Azure Active Directory Domain Services لإدارة بعض الإعدادات في Microsoft Defender لنقطة النهاية.

## <a name="configure-microsoft-defender-for-endpoint-with-group-policy-objects"></a>تكوين Microsoft Defender لنقطة النهاية باستخدام كائنات نهج المجموعة

> [!NOTE]
> إذا كنت تستخدم حل [Microsoft Defender الجديد والموحد لنقطة النهاية ل Windows Server 2012 R2 و2016](/microsoft-365/security/defender-endpoint/configure-server-endpoints#new-functionality-in-the-modern-unified-solution-for-windows-server-2012-r2-and-2016-preview)، فالرجاء التأكد من استخدام أحدث ملفات ADMX في متجرك المركزي للوصول إلى خيارات نهج Microsoft Defender لنقطة النهاية الصحيحة. الرجاء الرجوع [إلى كيفية إنشاء](/troubleshoot/windows-client/group-policy/create-and-manage-central-store) المتجر المركزي للقالب الإدارية لنهة المجموعة وإدارته في Windows وتنزيل أحدث الملفات لاستخدامها **مع** Windows 10. 

يسرد الجدول التالي المهام المختلفة التي يمكنك تنفيذها لتكوين Microsoft Defender لنقطة النهاية باستخدام كائنات نهج المجموعة.

<br/><br/>

|مهمة|الموارد لمعرفة المزيد|
|---|---|
|**إدارة إعدادات كائنات المستخدم والكمبيوتر** <br/><br/> *يمكنك تخصيص كائنات نهج المجموعة المضمنة، أو إنشاء كائنات نهج المجموعة المخصصة ووحدات تنظيمية لتتناسب مع احتياجات المؤسسة.*|[إدارة نهج المجموعة في مجال إدارة خدمات مجال Azure Active Directory](/azure/active-directory-domain-services/manage-group-policy)|
|**تكوين برنامج الحماية من الفيروسات من Microsoft Defender** <br/><br/> *تكوين ميزات الحماية من الفيروسات &، بما في ذلك إعدادات النهج والاستثناءات وميزات المعالجة والفحص المجدول على أجهزة مؤسستك (يشار إليها أيضا بنقاط النهاية).*|[استخدم إعدادات نهج المجموعة لتكوين برنامج الحماية من الفيروسات من Microsoft Defender](/windows/security/threat-protection/microsoft-defender-antivirus/use-group-policy-microsoft-defender-antivirus) <br/><br/> [استخدام "نهج المجموعة" لتمكين الحماية التي يتم تسليمها من السحابة](/windows/security/threat-protection/microsoft-defender-antivirus/enable-cloud-protection-microsoft-defender-antivirus#use-group-policy-to-enable-cloud-delivered-protection)|
|**إدارة قواعد الحد من الهجمات على سطح الهجوم في مؤسستك** <br/><br/> *يمكنك تخصيص قواعد تقليل مساحة الهجوم باستبعاد الملفات & المجلدات، أو عن طريق إضافة نص مخصص إلى تنبيهات الإعلامات التي تظهر على أجهزة المستخدمين.*|[تخصيص قواعد الحد من سطح الهجوم باستخدام "كائنات نهج المجموعة"](/microsoft-365/security/defender-endpoint/customize-attack-surface-reduction#use-group-policy-to-exclude-files-and-folders)|
|**إدارة إعدادات الحماية من استغلال** <br/><br/> *يمكنك تخصيص إعدادات الحماية من استغلالك، واستيراد ملف تكوين، ثم استخدام "نهج المجموعة" لنشر ملف التكوين هذا.*|[تخصيص إعدادات الحماية من استغلال](/microsoft-365/security/defender-endpoint/customize-exploit-protection) <br/><br/> [استيراد تكوينات الحماية من استغلال استغلال وتصديرها ونشرها](/microsoft-365/security/defender-endpoint/import-export-exploit-protection-emet-xml) <br/><br/> [استخدام "نهج المجموعة" لتوزيع التكوين](/microsoft-365/security/defender-endpoint/import-export-exploit-protection-emet-xml#use-group-policy-to-distribute-the-configuration)|
|**تمكين حماية الشبكة** للمساعدة في منع الموظفين من استخدام التطبيقات التي محتوى ضار على الإنترنت <br/><br/> *نوصي باستخدام [وضع التدقيق](/microsoft-365/security/defender-endpoint/evaluate-network-protection) أولا لحماية الشبكة في بيئة اختبار لمعرفة التطبيقات التي سيتم حظرها قبل طرحها.*|[تشغيل حماية الشبكة باستخدام "نهج المجموعة"](/microsoft-365/security/defender-endpoint/enable-network-protection#group-policy)|
|**تكوين الوصول إلى المجلدات الخاضعة للتحكم** للحماية من برامج الفدية الضارة <br/><br/> *[يشار أيضا إلى الوصول](/microsoft-365/security/defender-endpoint/controlled-folders) إلى المجلدات الخاضعة للتحكم بالحماية من البرامج الضارة.*|[تمكين الوصول إلى المجلدات الخاضعة للتحكم باستخدام "نهج المجموعة"](/microsoft-365/security/defender-endpoint/enable-controlled-folders#group-policy)|
|**قم بتكوين Microsoft Defender SmartScreen** الحماية من المواقع والملفات الضارة على الإنترنت.|[تكوين Microsoft Defender SmartScreen نهج المجموعة وإدارة أجهزة المحمول (MDM) باستخدام "نهج المجموعة"](/windows/security/threat-protection/microsoft-defender-smartscreen/microsoft-defender-smartscreen-available-settings#group-policy-settings)|
|**قم بتكوين التشفير و BitLocker** لحماية المعلومات على أجهزة المؤسسة التي تعمل Windows|[إعدادات نهج مجموعة BitLocker](/windows/security/information-protection/bitlocker/bitlocker-group-policy-settings)|
|**تكوين "حماية بيانات اعتماد Microsoft Defender"** للحماية من هجمات سرقة بيانات الاعتماد|[تمكين Windows بيانات اعتماد Defender باستخدام نهج المجموعة](/windows/security/identity-protection/credential-guard/credential-guard-manage#enable-windows-defender-credential-guard-by-using-group-policy)|

## <a name="configure-your-microsoft-365-defender-portal"></a>تكوين مدخل Microsoft 365 Defender

إذا لم تكن قد فعلت ذلك بعد، ف قم بتكوين مدخل Microsoft 365 Defender لعرض التنبيهات وتكوين ميزات الحماية من المخاطر وعرض معلومات مفصلة حول الوضع الأمني العام لم مؤسستك. راجع [Microsoft 365 Defender](/microsoft-365/security/defender/microsoft-365-defender). يمكنك أيضا تكوين الميزات التي يمكن للمستخدمين رؤياها في مدخل Microsoft 365 Defender وما هي الميزات.

- [نظرة عامة على Microsoft 365 Defender](/microsoft-365/security/defender-endpoint/use)
- [حماية نقطة النهاية: Microsoft 365 Defender](/mem/intune/protect/endpoint-protection-windows-10#microsoft-defender-security-center)

## <a name="next-steps"></a>الخطوات التالية

- [احصل على نظرة عامة حول إدارة المخاطر والثغرات الأمنية](/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt)
- [زيارة لوحة Microsoft 365 Defender عمليات أمان المدخل](/microsoft-365/security/defender-endpoint/security-operations-dashboard)
- [إدارة Microsoft Defender لنقطة النهاية باستخدام Intune](manage-mde-post-migration-intune.md)
