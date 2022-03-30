---
title: قدرات متعددة الجغرافيا في OneDrive SharePoint Online
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.custom: admindeeplinkSPO
ms.collection:
- Strat_SP_gtc
- SPO_Content
- m365solution-scenario
- m365solution-spintranet
ms.localizationpriority: medium
ms.assetid: 094e86f2-9ff0-40ac-af31-28fcaba00c1d
description: قم بتوسيع Microsoft 365 الجغرافيا إلى مناطق جغرافية متعددة ذات قدرات جغرافية متعددة في OneDrive Online.
ms.openlocfilehash: 778efca6035dad05ec9bc77298b888e50f381ca1
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63576906"
---
# <a name="multi-geo-capabilities-in-onedrive-and-sharepoint-online"></a>قدرات متعددة الجغرافيا في OneDrive SharePoint Online

تمكن القدرات متعددة الجغرافيا في OneDrive SharePoint Online التحكم في الموارد المشتركة مثل مواقع فريق SharePoint Microsoft 365 علب بريد المجموعة المخزنة في موقع جغرافي محدد.

يحتوي كل مستخدم علبة بريد SharePoint وموقع ويب على موقع بيانات مفضل (PDL) يشير إلى الموقع الجغرافي حيث سيتم تخزين البيانات ذات الصلة. يمكن تخزين البيانات الشخصية الخاصة بالمستخدمين (Exchange البريد الإلكتروني OneDrive) إلى جانب أي من مجموعات Microsoft 365 أو مواقع SharePoint التي ينشئونها في الموقع الجغرافي المحدد لتلبية متطلبات الإقامة الخاصة بالبيانات. يمكنك تحديد [مسؤولي مختلفين لكل موقع جغرافي](add-a-sharepoint-geo-admin.md).

يحصل المستخدمون على تجربة سلسة عند استخدام Microsoft 365، بما في ذلك Office وتطبيقات OneDrive والبحث. راجع [تجربة المستخدم في بيئة متعددة الجغرافيا](multi-geo-user-experience.md) للحصول على التفاصيل.

## <a name="onedrive"></a>OneDrive

يمكن توفير OneDrive المستخدم أو نقله من قبل المسؤول إلى موقع القمر الصناعي [](move-onedrive-between-geo-locations.md) وفقا ل PDL الخاص بالمستخدم. بعد ذلك، يتم الاحتفاظ بالملفات الشخصية في ذلك الموقع الجغرافي، على الرغم من أنه يمكن مشاركتها مع المستخدمين في مواقع جغرافية أخرى.

## <a name="sharepoint-sites-and-groups"></a>SharePoint المواقع والمجموعات

تتوفر إدارة ميزة Multi-Geo من <a href="https://go.microsoft.com/fwlink/?linkid=2185219" target="_blank">خلال SharePoint إدارة الموقع</a>. يمكن العثور على معلومات مفصلة في [منشور المدونة المناظر](https://techcommunity.microsoft.com/t5/Office-365-Blog/Now-available-Multi-Geo-in-SharePoint-and-Office-365-Groups/ba-p/263302).

عندما ينشئ المستخدم SharePoint متصلا بالمجموعة في بيئة متعددة الجغرافيا، يتم استخدام PDL لتحديد الموقع الجغرافي حيث يتم إنشاء الموقع علبة بريد المجموعة المقترنة به. (إذا لم يتم تعيين قيمة PDL الخاصة بالمستخدم، أو تم تعيينها إلى موقع جغرافي لم يتم تكوينه كموا موقع القمر الصناعي، يتم عندئذ إنشاء الموقع علبة البريد والموقع في الموقع المركزي.)

Microsoft 365 الخدمات الأخرى غير Exchange أو OneDrive أو SharePoint أو Teams تكون متعددة الجغرافيا. ومع Microsoft 365، سيتم تكوين المجموعات التي تم إنشاؤها بواسطة هذه الخدمات باستخدام PDL الخاص بالمنشئ علبة بريد Exchange، يتم توفير SharePoint موقع المجموعة في الموقع الجغرافي المناظر. 

## <a name="managing-the-multi-geo-environment"></a>إدارة البيئة الجغرافية المتعددة

يتم إعداد بيئة متعددة الجغرافيا وإدارتها من <a href="https://go.microsoft.com/fwlink/?linkid=2185219" target="_blank">خلال SharePoint الإدارة</a>. 

![لقطة شاشة لصفحة المواقع الجغرافية في SharePoint إدارة الموقع.](../media/sharepoint-multi-geo-admin-center.png)

(تتطلب بعض الإجراءات، مثل SharePoint موقع ويب أو موقع OneDrive Microsoft PowerShell.)

## <a name="see-also"></a>راجع أيضًا

[Multi-Geo في SharePoint Microsoft 365 المجموعات](https://techcommunity.microsoft.com/t5/Office-365-Blog/Now-available-Multi-Geo-in-SharePoint-and-Office-365-Groups/ba-p/263302)

[إدارة بيئة متعددة الجغرافيا](administering-a-multi-geo-environment.md)

[SharePoint النسبية للتخزين في بيئات متعددة الجغرافيا](sharepoint-multi-geo-storage-quota.md)

[إدارة علب Exchange Online البريد في بيئة متعددة الجغرافيا](administering-exchange-online-multi-geo.md)
