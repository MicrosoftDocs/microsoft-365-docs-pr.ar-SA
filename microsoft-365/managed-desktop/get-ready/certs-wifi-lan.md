---
title: إعداد الشهادات وملفات تعريف الشبكة لسطح المكتب المدار من Microsoft
description: متطلبات الشهادة واتصال wi-fi
keywords: سطح المكتب المدار من Microsoft، Microsoft 365، الخدمة، الوثائق
ms.service: m365-md
author: tiaraquan
f1.keywords:
- NOCSH
ms.author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
manager: dougeby
ms.topic: article
audience: Admin
ms.openlocfilehash: ccdd9f390c794590eed6cbe11d169430f92bdf55
ms.sourcegitcommit: cafca45069819a44c7cf8c67f6c1e105de1b3393
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/10/2022
ms.locfileid: "63566082"
---
# <a name="prepare-certificates-and-network-profiles-for-microsoft-managed-desktop"></a>إعداد الشهادات وملفات تعريف الشبكة لسطح المكتب المدار من Microsoft  

المصادقة المستندة إلى الشهادة هي أحد المتطلبات الشائعة للعملاء الذين يستخدمون Microsoft Managed Desktop. قد تحتاج إلى شهادات من أجل:

- الوصول Wi-Fi أو LAN
- الاتصال إلى حلول VPN
- الوصول إلى الموارد الداخلية في مؤسستك

نظرا لأن أجهزة Microsoft Managed Desktop منضمة إلى Azure Active Directory (Azure AD) وتدار بواسطة Microsoft Intune، يجب نشر مثل هذه الشهادات باستخدام:

- بروتوكول تسجيل الشهادة البسيط (SCEP) أو
- البنية الأساسية للشهادات القياسية لتشريب المفاتيح العامة (PKCS) المتكاملة مع Intune.

## <a name="certificate-requirements"></a>متطلبات الشهادة

الشهادات الجذر مطلوبة لنشر الشهادات من خلال البنية الأساسية ل SCEP أو PKCS. قد تحتاج التطبيقات والخدمات الأخرى في مؤسستك إلى شهادات جذر لنشرها على أجهزة سطح المكتب المدارة من Microsoft.

قبل نشر شهادات SCEP أو PKCS إلى Microsoft Managed Desktop، يجب عليك جمع متطلبات كل خدمة تتطلب شهادة مستخدم أو جهاز في مؤسستك. لتسهيل هذا النشاط، يمكنك استخدام أحد قوالب التخطيط التالية:  

- [قالب شهادة PKCS](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/managed-desktop/get-ready/downloads/PKCS-certificate-template.xlsx)
- [قالب شهادة SCEP](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/managed-desktop/get-ready/downloads/SCEP-certificate-template.xlsx)

## <a name="wi-fi-connectivity-requirements"></a>Wi-Fi متطلبات الاتصال

للسماح بأن يتم توفير الجهاز تلقائيا مع Wi-Fi المطلوب لشبكة المؤسسة، قد تحتاج إلى ملف تعريف Wi-Fi تكوين.

يمكنك تكوين Microsoft Managed Desktop لنشر ملفات التعريف هذه على أجهزتك. إذا كان أمان الشبكة يتطلب أن تكون الأجهزة جزءا من المجال المحلي، فقد تحتاج إلى تقييم البنية الأساسية لشبكة Wi-Fi لضمان توافقها مع أجهزة سطح المكتب المدارة من Microsoft. أجهزة سطح المكتب المدارة من Microsoft هي Azure AD المتصلة فقط.

قبل نشر تكوين Wi-Fi على أجهزة سطح المكتب المدارة من Microsoft، سيطلب منك جمع متطلبات مؤسستك لكل شبكة Wi-Fi الشبكة. لتسهيل هذا النشاط، يمكنك استخدام قالب ملف [تعريف WiFi هذا](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/managed-desktop/get-ready/downloads/WiFi-profile-template.xlsx).

## <a name="wired-connectivity-requirements-and-8021x-authentication"></a>متطلبات الاتصال السلكي ومصادقة 802.1x

إذا كنت تستخدم مصادقة 802.1x لتأمين الوصول من الأجهزة إلى شبكة المنطقة المحلية (LAN)، ستحتاج إلى دفع تفاصيل التكوين المطلوبة إلى أجهزة سطح المكتب المدارة من Microsoft.

تدعم أجهزة سطح المكتب المدارة الإصدار 1809 من Windows 10 Microsoft نشر تكوين 802.1x من خلال موفر خدمة تكوين WiredNetwork (CSP). لمزيد من المعلومات، راجع [وثائق WiredNetwork CSP](/windows/client-management/mdm/wirednetwork-csp) .

قبل نشر ملف تعريف تكوين شبكة سلكي على أجهزة سطح المكتب المدارة من Microsoft، اجمع متطلبات مؤسستك لشبكة الشركة السلكية.

**لجمع متطلبات شبكة الشركة السلكية:**

1. سجل الدخول إلى جهاز تم تكوين ملف تعريف 802.1x الحالي الخاص بك ومتصل بشبكة LAN.  
2. افتح موجه أوامر باستخدام بيانات الاعتماد الإدارية.
3. ابحث عن اسم واجهة LAN عن طريق تشغيل `netsh interface show interface`.
4. تصدير ملف تعريف LAN XML عن طريق تشغيل `netsh lan export profile folder=.  Interface=”interface_name”`.
5. إذا كنت بحاجة إلى اختبار ملف التعريف الذي تم تصديره على جهاز Microsoft Managed Desktop، فجرب .`netsh lan add profile filename="PATH_AND_FILENAME.xml" interface="INTERFACE_NAME"`

## <a name="deploy-certificate-infrastructure"></a>نشر البنية الأساسية للشهادة  

إذا كان لديك بالفعل بنية أساسية موجودة ل SCEP أو PKCS مع Intune وكان هذا النهج يلبي متطلباتك، يمكنك أيضا استخدامه لسطح المكتب المدار من Microsoft.

إذا لم تكن هناك بنية أساسية ل SCEP أو PKCS موجودة بالفعل،  فسوف تحتاج إلى إعداد واحدة. لمزيد من المعلومات، راجع [تكوين ملف تعريف شهادة للأجهزة في](/intune/certificates-configure) Microsoft Intune.

## <a name="deploy-a-lan-profile"></a>نشر ملف تعريف LAN

بمجرد تصدير ملف تعريف LAN، يمكنك إعداد النهج لسطح المكتب المدار من Microsoft.

**لإعداد النهج لسطح المكتب المدار من Microsoft:**

1. إنشاء ملف تعريف مخصص في Microsoft Intune ملف تعريف LAN باستخدام الإعدادات التالية (راجع استخدام الإعدادات المخصصة للأجهزة Windows 10 [Intune](/intune/custom-settings-windows-10)). في **OMA-URI الإعدادات**، حدد **إضافة**، ثم أدخل القيم التالية:
    - الاسم: ملف تعريف Workplace-Windows LAN 10
    - الوصف: أدخل وصفا يقدم نظرة عامة حول الإعداد وأي تفاصيل مهمة أخرى.
    - OMA-URI (حساسة للقضية): Enter `./Device/Vendor/MSFT/WiredNetwork/LanXML`
    - نوع البيانات: حدد **سلسلة (ملف XML)**.
    - XML مخصص: Upload ملف XML الذي تم تصديره.
2. تعيين ملف التعريف المخصص إلى **"أجهزة مكان العمل الحديثة" - المجموعة "اختبار** ".
3. إجراء أي اختبار تشعر أنه ضروري باستخدام جهاز في مجموعة نشر الاختبار. إذا نجح، قم بتعيين ملف التعريف المخصص إلى المجموعات التالية:
    - أجهزة مكان العمل الحديثة - أولا
    - أجهزة مكان العمل الحديثة - سريع
    - أجهزة مكان العمل الحديثة - واسعة

## <a name="deploy-certificates-and-wi-fivpn-profile"></a>نشر الشهادات وملف تعريف Wi-Fi/VPN

**لنشر الشهادات وملفات التعريف:**

1. إنشاء ملف تعريف لكل شهادة من الشهادات الجذر والمتوسطة (راجع [إنشاء ملفات تعريف شهادات موثوق بها](/intune/protect/certificates-configure#step-3-create-trusted-certificate-profiles). يجب أن يتضمن كل ملف من ملفات التعريف هذه وصفا يتضمن تاريخ انتهاء الصلاحية بتنسيق DD/MM/YYYY. **يجب أن يكون لملفات تعريف الشهادات تاريخ انتهاء الصلاحية.**
2. إنشاء ملف تعريف لكل شهادات SCEP أو PKCS (راجع إنشاء ملف تعريف شهادة [SCEP](/intune/protect/certificates-scep-configure#create-a-scep-certificate-profile) أو [إنشاء ملف تعريف شهادة PKCS](/intune/protect/certficates-pfx-configure#create-a-pkcs-certificate-profile)). يجب أن يتضمن كل ملف من ملفات التعريف هذه وصفا يتضمن تاريخ انتهاء الصلاحية بتنسيق DD/MM/YYYY. **يجب أن يكون لملفات تعريف الشهادات تاريخ انتهاء الصلاحية.**
3. إنشاء ملف تعريف لكل شبكة WiFi خاصة بالشركة (راجع إعدادات [Wi-Fi للأجهزة Windows 10 واللاحقة](/intune/wi-fi-settings-windows)).
4. إنشاء ملف تعريف لكل VPN خاص بالشركة ([راجع Windows 10 وإعدادات Windows Holographic لإضافة اتصالات VPN باستخدام Intune](/intune/vpn-settings-windows-10)).
5. تعيين ملفات التعريف إلى **"أجهزة مكان العمل الحديثة" - المجموعة "اختبار** ".
6. إجراء أي اختبار تشعر أنه ضروري باستخدام جهاز في مجموعة نشر الاختبار. إذا نجح، قم بتعيين ملف التعريف المخصص إلى المجموعات التالية:
    - أجهزة مكان العمل الحديثة - أولا
    - أجهزة مكان العمل الحديثة - سريع
    - أجهزة مكان العمل الحديثة - واسعة

## <a name="steps-to-get-ready-for-microsoft-managed-desktop"></a>خطوات الاستعداد لسطح المكتب المدار من Microsoft

1. مراجعة [المتطلبات الأساسية لسطح المكتب المدار من Microsoft](prerequisites.md).
1. تشغيل [أدوات تقييم الجهوزية](readiness-assessment-tool.md).
1. شراء [Company Portal](../get-started/company-portal.md).
1. مراجعة [المتطلبات الأساسية الخاصة وحسابات الضيوف](guest-accounts.md).
1. تحقق [من تكوين الشبكة](network.md).
1. إعداد الشهادات وملفات تعريف الشبكة (هذه المقالة).
1. [إعداد وصول المستخدم إلى البيانات](authentication.md).
1. [تحضير التطبيقات](apps.md).
1. [إعداد محركات أقراص تم تعيينها](mapped-drives.md).
1. [تحضير موارد الطباعة](printing.md).
1. أسماء [أجهزة العنوان](address-device-names.md).
