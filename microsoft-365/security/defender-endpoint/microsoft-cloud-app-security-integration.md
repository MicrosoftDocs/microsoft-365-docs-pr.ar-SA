---
title: نظرة عامة حول تكامل تطبيقات السحابة ل Microsoft Defender
ms.reviewer: ''
description: يتكامل Microsoft Defender for Endpoint مع Defender for Cloud Apps من خلال إعادة توجيه جميع أنشطة شبكات تطبيقات السحابة.
keywords: السحابة والتطبيق والشبكات والرؤية والاستخدام
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
ms.date: 10/18/2018
ms.technology: mde
ms.openlocfilehash: d3cf5259aeb070175d5d2a4a95154974c6cd4d56
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 01/12/2022
ms.locfileid: "63569936"
---
# <a name="microsoft-defender-for-cloud-apps-in-defender-for-endpoint-overview"></a>نظرة عامة حول Microsoft Defender لتطبيقات السحابة في Defender for Endpoint

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

[!include[Prerelease information](../../includes/prerelease.md)]

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Microsoft Defender for Cloud Apps هو حل شامل يوفر إمكانية الرؤية في تطبيقات السحابة وخدماتها من خلال السماح لك بالتحكم في الوصول إلى تطبيقات السحابة والحد من الوصول إليها، مع فرض متطلبات التوافق على البيانات المخزنة في السحابة. لمزيد من المعلومات، راجع [Defender for Cloud Apps](/cloud-app-security/what-is-cloud-app-security).

> [!NOTE]
> تتوفر هذه الميزة مع ترخيص E5 ل [Enterprise Mobility + Security](https://www.microsoft.com/cloud-platform/enterprise-mobility-security) على الأجهزة التي تعمل Windows 10 الإصدار 1809 أو إصدار أحدث، أو Windows 11.

## <a name="microsoft-defender-for-endpoint-and-defender-for-cloud-apps-integration"></a>تكامل Microsoft Defender ل Endpoint و Defender for Cloud Apps

يعتمد اكتشاف Defender for Cloud Apps على سجلات حركة مرور السحابة التي يتم إعادة توجيهها لها من جدار حماية المؤسسة وخادمات الوكيل. يتكامل Microsoft Defender for Endpoint مع Defender for Cloud Apps من خلال تجميع جميع أنشطة شبكات تطبيقات السحابة وإعارة توجيهها، وتوفير رؤية لا مثيل لها لاستخدام تطبيقات السحابة. وظيفة المراقبة مضمنة في الجهاز، مما يوفر تغطية كاملة لنشاط الشبكة.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4r4yQ]

يوفر التكامل التحسينات الرئيسية التالية لاكتشاف Defender for Cloud Apps الموجود:

- متوفر في كل مكان - بما أنه يتم تجميع نشاط الشبكة مباشرة من نقطة النهاية، فإنه يكون متوفرا أينما كان الجهاز، أو على شبكة الشركة أو خارجها، لأنه لم يعد يعتمد على حركة المرور التي يتم توجيهها عبر جدار الحماية الخاص بالمؤسسة أو خوادم الوكيل.

- يعمل خارج المربع، ولا يتطلب أي تكوين - تتطلب إعادة توجيه سجلات حركة المرور السحابية إلى Defender for Cloud Apps جدار الحماية وتكوين الخادم الوكيل. باستخدام تكامل Defender for Endpoint و Defender for Cloud Apps، لا يتطلب الأمر أي تكوين. ما عليك سوى تشغيلها في Microsoft 365 Defender الإعدادات وأنت الآن على ما تريد.

- سياق الجهاز - لا تفتقد سجلات حركة مرور السحابة إلى سياق الجهاز. يتم إعلام Defender لنشاط شبكة Endpoint باستخدام سياق الجهاز (الجهاز الذي قام بالوصول إلى تطبيق السحابة)، بحيث تتمكن من فهم مكان (جهاز) نشاط الشبكة بالضبط، بالإضافة إلى الشخص (المستخدم) الذي قام بتنفيذه.

لمزيد من المعلومات حول اكتشاف السحابة، راجع [استخدام التطبيقات المكتشفة](/cloud-app-security/discovered-apps).

## <a name="related-topic"></a>موضوع ذو صلة

- [تكوين تكامل Microsoft Defender لتطبيقات السحابة](microsoft-cloud-app-security-config.md)
