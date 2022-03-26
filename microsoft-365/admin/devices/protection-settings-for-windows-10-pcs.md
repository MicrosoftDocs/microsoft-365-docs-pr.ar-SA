---
title: تحرير إعدادات حماية الجهاز أو إنشائها Windows 10 الكمبيوتر الشخصي
f1.keywords:
- NOCSH
ms.author: sharik
author: skjerland
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- M365-identity-device-management
- Adm_TOC
ms.custom:
- Core_O365Admin_Migration
- MiniMaven
- MSB365
- OKR_SMB_M365
- AdminSurgePortfolio
- adminvideo
search.appverid:
- BCS160
- MET150
ms.assetid: bd66c26c-73a4-45a8-8642-3ea4ee7cd89d
description: تعرف على الإعدادات المتوفرة في Microsoft 365 للأعمال لتأمين Windows 10 الأجهزة.
ms.openlocfilehash: 26a9921d1c950990adcb4a28516ce2207fb3bcd1
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63571999"
---
# <a name="edit-or-create-device-protection-settings-for-windows-10-pcs"></a>تحرير إعدادات حماية الجهاز أو إنشائها Windows 10 الكمبيوتر الشخصي

تنطبق هذه المقالة على Microsoft 365 Business Premium.

> [!NOTE]
> يتم طرح Microsoft Defender for Business Microsoft 365 Business Premium العملاء، بدءا من 1 مارس 2022. يوفر هذا العرض ميزات أمان إضافية للأجهزة. [تعرف على المزيد حول Defender for Business](../../security/defender-business/mdb-overview.md).

بعد إعداد إعدادات حماية Windows الافتراضية في صفحة الإعداد، يمكنك إضافة إعدادات جديدة تنطبق على كل المستخدمين أو مجموعة من المستخدمين. يمكنك أيضا تحرير أي من تلك التي قمت بإنشاءها.

## <a name="watch-create-protection-settings-for-windows-10-devices"></a>شاهد: إنشاء إعدادات حماية للأجهزة Windows 10 الأجهزة

عرض فيديو حول كيفية تأمين أجهزة Windows 10 باستخدام Microsoft 365 Business Premium:
  
> [!VIDEO https://www.microsoft.com/videoplayer/embed/a5734146-620a-4cec-8618-536b3ca37972?autoplay=false]
  
1. انتقل إلى مركز الإدارة في <a href="https://go.microsoft.com/fwlink/p/?linkid=837890" target="_blank">https://admin.microsoft.com</a>. 
2. على الجانب الأيسر من التنقل، اختر **إضافة** \> **سياسات** \> **الأجهزة**.
3. في الجزء **إضافة نهج** ، أدخل اسما فريدا لهذا النهج. 
4. ضمن **نوع النهج**، **اختر Windows 10 تكوين الجهاز**.
5. قم **بتوسيع "Windows 10 آمنة**\>" تقوم الأجهزة بتكوين الإعدادات كما تريد. لمزيد من المعلومات، راجع [الإعدادات المتوفرة](#available-settings). 
    
    يمكنك دائما استخدام الارتباط **إعادة تعيين الإعدادات الافتراضية** للعودة إلى الإعداد الافتراضي. 
    
    ![إضافة جزء نهج مع تحديد Windows 10 الجهاز.](../../media/fa9e2dc2-7eae-4c96-af34-765a1f641ecf.png)
  
6. هل تقرر **روبوت Who ستحصل على هذه الإعدادات؟** إذا كنت لا تريد استخدام مجموعة أمان جميع المستخدمين  الافتراضية، فاختر تغيير، وابحث عن مجموعة الأمان التي ستحصل على هذه الإعدادات \> **حدد**.
7. وأخيرا، اختر **تم** لحفظ النهج وتعيينه إلى الأجهزة. 

## <a name="edit-windows-10-protection-settings"></a>تحرير Windows 10 الحماية
 
1. انتقل إلى مركز الإدارة في <a href="https://go.microsoft.com/fwlink/p/?linkid=837890" target="_blank">https://admin.microsoft.com</a>.     
2. على الجانب الأيسر من التنقل، اختر **"سياسات** \> **الأجهزة".**
1. اختر نهج جهاز Windows ثم **تحرير**.
1. اختر **تحرير** بجانب إعداد تريد تغييره، ثم **حفظ**.

## <a name="available-settings"></a>الإعدادات المتوفرة

تكون كل الإعدادات بشكل افتراضي في **وضع "On**". تتوفر الإعدادات التالية.
  
لمزيد من المعلومات، راجع [كيفية تعيين ميزات الحماية Microsoft 365 Premium إعدادات Intune](map-protection-features-to-intune-settings.md). 


|الإعداد  <br/> |الوصف  <br/> |
|:-----|:-----|
|المساعدة على حماية أجهزة الكمبيوتر الشخصية من الفيروسات والتهديدات الأخرى باستخدام برنامج الحماية من الفيروسات لـ Windows Defender  <br/> |يتطلب تشغيل برنامج الحماية من الفيروسات لـ Windows Defender لحماية أجهزة الكمبيوتر الشخصية من مخاطر الاتصال بالإنترنت.  <br/> |
|المساعدة على حماية أجهزة الكمبيوتر الشخصية من التهديدات المستندة إلى الويب في Microsoft Edge  <br/> |تشغيل الإعدادات في Edge التي تساعد على حماية المستخدمين من المواقع والتنزيلها الضارة.  <br/> |
|استخدام القواعد التي تقلل من سطح الهجوم للأجهزة  <br/> |عند تشغيل، يساعد الحد من سطح الهجوم على حظر الإجراءات والتطبيقات التي تستخدمها البرامج الضارة عادة لإصابة الأجهزة. يتوفر هذا الإعداد فقط إذا برنامج الحماية من الفيروسات لـ Windows Defender تعيين إلى "تم". راجع [تقليل أسطح الهجمات](/windows/security/threat-protection/microsoft-defender-atp/exploit-protection) لمعرفة المزيد.  <br/> |
|حماية المجلدات من التهديدات مثل برامج الفدية الضارة  <br/> |يستخدم هذا الإعداد إمكانية الوصول إلى المجلدات الخاضعة للتحكم لحماية بيانات الشركة من التعديل بواسطة التطبيقات المريبة أو الضارة، مثل برامج الفدية الضارة. يتم حظر هذه الأنواع من التطبيقات من إجراء تغييرات في المجلدات المحمية. يتوفر هذا الإعداد فقط إذا برنامج الحماية من الفيروسات لـ Windows Defender تعيين إلى "تم". راجع [حماية المجلدات باستخدام الوصول إلى المجلدات الخاضعة للتحكم](/mem/configmgr/protect/deploy-use/create-deploy-exploit-guard-policy#bkmk_CFA) لمعرفة المزيد.  <br/> |
|منع وصول الشبكة إلى محتوى يحتمل أن يكون ضارا على الإنترنت  <br/> |استخدم هذا الإعداد لحظر اتصالات المستخدمين الصادرين إلى مواقع الإنترنت ذات السمعة المنخفضة التي قد تستضيف رسائل التصيد الاحتيالي أو عمليات استغلال أو أي محتوى ضار آخر. يتوفر هذا الإعداد فقط إذا برنامج الحماية من الفيروسات لـ Windows Defender تعيين إلى **"تم".** لمزيد من المعلومات، راجع [حماية الشبكة](/windows/security/threat-protection/windows-defender-antivirus/configure-real-time-protection-windows-defender-antivirus).  <br/> |
|المساعدة في حماية الملفات والمجلدات على أجهزة الكمبيوتر الشخصية من الوصول غير المصرح به باستخدام BitLocker  <br/> |يحمي BitLocker البيانات عن طريق تشفير محركات الأقراص الثابت للكمبيوتر والحماية من التعرض للبيانات إذا تم فقدان جهاز كمبيوتر أو سرقته. لمزيد من المعلومات، راجع [الأسئلة الشائعة حول BitLocker](/windows/security/information-protection/BitLocker/BitLocker-frequently-asked-questions).  <br/> |
|السماح للمستخدمين بتنزيل التطبيقات من Microsoft Store  <br/> |السماح للمستخدمين بتنزيل التطبيقات وتثبيتها من Microsoft Store. تتضمن التطبيقات كل شيء من الألعاب إلى أدوات الإنتاجية، لذا سنترك هذا الإعداد في وضع التشغيل، ولكن يمكنك إيقاف تشغيله لمزيد من الأمان.  <br/> |
|السماح للمستخدمين بالوصول إلى Cortana  <br/> |Cortana تكون مفيدة جدا! Cortana تشغيل الإعدادات أو إيقاف تشغيلها لك، وتحديد التوجيهات، والتأكد من أنك في الوقت المحدد للمواعيد، لذا سنحتفظ بهذا الإعداد في وضع التشغيل بشكل افتراضي.  <br/> |
|السماح للمستخدمين بتلقي Windows والإعلانات من Microsoft  <br/> |Windows هذه التلميحات مفيدة وتساعد على توجيه المستخدمين عند إصدار ميزات جديدة.  <br/> |
|تحديث Windows 10 تلقائيا  <br/> |تأكد من أن Windows 10 الأجهزة تتلقى التحديثات الأخيرة تلقائيا.  <br/> |
|إيقاف تشغيل شاشة الجهاز عند الخمول لهذا الوقت  <br/> |تأكد من حماية بيانات الشركة إذا كان المستخدم معطلا. قد يعمل المستخدم في موقع عام، مثل المقهى، ويبتعد أو يتشتت قليلا، مما يترك جهازه عرضة لنظرات سريعة عشوائية. يتيح لك هذا الإعداد التحكم في مدة خمول المستخدم قبل إيقاف تشغيل الشاشة.  <br/> |

## <a name="see-also"></a>راجع أيضًا

[أفضل 10 طرق لتأمين Microsoft 365 خطط الأعمال](../security-and-compliance/secure-your-business-data.md)