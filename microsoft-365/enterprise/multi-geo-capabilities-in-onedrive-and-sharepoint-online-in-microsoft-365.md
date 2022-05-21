---
title: قدرات جغرافية متعددة في OneDrive SharePoint Online
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
description: قم بتوسيع وجودك Microsoft 365 إلى مناطق جغرافية متعددة ذات قدرات جغرافية متعددة في OneDrive Online.
ms.openlocfilehash: e49df6054e30e9e288e893da8d914ebb567eb8e5
ms.sourcegitcommit: 349f0f54b0397cdd7d8fbb9ef07f1b6654a32d6e
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/20/2022
ms.locfileid: "65622224"
---
# <a name="multi-geo-capabilities-in-onedrive-and-sharepoint-online"></a>قدرات جغرافية متعددة في OneDrive SharePoint Online

تتيح الإمكانات متعددة المناطق الجغرافية في OneDrive SharePoint Online التحكم في الموارد المشتركة مثل مواقع فرق SharePoint وعلب بريد مجموعة Microsoft 365 المخزنة في وضع السكون في موقع جغرافي محدد.

يحتوي كل مستخدم وعلبة بريد المجموعة وموقع SharePoint على موقع البيانات المفضل (PDL) الذي يشير إلى الموقع الجغرافي حيث سيتم تخزين البيانات ذات الصلة. يمكن تخزين البيانات الشخصية للمستخدمين (Exchange علبة البريد OneDrive) مع أي مواقع مجموعات Microsoft 365 أو SharePoint يقومون بإنشائها في الموقع الجغرافي المحدد لتلبية متطلبات موقع البيانات. يمكنك [تحديد مسؤولين مختلفين لكل موقع جغرافي](add-a-sharepoint-geo-admin.md).

يحصل المستخدمون على تجربة سلسة عند استخدام خدمات Microsoft 365، بما في ذلك تطبيقات Office OneDrive والبحث. راجع [تجربة المستخدم في بيئة متعددة المناطق الجغرافية](multi-geo-user-experience.md) للحصول على التفاصيل.

## <a name="onedrive"></a>OneDrive

يمكن توفير OneDrive لكل مستخدم أو [نقلها من قبل مسؤول](move-onedrive-between-geo-locations.md) إلى موقع قمر صناعي وفقا ل PDL الخاص بالمستخدم. ثم يتم الاحتفاظ بالملفات الشخصية في هذا الموقع الجغرافي، على الرغم من أنه يمكن مشاركتها مع المستخدمين في مواقع جغرافية أخرى.

## <a name="sharepoint-sites-and-groups"></a>SharePoint المواقع والمجموعات

تتوفر إدارة ميزة Multi-Geo من خلال <a href="https://go.microsoft.com/fwlink/?linkid=2185219" target="_blank">مركز إدارة SharePoint</a>. يمكن العثور على معلومات مفصلة في [منشور المدونة المقابل](https://techcommunity.microsoft.com/t5/Office-365-Blog/Now-available-Multi-Geo-in-SharePoint-and-Office-365-Groups/ba-p/263302).

عندما يقوم مستخدم بإنشاء موقع متصل بمجموعة SharePoint في بيئة متعددة المناطق الجغرافية، يتم استخدام PDL الخاص به لتحديد الموقع الجغرافي حيث يتم إنشاء الموقع وعلبة بريد المجموعة المقترنة به. (إذا لم يتم تعيين قيمة PDL الخاصة بالمستخدم، أو تم تعيينها إلى موقع جغرافي لم يتم تكوينه كموقع تابع، فسيتم إنشاء الموقع وعلبة البريد في الموقع المركزي.)

خدمات Microsoft 365 غير Exchange، OneDrive، SharePoint، Teams ليست متعددة المناطق الجغرافية. ومع ذلك، سيتم تكوين مجموعات Microsoft 365 التي تم إنشاؤها بواسطة هذه الخدمات مع PDL الخاص بالمبدعين وعلبة بريد المجموعة Exchange الخاصة بهم، ويتم توفير موقع SharePoint في الموقع الجغرافي المقابل. 

## <a name="managing-the-multi-geo-environment"></a>إدارة البيئة متعددة المناطق الجغرافية

يتم إعداد البيئة متعددة المناطق الجغرافية وإدارتها من خلال <a href="https://go.microsoft.com/fwlink/?linkid=2185219" target="_blank">مركز إدارة SharePoint</a>. 

![لقطة شاشة لصفحة المواقع الجغرافية في مركز إدارة SharePoint.](../media/sharepoint-multi-geo-admin-center.png)

(تتطلب بعض الإجراءات، مثل نقل موقع SharePoint أو موقع OneDrive Microsoft PowerShell.)

## <a name="see-also"></a>راجع أيضًا

[متعدد الجغرافيا في SharePoint مجموعات Microsoft 365](https://techcommunity.microsoft.com/t5/Office-365-Blog/Now-available-Multi-Geo-in-SharePoint-and-Office-365-Groups/ba-p/263302)

[إدارة بيئة متعددة المواقع الجغرافية](administering-a-multi-geo-environment.md)

[SharePoint الحصص النسبية للتخزين في بيئات جغرافية متعددة](sharepoint-multi-geo-storage-quota.md)

[إدارة علب بريد Exchange Online في بيئة متعددة الجغرافيا](administering-exchange-online-multi-geo.md)
