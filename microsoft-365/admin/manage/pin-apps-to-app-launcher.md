---
title: تثبيت التطبيقات على "تشغيل تطبيق المستخدمين"
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.collection:
- Adm_O365
- M365-subscription-management
- Adm_TOC
ms.service: o365-administration
ms.custom: admindeeplinkMAC
ms.localizationpriority: medium
description: كمسؤول عام، يمكنك تثبيت ما يصل إلى ثلاثة تطبيقات إلى "مستخدم" ومطلق التطبيق الخاص بك.
ms.openlocfilehash: 7ff85e379198312666f03c2d7d6c8bb42b9e08d0
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63570051"
---
# <a name="pin-apps-to-your-users-app-launcher"></a>تثبيت التطبيقات على "تشغيل تطبيق المستخدمين"

يمكنك استخدام عناصر التحكم في مدخل Azure Active Directory ل تثبيت ما يصل إلى ثلاثة تطبيقات إلى Office.com ومطلق التطبيق لجميع المستخدمين في مؤسستك. يمكنك أيضا تنظيم مجموعات من التطبيقات. يمكن للمستخدم لاحقا إلغاء تثبيت أي تطبيق تضيفه في أي وقت. تثبيت تطبيق للمستخدمين، يجب أن تكون مسؤول تطبيق السحابة أو مسؤول التطبيق في Azure Active Directory، أو مسؤول عام في Office 365. لمزيد من المعلومات حول أدوار المسؤولين، راجع [أدوار Azure AD](/azure/active-directory/roles/permissions-reference) المضمنة [وأدوار المسؤولين في](../add-users/about-admin-roles.md) Microsoft 365. 

للحصول على مزيد من المعلومات حول Office.com ومطلق التطبيق، راجع الاجتماع بوادر التطبيق وتحديثات لمدونة office.com ومدونة [Office 365 التطبيق.](https://techcommunity.microsoft.com/t5/office-365-blog/updates-to-office-com-and-the-office-365-app-launcher/ba-p/1150503) [](https://support.microsoft.com/office/79f12104-6fed-442f-96a0-eb089a3f476a)

## <a name="use-the-azure-active-directory-portal-to-pin-apps"></a>استخدام مدخل Azure Active Directory ل تثبيت التطبيقات

1. انتقل إلى مركز مسؤولي Microsoft 365 في <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a>.
2. في التنقل الأيسر، اختر **إظهار الكل**، و ضمن **مراكز الإدارة**، اختر **Azure Active Directory**.
3. في **Azure Active Directory**، اختر **إعدادات Enterprise** **applicationsUser** > .
4. في المقطع **Office 365 الإعدادات**، اختر **إضافة تطبيق**.
5. اختر التطبيقات التي تريد تثبيتها في "تشغيل تطبيق المستخدمين"، ثم اختر **إضافة**.

:::image type="content" source="../../media/add-apps.png" alt-text="Microsoft 365 الإعدادات ل تثبيت التطبيقات.":::

### <a name="pin-a-custom-app"></a>تثبيت تطبيق مخصص

> [!NOTE]
> ستشير واجهة المستخدم إلى ما إذا كنت بحاجة إلى شراء تراخيص Azure AD إضافية لاستخدام هذه الميزة. لمزيد من المعلومات، راجع [أسعار Azure Active Directory](https://azure.microsoft.com/pricing/details/active-directory/).

1. في **Azure Active Directory**، اختر **Enterprise** **applicationsNew** >  application في أعلى **صفحة جميع** التطبيقات.
2. في الصفحة **إضافة تطبيق**، اختر تطبيق غير  معرض أو إنشاء تطبيقك  الخاص إذا كنت في إصدار المعاينة من Azure Active Directory. 
3. اكتب اسما للتطبيق، ثم عين المستخدم في علامة **التبويب المستخدمون** والمجموعات.
4. استخدم علامة **التبويب** خصائص لتحميل أيقونة للتطبيق.
5. لتعيين عنوان URL للتطبيق، في علامة التبويب تسجيل **الدخول** المفرد، اختر **مرتبط** ثم أدخل عنوان URL.
6. اختر **حفظ**.

## <a name="create-application-collections"></a>إنشاء مجموعات التطبيقات

يمكنك أيضا إنشاء مجموعات تطبيقات للمستخدمين في مؤسستك. للحصول على الإرشادات، راجع [إنشاء مجموعات على مدخل تطبيقاتي في مدخل Azure](/azure/active-directory/manage-apps/access-panel-collections).