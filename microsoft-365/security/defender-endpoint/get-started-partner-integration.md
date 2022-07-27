---
title: كن شريكاً Microsoft Defender لنقطة النهاية
ms.reviewer: ''
description: تعرف على الخطوات والمتطلبات لدمج الحل الخاص بك مع Microsoft Defender لنقطة النهاية وأن تكون شريكا
keywords: شريك، تكامل، التحقق من صحة الحل، المصادقة، المتطلبات، العضو، misa، مدخل التطبيق
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
ms.openlocfilehash: 276f411699f4a9db61850a04da3ff18d3c6bb2a7
ms.sourcegitcommit: e8dd5cd434d17af7096d28d467a2b3b021cbb233
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/27/2022
ms.locfileid: "67051195"
---
# <a name="become-a-microsoft-defender-for-endpoint-partner"></a>كن شريكاً Microsoft Defender لنقطة النهاية

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [الخطة 1 من Microsoft Defender لنقطة النهاية](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


لتصبح شريك حل Defender لنقطة النهاية، ستحتاج إلى اتباع الخطوات التالية وإكمالها.

## <a name="step-1-subscribe-to-a-microsoft-defender-for-endpoint-license"></a>الخطوة 1: الاشتراك في ترخيص Microsoft Defender لنقطة النهاية

هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink) يسمح لك الاشتراك باستخدام مستأجر Microsoft Defender لنقطة النهاية مع ما يصل إلى ثلاثة أجهزة لتطوير حلول تتكامل مع Microsoft Defender لنقطة النهاية.

## <a name="step-2-fulfill-the-solution-validation-and-certification-requirements"></a>الخطوة 2: استيفاء متطلبات التحقق من صحة الحل والمصادقة

أفضل طريقة لشركاء التكنولوجيا للمصادقة على عمل التكامل الخاص بهم هي أن يوافق العميل المشترك على تصميم التكامل المقترح (يمكن للعميل استخدام خيار \(**التوصية بشركاء** وواجهة برمجة التطبيقات > تطبيقات\) الشريك في [صفحة تطبيق الشريك](https://security.microsoft.com/interoperability/partnersapps) في Microsoft 365 Defender واختباره وعرضه على فريق Microsoft Defender لنقطة النهاية.

بمجرد قيام فريق Microsoft Defender لنقطة النهاية بمراجعة التكامل والموافقة عليه، سنوجهك إلى تضمينك كشريك في Microsoft Intelligent Security Association.

## <a name="step-3-get-listed-in-the-microsoft-defender-for-endpoint-partner-application-portal"></a>الخطوة 3: إدراج في مدخل تطبيق الشريك Microsoft Defender لنقطة النهاية

يدعم Microsoft Defender لنقطة النهاية اكتشاف تطبيقات الجهات الخارجية والتكامل باستخدام [صفحة الشريك](partner-applications.md) داخل المنتج المضمنة في مدخل إدارة Microsoft Defender لنقطة النهاية.

لإدراج شركتك كشريك في صفحة الشريك داخل المنتج، ستحتاج إلى توفير المعلومات التالية:

1. شعار مربع (SVG).
2. اسم المنتج المطلوب تقديمه.
3. توفير وصف منتج مكون من 15 كلمة.
4. قم بإنشاء ارتباط إلى الصفحة المنتقل إليها ليكمل العميل عملية التكامل أو منشور المدونة الذي سيتضمن معلومات كافية للعملاء. يجب مراجعة أي إصدار اضغط بما في ذلك اسم المنتج Microsoft Defender لنقطة النهاية من قبل فرق التسويق والهندسة. انتظر 10 أيام على الأقل حتى تتم عملية المراجعة.
5. إذا كنت تستخدم نهج Azure AD متعدد المستأجرين، فسنحتاج إلى اسم التطبيق Azure AD لتعقب استخدام التطبيق.
6. قم بتضمين حقل User-Agent في كل استدعاء API تم إجراؤه Microsoft Defender لنقطة النهاية مجموعة عامة من واجهات برمجة التطبيقات أو واجهات برمجة تطبيقات أمان الرسم البياني. سيتم استخدام هذا لأغراض إحصائية واستكشاف الأخطاء وإصلاحها والتعرف على الشريك. بالإضافة إلى ذلك، تعد هذه الخطوة شرطا للعضوية في Microsoft Intelligent Security Association (MISA).

   اتبع الخطوات التالية:

   - قم بتعيين حقل User-Agent في كل عنوان طلب HTTP إلى التنسيق أدناه.

     ```http
     MdePartner-{CompanyName}-{ProductName}/{Version}
     ```

     على سبيل المثال، User-Agent:

     ```http
     MdePartner-Contoso-ContosoCognito/1.0.0
     ```

   - لمزيد من المعلومات، راجع [RFC 2616 section-14.43](https://tools.ietf.org/html/rfc2616#section-14.43).

تساعد الشراكات مع Microsoft Defender لنقطة النهاية عملائنا المشتركين على زيادة تبسيط الدفاعات وتكاملها وتنسيقها. يسعدنا اختيارك أن تصبح شريكا Microsoft Defender لنقطة النهاية وتحقيق هدفنا المشترك المتمثل في حماية العملاء وأصولهم بشكل فعال من خلال منع التهديدات الحديثة والاستجابة لها معا.

## <a name="misa-nomination"></a>تسمية MISA 
يمكن مرشح موفري خدمات الأمان المدارة (MSSP) وموردي البرامج المستقلين (ISV) لمؤسسة الأمان الذكي من Microsoft (MISA). لمزيد من المعلومات، راجع [صفحة معلومات MISA](https://www.microsoft.com/security/business/intelligent-security-association).


## <a name="related-topics"></a>المواضيع ذات الصلة

- [فرص الشريك التقني](partner-integration.md)
