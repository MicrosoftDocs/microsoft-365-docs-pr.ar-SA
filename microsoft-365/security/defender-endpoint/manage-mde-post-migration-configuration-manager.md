---
title: إدارة Microsoft Defender لنقطة النهاية باستخدام "إدارة التكوين"
description: تعرف على كيفية إدارة Microsoft Defender لنقطة النهاية باستخدام "إدارة التكوين"
keywords: بعد الترحيل، والإدارة، والعمليات، والصيانة، والاستخدام، وإدارة التكوين، و Microsoft Defender لنقطة النهاية، وedr
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
- m365initiative-defender-endpoint
ms.topic: article
ms.date: 11/29/2021
ms.reviewer: chventou
ms.openlocfilehash: 40bac47a4c22e3a8706ed4b38b479fff5d500410
ms.sourcegitcommit: 4c207a9bdbb6c8ba372ae37907ccefca031a49f8
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/09/2022
ms.locfileid: "63583756"
---
# <a name="manage-microsoft-defender-for-endpoint-with-configuration-manager"></a>إدارة Microsoft Defender لنقطة النهاية باستخدام إدارة التكوين

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)


نوصي [باستخدام إدارة نقاط النهاية من Microsoft التي](/mem) [تتضمن Microsoft Intune](/mem/intune/fundamentals/what-is-intune) (Intune) [Microsoft Endpoint Configuration Manager](/mem/configmgr/core/understand/introduction)  (إدارة التكوين) لإدارة ميزات الحماية من المخاطر في مؤسستك للأجهزة (يشار إليها أيضا بنقاط النهاية).

- [تعرف على المزيد حول إدارة نقاط النهاية](/mem/endpoint-manager-overview)
- [المشاركة في إدارة Microsoft Defender لنقطة النهاية على أجهزة Windows 10 Windows 11 باستخدام "إدارة التكوين" و"Intune"](manage-mde-post-migration-intune.md)

## <a name="configure-microsoft-defender-for-endpoint-with-configuration-manager"></a>تكوين Microsoft Defender لنقطة النهاية باستخدام "إدارة التكوين"

<br/><br/>

|مهمة|الموارد لمعرفة المزيد|
|---|---|
|**تثبيت وحدة تحكم "إدارة التكوين** " إذا لم يكن لديك بالفعل <br/><br/> *إذا لم يكن لديك بالفعل وحدة تحكم "إدارة التكوين"، فاستخدم هذه الموارد للحصول على وحدات البت وتثبيتها.*|[الحصول على وسائط التثبيت](/mem/configmgr/core/servers/deploy/install/get-install-media) <br/><br/> [تثبيت وحدة التحكم Configuration Manager](/mem/configmgr/core/servers/deploy/install/install-consoles)|
|**استخدام "إدارة التكوين" لتهيئة الأجهزة** في Microsoft Defender لنقطة النهاية <br/><br/> *إذا كانت لديك أجهزة (أو نقاط نهاية) غير مجهزه مسبقا في Microsoft Defender لنقطة النهاية، يمكنك القيام بذلك باستخدام إدارة التكوين.*|[Onboard to Microsoft Defender for Endpoint with Configuration Manager](/mem/configmgr/protect/deploy-use/defender-advanced-threat-protection#about-onboarding-to-atp-with-configuration-manager)|
|**إدارة سياسات الحماية من البرامج الضارة Windows جدار الحماية** لأجهزة الكمبيوتر العميلة (نقاط النهاية) <br/><br/> *قم بتكوين ميزات حماية نقطة النهاية، بما في ذلك Microsoft Defender لنقطة النهاية، وحماية استغلال، والتحكم في التطبيق، والحماية من البرامج الضارة، وإعدادات جدار الحماية، والمزيد.*|[إدارة التكوين: Endpoint Protection](/mem/configmgr/protect/deploy-use/endpoint-protection)|
|**اختيار أساليب لتحديث تحديثات** البرامج الضارة على أجهزة مؤسستك <br/><br/> *باستخدام Endpoint Protection في "إدارة التكوين"، يمكنك الاختيار من بين عدة أساليب لإبقاء تعريفات مكافحة البرامج الضارة م تحديثات على أجهزة مؤسستك.*|[تكوين تحديثات التعريف Endpoint Protection](/mem/configmgr/protect/deploy-use/endpoint-definition-updates) <br/><br/> [استخدام "إدارة التكوين" لتقديم تحديثات التعريف](/mem/configmgr/protect/deploy-use/endpoint-definitions-configmgr)|
|**تمكين حماية الشبكة** للمساعدة في منع الموظفين من استخدام التطبيقات التي محتوى ضار على الإنترنت <br/><br/> *نوصي باستخدام [وضع التدقيق](/microsoft-365/security/defender-endpoint/evaluate-network-protection) أولا لحماية الشبكة في بيئة اختبار لمعرفة التطبيقات التي سيتم حظرها قبل طرحها.*|[تشغيل حماية الشبكة باستخدام "إدارة التكوين"](/microsoft-365/security/defender-endpoint/enable-network-protection#microsoft-endpoint-configuration-manager)|
|**تكوين الوصول إلى المجلدات الخاضعة للتحكم** للحماية من برامج الفدية الضارة <br/><br/> *يشار أيضا إلى الوصول إلى المجلدات الخاضعة للتحكم بالحماية من البرامج الضارة.*|[حماية نقطة النهاية: الوصول إلى المجلدات الخاضعة للتحكم](/mem/intune/protect/endpoint-protection-windows-10#controlled-folder-access) <br/><br/> [تمكين الوصول المتحكم به إلى المجلدات في إدارة تكوين نقطة نهاية Microsoft](/microsoft-365/security/defender-endpoint/enable-controlled-folders#microsoft-endpoint-configuration-manager)|

## <a name="configure-your-microsoft-365-defender-portal"></a>تكوين مدخل Microsoft 365 Defender

إذا لم تكن قد فعلت ذلك بعد، ف قم بتكوين مدخل Microsoft 365 Defender لعرض التنبيهات وتكوين ميزات الحماية من المخاطر وعرض معلومات مفصلة حول الوضع الأمني العام لم مؤسستك. راجع أثناء اكتشاف الهجوم وتوقفه، تم تشغيل تنبيهات، مثل "تنبيه وصول أولي"، وظهرت في مدخل Microsoft 365 Defender[.](/microsoft-365/security/defender/microsoft-365-defender) يمكنك أيضا تكوين الميزات التي يمكن للمستخدمين رؤياها في مدخل Microsoft 365 Defender وما هي الميزات.

- [نظرة عامة على Microsoft 365 Defender](/microsoft-365/security/defender-endpoint/use)
- [حماية نقطة النهاية: Microsoft 365 Defender](/mem/intune/protect/endpoint-protection-windows-10#microsoft-defender-security-center)

## <a name="next-steps"></a>الخطوات التالية

- [احصل على نظرة عامة حول إدارة المخاطر والثغرات الأمنية](/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt)
- [زيارة لوحة Microsoft 365 Defender عمليات أمان المدخل](/microsoft-365/security/defender-endpoint/security-operations-dashboard)
- [إدارة Microsoft Defender لنقطة النهاية باستخدام Intune](manage-mde-post-migration-intune.md)
