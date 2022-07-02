---
title: إدارة Microsoft Defender لنقطة النهاية باستخدام Configuration Manager
description: تعرف على كيفية إدارة Microsoft Defender لنقطة النهاية باستخدام Configuration Manager
keywords: بعد الترحيل، والإدارة، والعمليات، والصيانة، والاستخدام، Configuration Manager، Microsoft Defender لنقطة النهاية، edr
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
- m365initiative-defender-endpoint
ms.topic: article
ms.date: 07/01/2022
ms.reviewer: chventou
ms.openlocfilehash: b253fe7dad271684f5c0e927ec162ea4e993df29
ms.sourcegitcommit: bfbe2574f487ced69e711b48ce140120bd99181b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/02/2022
ms.locfileid: "66607378"
---
# <a name="manage-microsoft-defender-for-endpoint-with-configuration-manager"></a>إدارة Microsoft Defender لنقطة النهاية باستخدام Configuration Manager

**ينطبق على:**
- [الخطة 1 من Microsoft Defender لنقطة النهاية](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

نوصي باستخدام [Microsoft إدارة نقاط النهاية](/mem)، والتي تتضمن [Microsoft Intune](/mem/intune/fundamentals/what-is-intune) (Intune) ونقطة [النهاية من Microsoft Configuration Manager](/mem/configmgr/core/understand/introduction) (Configuration Manager ) لإدارة ميزات الحماية من التهديدات في مؤسستك للأجهزة (يشار إليها أيضا بنقاط النهاية).

- [تعرف على المزيد حول إدارة نقاط النهاية](/mem/endpoint-manager-overview)
- [المشاركة في إدارة Microsoft Defender لنقطة النهاية على أجهزة Windows 10 وأجهزة Windows 11 باستخدام Configuration Manager وIntune](manage-mde-post-migration-intune.md)

## <a name="configure-microsoft-defender-for-endpoint-with-configuration-manager"></a>تكوين Microsoft Defender لنقطة النهاية باستخدام Configuration Manager

|المهمه|الموارد لمعرفة المزيد|
|---|---|
|**تثبيت وحدة التحكم Configuration Manager** إذا لم يكن لديك بالفعل <br/><br/> *إذا لم يكن لديك بالفعل وحدة تحكم Configuration Manger، فاستخدم هذه الموارد للحصول على وحدات البت وتثبيتها.*|[الحصول على وسائط التثبيت](/mem/configmgr/core/servers/deploy/install/get-install-media) <br/><br/> [تثبيت وحدة التحكم Configuration Manager](/mem/configmgr/core/servers/deploy/install/install-consoles)|
|**استخدام Configuration Manager لإلحاق الأجهزة** Microsoft Defender لنقطة النهاية <br/><br/> *إذا كانت لديك أجهزة (أو نقاط نهاية) لم يتم إلحاقها بالفعل Microsoft Defender لنقطة النهاية، يمكنك القيام بذلك باستخدام Configuration Manager.*|[إلحاق Microsoft Defender لنقطة النهاية باستخدام Configuration Manager](/mem/configmgr/protect/deploy-use/defender-advanced-threat-protection#about-onboarding-to-atp-with-configuration-manager)|
|**إدارة نهج مكافحة البرامج الضارة وأمان جدار حماية Windows** لأجهزة الكمبيوتر العميلة (نقاط النهاية) <br/><br/> *تكوين ميزات حماية نقطة النهاية، بما في ذلك Microsoft Defender لنقطة النهاية وحماية الاستغلال والتحكم في التطبيق ومكافحة البرامج الضارة وإعدادات جدار الحماية والمزيد.*|[Configuration Manager: Endpoint Protection](/mem/configmgr/protect/deploy-use/endpoint-protection)|
|**اختيار أساليب لتحديث تحديثات مكافحة البرامج الضارة** على أجهزة مؤسستك <br/><br/> *باستخدام Endpoint Protection في Configuration Manager، يمكنك الاختيار من بين عدة طرق لإبقاء تعريفات مكافحة البرامج الضارة محدثة على أجهزة مؤسستك.*|[تكوين تحديثات التعريف لحماية نقطة النهاية](/mem/configmgr/protect/deploy-use/endpoint-definition-updates) <br/><br/> [استخدام Configuration Manager لتقديم تحديثات التعريف](/mem/configmgr/protect/deploy-use/endpoint-definitions-configmgr)|
|**تمكين Network Protection** للمساعدة في منع الموظفين من استخدام التطبيقات التي تحتوي على محتوى ضار على الإنترنت <br/><br/> *نوصي باستخدام [وضع التدقيق](/microsoft-365/security/defender-endpoint/evaluate-network-protection) في البداية لحماية الشبكة في بيئة اختبار لمعرفة التطبيقات التي سيتم حظرها قبل طرحها.*|[تشغيل حماية الشبكة باستخدام Configuration Manager](/microsoft-365/security/defender-endpoint/enable-network-protection#microsoft-endpoint-configuration-manager)|
|**تكوين الوصول المتحكم به إلى المجلد** للحماية من برامج الفدية الضارة <br/><br/> *يشار أيضا إلى الوصول إلى المجلدات الخاضعة للرقابة باسم الحماية من البرامج الضارة.*|[حماية نقطة النهاية: الوصول المتحكم به إلى المجلد](/mem/intune/protect/endpoint-protection-windows-10#controlled-folder-access) <br/><br/> [تمكين الوصول المتحكم به إلى المجلد في إدارة تكوين نقطة النهاية من Microsoft](/microsoft-365/security/defender-endpoint/enable-controlled-folders#microsoft-endpoint-configuration-manager)|

## <a name="configure-your-microsoft-365-defender-portal"></a>تكوين مدخل Microsoft 365 Defender

إذا لم تكن قد فعلت ذلك بالفعل، فقم بتكوين مدخل Microsoft 365 Defender لعرض التنبيهات، وتكوين ميزات الحماية من التهديدات، وعرض معلومات مفصلة حول الوضع الأمني العام لمؤسستك. راجع أثناء الكشف عن الهجوم وتوقفه، تم تشغيل تنبيهات، مثل "تنبيه وصول أولي"، وظهرت في [مدخل Microsoft 365 Defender](/microsoft-365/security/defender/microsoft-365-defender). يمكنك أيضا تكوين ما إذا كان يمكن للمستخدمين النهائيين رؤيتها وما هي الميزات في مدخل Microsoft 365 Defender.

- [نظرة عامة على Microsoft 365 Defender](/microsoft-365/security/defender-endpoint/use)
- [حماية نقطة النهاية: Microsoft 365 Defender](/mem/intune/protect/endpoint-protection-windows-10#microsoft-defender-security-center)

## <a name="next-steps"></a>الخطوات التالية

- [الحصول على نظرة عامة على إدارة المخاطر والثغرات الأمنية](/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt)
- [تفضل بزيارة لوحة معلومات عمليات أمان مدخل Microsoft 365 Defender](/microsoft-365/security/defender-endpoint/security-operations-dashboard)
- [إدارة Microsoft Defender لنقطة النهاية باستخدام Intune](manage-mde-post-migration-intune.md)
