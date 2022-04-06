---
title: خزينة المرفقات SharePoint OneDrive و Microsoft Teams
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: Admin
ms.date: ''
ms.topic: conceptual
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: 26261670-db33-4c53-b125-af0662c34607
ms.collection:
- M365-security-compliance
- SPO_Content
- m365initiative-defender-office365
ms.custom:
- seo-marvel-apr2020
- seo-marvel-jun2020
description: تعرف على Microsoft Defender لـ Office 365 الملفات في SharePoint عبر OneDrive for Business و Microsoft Teams.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 220bb976ebe701e5db5f03370a1a7c188f197cb1
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/25/2022
ms.locfileid: "64475752"
---
# <a name="safe-attachments-for-sharepoint-onedrive-and-microsoft-teams"></a>خزينة المرفقات SharePoint OneDrive و Microsoft Teams

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**ينطبق على**
- [Microsoft Defender لـ Office 365 الخطة 1 الخطة 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

خزينة مرفقات SharePoint و OneDrive و Microsoft Teams في [Microsoft Defender لـ Office 365](whats-new-in-defender-for-office-365.md) طبقة إضافية من الحماية للملفات التي تم فحصها مسبقا بشكل غير متزامن بواسطة مشغل الكشف عن الفيروسات الشائع [في Microsoft 365](virus-detection-in-spo.md). خزينة المرفقات SharePoint OneDrive و Microsoft Teams على الكشف عن الملفات الموجودة التي تم تعريفها كضارة في مواقع الفريق ومكتبات المستندات وحظرها.

خزينة تكون SharePoint OneDrive والزحام Microsoft Teams يتم تمكينها بشكل افتراضي. ول تشغيلها، راجع تشغيل [خزينة المرفقات](turn-on-mdo-for-spo-odb-and-teams.md) SharePoint OneDrive Microsoft Teams.

## <a name="how-safe-attachments-for-sharepoint-onedrive-and-microsoft-teams-works"></a>كيفية خزينة المرفقات SharePoint OneDrive Microsoft Teams المرفقات

عند خزينة مرفقات SharePoint و OneDrive و Microsoft Teams وتحديد ملف كضار، يتم تأمين الملف باستخدام التكامل المباشر مع مخازن الملفات. تعرض الصورة التالية مثالا لملف ضار تم اكتشافه في مكتبة.

:::image type="content" source="../../media/2bba71cc-7ad1-4799-8b9d-d56f923db3a7.png" alt-text="الملفات الموجودة في OneDrive for Business بها ملف تم الكشف عنها كضارة" lightbox="../../media/2bba71cc-7ad1-4799-8b9d-d56f923db3a7.png":::

على الرغم من أن الملف المحظور لا يزال مدرجا في مكتبة المستندات وفي تطبيقات الويب أو الأجهزة المحمولة أو سطح المكتب، لا يمكن للأشخاص فتح الملف أو نسخه أو نقله أو مشاركته. ولكن يمكنهم حذف الملف المحظور.

فيما يلي مثال على شكل ملف تم حظره على جهاز محمول:

:::image type="content" source="../../media/cb1c1705-fd0a-45b8-9a26-c22503011d54.png" alt-text="خيار حذف ملف تم حظره من OneDrive for Business من تطبيق OneDrive المحمول" lightbox="../../media/cb1c1705-fd0a-45b8-9a26-c22503011d54.png":::

بشكل افتراضي، يمكن للأشخاص تنزيل ملف تم حظره. إليك كيف يبدو تنزيل ملف تم حظره على جهاز محمول:

:::image type="content" source="../../media/be288a82-bdd8-4371-93d8-1783db3b61bc.png" alt-text="خيار تنزيل ملف تم حظره في OneDrive for Business" lightbox="../../media/be288a82-bdd8-4371-93d8-1783db3b61bc.png":::

SharePoint يمكن للمسؤولين عبر الإنترنت منع الأشخاص من تنزيل الملفات الضارة. للحصول على الإرشادات، راجع [استخدام SharePoint Online PowerShell لمنع المستخدمين من تنزيل ملفات ضارة](turn-on-mdo-for-spo-odb-and-teams.md#step-2-recommended-use-sharepoint-online-powershell-to-prevent-users-from-downloading-malicious-files).

لمعرفة المزيد حول تجربة المستخدم عند اكتشاف وجود ملف كضار، راجع ما يجب فعله عند العثور على ملف ضار في SharePoint Online أو OneDrive أو [Microsoft Teams](https://support.microsoft.com/office/01e902ad-a903-4e0f-b093-1e1ac0c37ad2).

## <a name="view-information-about-malicious-files-detected-by-safe-attachments-for-sharepoint-onedrive-and-microsoft-teams"></a>عرض معلومات حول الملفات الضارة التي تم اكتشافها بواسطة خزينة لمرفقات SharePoint OneDrive Microsoft Teams

سوف تظهر الملفات التي تم تعريفها على أنها ضارة بواسطة مرفقات خزينة ل SharePoint و OneDrive و Microsoft Teams في تقارير ل [Microsoft Defender لـ Office 365](view-reports-for-mdo.md) وفي المستكشف (والكشف في الوقت الحقيقي[).](threat-explorer.md).

عندما يتم تعريف الملف على أنه ضار بواسطة خزينة مرفقات SharePoint و OneDrive و Microsoft Teams، يتوفر الملف أيضا في الفحص، ولكن للمسؤولين فقط. لمزيد من المعلومات، راجع [إدارة الملفات المعزولة في Defender لـ Office 365](manage-quarantined-messages-and-files.md#use-the-microsoft-365-defender-portal-to-manage-quarantined-files-in-defender-for-office-365).

## <a name="keep-these-points-in-mind"></a>ضع هذه النقاط في الاعتبار

- Defender لـ Office 365 إجراء مسح ضوئي لكل ملف في SharePoint أو OneDrive for Business أو Microsoft Teams. يتم ذلك حسب التصميم. يتم فحص الملفات بشكل غير متزامن. تستخدم العملية أحداث نشاط الضيف والمشاركة إلى جانب مؤشرات الإحصاء الذكية وإشارات التهديدات لتحديد الملفات الضارة.

- تأكد من SharePoint تكوين مواقعك لاستخدام التجربة [الحديثة](/sharepoint/guide-to-sharepoint-modern-experience). Defender لـ Office 365 حماية الملفات سواء تم استخدام التجربة الحديثة أو طريقة العرض الكلاسيكية؛ ومع ذلك، تتوفر المؤشرات المرئية التي يتم حظر ملف في التجربة الحديثة فقط.

- خزينة المرفقات ل SharePoint و OneDrive و Microsoft Teams جزءا من استراتيجية الحماية الشاملة من المخاطر في مؤسستك، التي تتضمن الحماية من البريد العشوائي والحماية من البرامج الضارة في Exchange Online Protection (EOP) بالإضافة إلى خزينة الارتباطات خزينة المرفقات في Microsoft Defender لـ Office 365. لمعرفة المزيد، راجع [الحماية من التهديدات في](protect-against-threats.md) Office 365.
