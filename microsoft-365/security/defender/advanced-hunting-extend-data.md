---
title: توسيع تغطية الصيد المتقدمة باستخدام الإعدادات المناسبة
description: التحقق من إعدادات التدقيق Windows الأجهزة والإعدادات الأخرى للمساعدة في ضمان حصولك على البيانات الأكثر شمولية في عمليات البحث المتقدمة
keywords: الصيد المتقدم، والحادث، وال pivot، والكيانات، وإعدادات التدقيق، وإدارة حساب المستخدم، وإدارة مجموعة الأمان، وصيد التهديدات، وصيد التهديدات الإلكترونية، والبحث، والاستعلام، والتعقب، Microsoft 365، Microsoft 365 Defender
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: maccruz
author: schmurky
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-security-compliance
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: dd61fa434eaf2130f0fcb0f28df9a20d696e04ec
ms.sourcegitcommit: bf3965b46487f6f8cf900dd9a3af8b213a405989
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 11/02/2021
ms.locfileid: "63569835"
---
# <a name="extend-advanced-hunting-coverage-with-the-right-settings"></a>توسيع تغطية الصيد المتقدمة باستخدام الإعدادات المناسبة

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**ينطبق على:**
- Microsoft 365 Defender
- Microsoft Defender لنقطة النهاية

[يعتمد الصيد](advanced-hunting-overview.md) المتقدم على البيانات القادمة من مصادر مختلفة، بما في ذلك أجهزتك Office 365 العمل و Azure AD و Microsoft Defender for Identity. للحصول على البيانات الأكثر شمولية الممكنة، تأكد من وجود الإعدادات الصحيحة في مصادر البيانات المقابلة.

## <a name="advanced-security-auditing-on-windows-devices"></a>تدقيق الأمان المتقدم على Windows الأجهزة
قم تشغيل إعدادات التدقيق المتقدمة هذه لضمان حصولك على بيانات حول الأنشطة على أجهزتك، بما في ذلك إدارة الحسابات المحلية وإدارة مجموعة الأمان المحلية وإنشاء الخدمة.

| البيانات | الوصف | جدول مخطط | كيفية تكوين |
| --- | --- | --- | --- |
| إدارة الحسابات | الأحداث التي تم التقاطها كقيم `ActionType` مختلفة تشير إلى إنشاء حساب محلي وحذفه وأنشطة أخرى ذات صلة به | [DeviceEvents](advanced-hunting-deviceevents-table.md) | - نشر نهج تدقيق أمان متقدم: [تدقيق إدارة حساب المستخدم](/windows/security/threat-protection/auditing/audit-user-account-management)<br> - [التعرف على سياسات تدقيق الأمان المتقدمة](/windows/security/threat-protection/auditing/advanced-security-auditing) |
| إدارة مجموعة الأمان | الأحداث التي تم التقاطها كقيم مختلفة `ActionType` تشير إلى إنشاء مجموعة أمان محلية وأنشطة إدارة المجموعات المحلية الأخرى | [DeviceEvents](advanced-hunting-deviceevents-table.md) | - نشر نهج تدقيق أمان متقدم: [إدارة مجموعة أمان التدقيق](/windows/security/threat-protection/auditing/audit-security-group-management)<br> - [التعرف على سياسات تدقيق الأمان المتقدمة](/windows/security/threat-protection/auditing/advanced-security-auditing) |
| تثبيت الخدمة | الأحداث التي تم التقاطها مع `ActionType` القيمة `ServiceInstalled`، مما يشير إلى أنه تم إنشاء خدمة | [DeviceEvents](advanced-hunting-deviceevents-table.md) | - نشر نهج تدقيق أمان متقدم: [ملحق نظام أمان التدقيق](/windows/security/threat-protection/auditing/audit-security-system-extension)<br> - [التعرف على سياسات تدقيق الأمان المتقدمة](/windows/security/threat-protection/auditing/advanced-security-auditing) |

## <a name="microsoft-defender-for-identity-sensor-on-the-domain-controller"></a>مستشعر Microsoft Defender for Identity على وحدة التحكم بالمجال
إذا كنت تقوم بتشغيل Active Directory في الموقع، ستحتاج إلى تثبيت مستشعر Microsoft Defender for Identity على وحدة التحكم بالمجال للحصول على بيانات ل Microsoft Defender for Identity. عند تثبيت هذه البيانات وتكوينها بشكل صحيح، يتم أيضا تغذية عملية البحث المتقدمة عبر Microsoft Defender for Identity وتوفر صورة أكثر شمولية للمعلومات والأحداث المتعلقة بالهوية في شبكتك. تحسن هذه البيانات أيضا من قدرة Microsoft Defender for Identity على إنشاء تنبيهات ذات صلة تغطيها أيضا عملية البحث المتقدم. 

| البيانات | الوصف | جدول مخطط | كيفية تكوين |
| --- | --- | --- | --- |
| وحدة التحكم في المجال | البيانات من Active Directory المرسلة إلى Microsoft Defender for Identity، وإثراء المعلومات ذات الصلة بالهوية، مثل تفاصيل الحساب ونشاط تسجيل الوصول واستعلامات Active Directory | جداول متعددة، بما في [ذلك IdentityInfo](advanced-hunting-identityinfo-table.md) و [IdentityLogonEvents](advanced-hunting-identitylogonevents-table.md) و [IdentityQueryEvents](advanced-hunting-identityqueryevents-table.md)  | - [تثبيت مستشعر Microsoft Defender for Identity](/azure-advanced-threat-protection/install-atp-step4)<br>- [تشغيل الأحداث Windows ذات الصلة](/azure-advanced-threat-protection/configure-event-collection) |

>[!NOTE]
>قد لا تتوفر بعض الجداول في هذه المقالة في Microsoft Defender for Endpoint. [قم Microsoft 365 Defender](m365d-enable.md) للبحث عن التهديدات باستخدام المزيد من مصادر البيانات. يمكنك نقل مهام سير عمل الصيد المتقدمة من Microsoft Defender ل Endpoint إلى Microsoft 365 Defender باتباع الخطوات الواردة في ترحيل استعلامات الصيد المتقدمة من [Microsoft Defender ل Endpoint](advanced-hunting-migrate-from-mde.md).

## <a name="related-topics"></a>المواضيع ذات الصلة
- [نظرة عامة متقدمة حول الصيد](advanced-hunting-overview.md)
- [فهم المخطط](advanced-hunting-schema-tables.md)