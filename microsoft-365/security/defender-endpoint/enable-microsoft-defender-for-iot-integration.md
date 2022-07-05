---
title: إلحاق Microsoft Defender ل IoT مع Microsoft Defender لنقطة النهاية
description: الإلحاق مع Microsoft Defender ل IoT للحصول على تقييمات الرؤية والأمان التي تركز على أجهزة IoT.
keywords: تمكين siem connector و siem و connector ومعلومات الأمان والأحداث
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: siosulli
author: siosulli
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: a70b61ff9a27b10e66b6f4537751790eaabc59af
ms.sourcegitcommit: 44ece87e3e0c0c851dfc1e77211ac3e5e4a5b973
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/05/2022
ms.locfileid: "66617271"
---
# <a name="onboard-with-microsoft-defender-for-iot"></a>الإلحاق مع Microsoft Defender ل IoT

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**

- [مشكلات الأداء في Microsoft Defender لنقطة النهاية](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!include[Prerelease information](../../includes/prerelease.md)]

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-enablesiem-abovefoldlink)

يتكامل Microsoft Defender لنقطة النهاية الآن بسلاسة مع Microsoft Defender ل IoT. يعمل هذا التكامل على توسيع قدرات اكتشاف جهازك مع قدرات المراقبة بدون عامل التي يوفرها Defender ل IoT. سيساعد هذا في تأمين أجهزة IoT للمؤسسات المتصلة بشبكات تكنولوجيا المعلومات، مثل أجهزة بروتوكول الصوت عبر الإنترنت (VoIP) والطابعات والكاميرات. فهو يسمح للمؤسسات بالاستفادة من حل متكامل واحد يؤمن جميع البنية الأساسية ل IoT والتكنولوجيا التشغيلية (OT). لمزيد من المعلومات، راجع [حماية شبكة إنترنت الأشياء على مستوى المؤسسة](/azure/defender-for-iot/organizations/overview-eiot).

بمجرد تحديد خطة Defender ل IoT وإعداد مستشعر شبكة Enterprise IoT، تبدأ بيانات الجهاز تلقائيا في التدفق إلى كل من Defender لنقطة النهاية و Defender لمداخل IoT. 

يوفر تكامل Defender ل IoT رؤية متزايدة للمساعدة في تحديد موقع أجهزة IoT في شبكتك وتحديدها وتأمينها. سيوفر لك ذلك طريقة عرض موحدة واحدة لمخزون OT/IoT الكامل إلى جانب بقية أجهزة تكنولوجيا المعلومات (محطات العمل والخوادم والأجهزة المحمولة).

يتمتع العملاء الذين قاموا بإلحاق Defender ل IoT أيضا بتوصيات أمنية لتقييمات الثغرات الأمنية والتكوينات الخاطئة لأجهزة IoT.

## <a name="prerequisites"></a>المتطلبات الأساسية

لتعديل إعدادات تكامل Defender لنقطة النهاية، يجب أن يكون للمستخدم الأدوار التالية:

- المسؤول العام للمستأجر في Azure Active Directory
- مسؤول الأمان لاشتراك Azure الذي سيتم استخدامه من أجل تكامل Microsoft Defender ل IoT

## <a name="onboard-a-defender-for-iot-plan"></a>إعداد خطة Defender ل IoT

1. في جزء التنقل من [https://security.microsoft.com](https://security.microsoft.com/) المدخل، حدد **Settings** \> **Device discovery** \> **Enterprise IoT**.

1. حدد الخيارات التالية لخطتك:

   - حدد اشتراك Azure من قائمة الاشتراكات المتوفرة في مستأجر Azure Active Directory حيث تريد إضافة خطة.

   - حدد خطة تسعير، إما التزام شهري أو سنوي، أو إصدار تجريبي. يوفر Microsoft Defender ل IoT إصدارا تجريبيا مجانيا لمدة 30 يوما لأول 1000 جهاز مخصص لأغراض التقييم.

      لمزيد من المعلومات، راجع [صفحة تسعير Microsoft Defender ل IoT](https://azure.microsoft.com/pricing/details/iot-defender/).
   
   - حدد عدد الأجهزة الملتزم بها التي ستحتاج إلى مراقبتها. إذا حددت إصدارا تجريبيا، فلن يظهر هذا المقطع لأن لديك 1000 جهاز افتراضي.

## <a name="set-up-a-network-sensor"></a>إعداد مستشعر الشبكة

لإعداد مستشعر شبكة، يجب أن يحتوي اشتراك Azure على خطة Defender ل IoT مع إضافة أجهزة Enterprise IoT. لمزيد من المعلومات، راجع [بدء استخدام Defender ل IoT](/azure/defender-for-iot/organizations/getting-started).

لإضافة مستشعر شبكة، ضمن **إعداد مستشعرات الشبكة** ، اختر رابط **Microsoft Defender ل IoT** . هذا ينقلك إلى عملية إعداد أداة الاستشعار على متن أجهزة الاستشعار في مدخل Azure. لمزيد من المعلومات، راجع [بدء استخدام Enterprise IoT](/azure/defender-for-iot/organizations/tutorial-getting-started-eiot-sensor).

## <a name="managing-your-iot-devices"></a>إدارة أجهزة IoT

لعرض أجهزة IoT وإدارتها في [مدخل Microsoft 365 Defender](https://security.microsoft.com/) انتقل إلى **مخزون الجهاز** من قائمة التنقل **في نقاط النهاية** وحدد علامة تبويب **أجهزة IoT**.

للحصول على معلومات حول كيفية عرض الأجهزة في Defender ل IoT، راجع [إدارة أجهزة IoT باستخدام مخزون الأجهزة للمؤسسات](/azure/defender-for-iot/organizations/how-to-manage-device-inventory-for-organizations).


## <a name="view-devices-alerts-recommendations-and-vulnerabilities"></a>عرض الأجهزة والتنبيهات والتوصيات والثغرات الأمنية

بعد تحديد خطتك وإعداد مستشعر الشبكة، قم بعرض البيانات المكتشفة وتقييمات الأمان في المواقع التالية:

- عرض بيانات الجهاز في Defender لنقطة النهاية أو Defender ل IoT
- عرض التنبيهات والتوصيات والثغرات الأمنية في Defender لنقطة النهاية

لمزيد من المعلومات، راجع [صفحة تسعير Defender for IoT](https://azure.microsoft.com/pricing/details/iot-defender/). 

## <a name="cancel-your-defender-for-iot-plan"></a>إلغاء خطة Defender ل IoT

يمكنك إلغاء خطة Defender for IoT من صفحة إعدادات Defender لنقطة النهاية في [https://security.microsoft.com](https://security.microsoft.com/) المدخل. بمجرد إلغاء خطتك، يتوقف التكامل ولن تحصل على قيمة تقييم الأمان في Defender لنقطة النهاية، أو اكتشاف أجهزة جديدة في Defender ل IoT.

## <a name="see-also"></a>راجع أيضًا

- [نظرة عامة على اكتشاف الجهاز](configure-device-discovery.md)
- [الأسئلة الشائعة حول اكتشاف الجهاز](device-discovery-faq.md)
