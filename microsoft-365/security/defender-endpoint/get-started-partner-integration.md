---
title: كن أحد شركاء Microsoft Defender for Endpoint
ms.reviewer: ''
description: تعرف على الخطوات والمتطلبات لدمج الحل مع Microsoft Defender لنقطة النهاية وأن تكون شريكا
keywords: الشريك، التكامل، التحقق من صحة الحل، المصادقة، المتطلبات، العضو، misa، مدخل التطبيق
ms.prod: w10
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
ms.openlocfilehash: b063d8435817d7dd64c3febf6e3399f3876ef894
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63575790"
---
# <a name="become-a-microsoft-defender-for-endpoint-partner"></a>كن أحد شركاء Microsoft Defender for Endpoint

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


لكي تصبح شريك حل Defender for Endpoint، ستحتاج إلى اتباع الخطوات التالية وإكمالها.

## <a name="step-1-subscribe-to-a-microsoft-defender-for-endpoint-license"></a>الخطوة 1: الاشتراك في ترخيص Microsoft Defender لنقطة النهاية

هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink). يسمح لك الاشتراك باستخدام مستأجر Microsoft Defender لنقطة النهاية مع ما يصل إلى ثلاثة أجهزة لتطوير حلول تتكامل مع Microsoft Defender ل Endpoint.

## <a name="step-2-fulfill-the-solution-validation-and-certification-requirements"></a>الخطوة 2: تلبية متطلبات التحقق من صحة الحل والمصادقة

أفضل طريقة لشركاء التقنية للمصادقة على عمل تكاملهم هي أن يوافق عميل مشترك على تصميم التكامل المقترح  (\(يمكن للعميل استخدام الخيار موصى بخيار الشريك شركاء و API > [](https://security.microsoft.com/interoperability/partnersapps)\) في صفحة تطبيق الشريك في Microsoft 365 Defender واختباره وتخفضه إلى فريق Microsoft Defender لنقطة النهاية.

بمجرد مراجعة فريق Microsoft Defender لنقطة النهاية للتكامل والموافقة عليه، سنوجهك لتضمينك كشريك في "اقتران الأمان الذكي ل Microsoft".

## <a name="step-3-get-listed-in-the-microsoft-defender-for-endpoint-partner-application-portal"></a>الخطوة 3: إدراجك في مدخل تطبيق شريك Microsoft Defender for Endpoint

يدعم Microsoft Defender ل Endpoint اكتشاف التطبيقات الخارجية والتكامل باستخدام صفحة الشريك داخل المنتج المضمنة في مدخل [](partner-applications.md) إدارة Microsoft Defender for Endpoint.

لكي تكون شركتك مدرجة كشركاء في صفحة الشريك داخل المنتج، ستحتاج إلى توفير المعلومات التالية:

1. شعار مربع (SVG).
2. اسم المنتج الذي سيتم تقديمه.
3. توفير وصف منتج من 15 كلمة.
4. قم بالارتباط بالصفحة المنتقلة للعميل لإكمال عملية التكامل أو منشور المدونة الذي سيتضمن معلومات كافية للعملاء. يجب مراجعة أي إصدار صحفي بما في ذلك اسم منتج Microsoft Defender for Endpoint بواسطة فرق التسويق والهندسة. انتظر 10 أيام على الأقل حتى تتم عملية المراجعة.
5. إذا كنت تستخدم نهج Azure AD متعدد المستأجرين، فنحن بحاجة إلى اسم تطبيق Azure AD لتعقب استخدام التطبيق.
6. قم بتضمين User-Agent في كل مكالمة API التي يتم إتصالها ب Microsoft Defender for Endpoint مجموعة عامة من واجهات برمجة التطبيقات أو Graph واجهات برمجة تطبيقات الأمان. سيتم استخدام هذا لأغراض إحصائية، استكشاف الأخطاء وإصلاحها، التعرف على الشريك. بالإضافة إلى ذلك، هذه الخطوة هي أحد متطلبات العضوية في Microsoft Intelligent Security Association (MISA).

   اتبع الخطوات التالية:

   - قم بتعيين User-Agent في كل رأس طلب HTTP إلى التنسيق أدناه.

     ```http
     MdePartner-{CompanyName}-{ProductName}/{Version}
     ```

     على سبيل المثال، User-Agent:

     ```http
     MdePartner-Contoso-ContosoCognito/1.0.0
     ```

   - لمزيد من المعلومات، راجع [المقطع RFC 2616-14.43](https://tools.ietf.org/html/rfc2616#section-14.43).

تساعد الشراكة مع Microsoft Defender for Endpoint عملائنا المتبادلين على زيادة تنظيم الدفاعات وتكاملها وتوحيدها. يسعدنا أنك اخترت أن تصبح شريك Microsoft Defender لنقطة النهاية وأن تحقق هدفنا المشترك وهو حماية العملاء وأصولهم بفعالية من خلال منع التهديدات الحديثة والاستجابة لها معا.

## <a name="misa-nomination"></a>مهى 
يمكن تسمية موفري خدمات الأمان المدارة (MSSP) وموردي البرامج المستقلة (ISV) إلى "جمعية الأمان الذكي ل Microsoft" (MISA). لمزيد من المعلومات، راجع [صفحة معلومات MISA](https://www.microsoft.com/security/business/intelligent-security-association).


## <a name="related-topics"></a>المواضيع ذات الصلة

- [فرص الشريك التقني](partner-integration.md)
