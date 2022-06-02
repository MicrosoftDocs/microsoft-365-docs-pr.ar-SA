---
title: الاتصال Microsoft Defender لـ Office 365 إلى Microsoft Sentinel
description: خطوات الاتصال Microsoft Defender لـ Office 365 ب Sentinel. أضف بيانات Microsoft Defender لـ Office 365 (*والبيانات* من بقية مجموعة Microsoft 365 Defender)، بما في ذلك الحوادث، إلى Microsoft Sentinel للحصول على جزء واحد من الزجاج في الأمان الخاص بك.
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
ms.topic: article
ms.technology: mdo
ms.openlocfilehash: ffd954e3bffb7d1781db5b7d0b4819f47aeede39
ms.sourcegitcommit: 7ab324551afac4fd82abc015247371ebfe6ccac2
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/02/2022
ms.locfileid: "65842357"
---
# <a name="connect-microsoft-defender-for-office-365-to-microsoft-sentinel"></a>الاتصال Microsoft Defender لـ Office 365 إلى Microsoft Sentinel

يمكنك استيعاب بياناتك Microsoft Defender لـ Office 365 (*والبيانات* من بقية مجموعة Microsoft 365 Defender)، بما في ذلك الحوادث، في Microsoft Sentinel.

استفد من إدارة أحداث معلومات الأمان الغنية (SIEM) جنبا إلى جنب مع البيانات من مصادر Microsoft 365 الأخرى، ومزامنة الحوادث والتنبيهات، والتتبع المتقدم.

> [!IMPORTANT]
> موصل Microsoft 365 Defender موجود حاليا في **PREVIEW**. راجع شروط الاستخدام التكميلية لمعاينات Microsoft Azure للحصول على شروط قانونية إضافية تنطبق على ميزات Azure الموجودة في الإصدار بيتا أو المعاينة أو غير ذلك التي لم يتم إصدارها بعد في التوفر العام.>

## <a name="what-you-will-need"></a>ما ستحتاج إليه
- Microsoft Defender لـ Office 365 الخطة 2 أو الأحدث.
- [دليل التشغيل السريع](/azure/sentinel/quickstart-onboard) ل Microsoft Sentinel.
- أذونات كافية (مسؤول الأمان في M365 & أذونات القراءة /الكتابة في Sentinel).

## <a name="add-the-microsoft-365-defender-connector"></a>إضافة موصل Microsoft 365 Defender
1. [سجل الدخول إلى مدخل Microsoft Azure](https://portal.azure.com) وانتقل إلى **Microsoft Sentinel** > اختر مساحة العمل ذات الصلة للتداخل مع Microsoft 365 Defender
    1. في قائمة التنقل اليسرى أسفل العنوان **"تكوين"** > اختر **موصلات البيانات**.
2. عند تحميل الصفحة، **ابحث عن** Microsoft 365 Defender **وحدد موصل Microsoft 365 Defender (معاينة**).
3. في القائمة المنبثقة للنشرة اليمنى، حدد **"فتح صفحة الموصل**".
4. ضمن قسم **التكوين** في الصفحة التي يتم تحميلها، حدد **الاتصال الحوادث & التنبيهات**، مما يؤدي إلى إيقاف تشغيل كافة قواعد إنشاء الحوادث في Microsoft لهذه المنتجات.
5. قم بالتمرير إلى **Microsoft Defender لـ Office 365** في قسم **أحداث الاتصال** من الصفحة. حدد **EmailEvents و EmailUrlInfo و EmailAttachmentInfo & EmailPostDeliveryEvents** ثم  **قم بتطبيق التغييرات** في أسفل الصفحة. (اختر جداول من منتجات Defender الأخرى إذا كانت مفيدة وقابلة للتطبيق، أثناء هذه الخطوة.)

## <a name="next-steps"></a>الخطوات التالية

سيتمكن المسؤولون الآن من رؤية الحوادث والتنبيهات والبيانات الأولية في Microsoft Sentinel واستخدام هذه البيانات *للتتبع المتقدم*، مع التركيز على البيانات الموجودة والجديدة من Microsoft Defender.

## <a name="more-information"></a>مزيد من المعلومات

[الاتصال Microsoft 365 Defender البيانات إلى microsoft Sentinel | Microsoft Docs](/azure/sentinel/connect-microsoft-365-defender?tabs=MDE)

[الاتصال Microsoft Teams إلى Microsoft Sentinel](/microsoftteams/teams-sentinel-guide)
