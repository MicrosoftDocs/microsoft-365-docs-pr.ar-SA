---
title: الخطوة 2. توفير الوصول عن بعد إلى التطبيقات والخدمات المحلية
f1.keywords:
- NOCSH
author: dansimp
ms.author: dansimp
manager: dansimp
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- Strat_O365_Enterprise
- remotework
- m365solution-remotework
- m365solution-scenario
ms.custom: ''
description: تأكد من أن العاملين عن بعد يمكنهم الوصول إلى الموارد المحلية مع تحسين الوصول إلى Microsoft 365 السحابية.
ms.openlocfilehash: 6baaa8c4e3935676278ff411d0282b82143056fc
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63568473"
---
# <a name="step-2-provide-remote-access-to-on-premises-apps-and-services"></a>الخطوة 2. توفير الوصول عن بعد إلى التطبيقات والخدمات المحلية

إذا كانت مؤسستك تستخدم حل VPN للوصول عن بعد، عادة ما يكون مع خوادم VPN على حافة الشبكة والعملاء VPN المثبتين على أجهزة المستخدمين، يمكن للمستخدمين استخدام اتصالات VPN للوصول عن بعد للوصول إلى التطبيقات المحلية الخوادم. ولكن قد تحتاج إلى تحسين حركة المرور Microsoft 365 المستندة إلى السحابة.

إذا لم يستخدم المستخدمون حل VPN، يمكنك استخدام وكيل تطبيق Azure Active Directory (Azure AD) وS VPN من Azure نقطة إلى موقع (P2S) لتوفير الوصول، استنادا إلى ما إذا كانت جميع تطبيقاتك مستندة إلى الويب.

فيما يلي التكوينات الأساسية للوصول عن بعد:

- أنت تستخدم بالفعل حل VPN للوصول عن بعد.
- أنت لا تستخدم حل VPN للوصول عن بعد وتريد أن يستخدم العاملون عن بعد أجهزة الكمبيوتر الشخصية الخاصة بهم.
- أنت لا تستخدم حل VPN للوصول عن بعد، لديك هوية مختلطة، وأنت بحاجة إلى الوصول عن بعد فقط إلى التطبيقات المستندة إلى الويب.
- لا تستخدم حل VPN للوصول عن بعد، كما تحتاج إلى الوصول إلى التطبيقات في الموقع، وبعضها لا يستند إلى الويب.

راجع هذا الخيار المتدفق للحصول على خيارات تكوين الوصول البعيد التي تمت مناقشتها في هذه المقالة.

:::image type="content" source="../media/empower-people-to-work-remotely-remote-access/empower-people-to-work-remotely-remote-access-flowchart.png" alt-text="ملف انسياب تكوين الوصول عن بعد." lightbox="../media/empower-people-to-work-remotely-remote-access/empower-people-to-work-remotely-remote-access-flowchart.png":::

باستخدام اتصالات الوصول عن بعد، يمكنك أيضا استخدام [سطح](https://support.microsoft.com/help/4028379/windows-10-how-to-use-remote-desktop) المكتب البعيد لتوصيل المستخدمين بكمبيوتر شخصي. على سبيل المثال، يمكن للعامل البعيد استخدام سطح المكتب البعيد للاتصال بجهاز الكمبيوتر الشخصي في مكتبه من جهاز Windows أو iOS أو Android. بمجرد اتصالهم عن بعد، يمكنهم استخدامه كما لو كانوا يجلسون أمامه.

## <a name="optimize-performance-for-remote-access-vpn-clients-to-microsoft-365-cloud-services"></a>تحسين الأداء لعملاء VPN الذين الوصول عن بعد Microsoft 365 السحابية

إذا كان العاملون عن بعد يستخدمون عميل VPN تقليدي للحصول على وصول عن بعد إلى شبكة مؤسستك، فتحقق من أن عميل VPN قد قسم دعم تقسيم التقسيم.

بدون تقسيم عملية النقل، يتم إرسال كل بيانات العمل عن بعد عبر اتصال VPN، حيث يجب إعادة توجيهها إلى أجهزة حواف مؤسستك، ومعالجتها، ثم إرسالها على الإنترنت.

:::image type="content" source="../media/empower-people-to-work-remotely-remote-access/empower-people-to-work-remotely-remote-access-before-tunneling.png" alt-text="حركة مرور الشبكة من عملاء VPN من دون أن يتم ذلك." lightbox="../media/empower-people-to-work-remotely-remote-access/empower-people-to-work-remotely-remote-access-before-tunneling.png":::

Microsoft 365 حركة المرور هذه مسارا غير مباشر عبر مؤسستك، يمكن إعادة توجيهه إلى نقطة إدخال شبكة Microsoft بعيدا عن الموقع الفعلي للعميل VPN. يضيف هذا المسار غير المباشر زمن زمن المرور إلى حركة مرور الشبكة ويخفض الأداء العام.

باستخدام تقسيم التوزيع، يمكنك تكوين عميل VPN لاستبعاد إرسال أنواع معينة من حركة المرور عبر اتصال VPN بشبكة المؤسسة.

لتحسين الوصول إلى Microsoft 365 السحابية، قم بتكوين عملاء VPN المنقسمين المنقسمين لاستبعاد حركة المرور إلى الفئة تحسين Microsoft 365 نقاط النهاية عبر اتصال VPN. لمزيد من المعلومات، [راجع Office 365 نقاط النهاية](../enterprise/microsoft-365-network-connectivity-principles.md#new-office-365-endpoint-categories). راجع [قائمة نقاط](../enterprise/urls-and-ip-address-ranges.md) نهاية الفئة "تحسين".

فيما يتعلق بتدفق حركة المرور الناتج، حيث تتجاوز معظم حركة المرور Microsoft 365 السحابة اتصال VPN.

:::image type="content" source="../media/empower-people-to-work-remotely-remote-access/empower-people-to-work-remotely-remote-access-after-tunneling.png" alt-text="حركة مرور الشبكة من عملاء VPN الذين يتم وضعهم في نواة." lightbox="../media/empower-people-to-work-remotely-remote-access/empower-people-to-work-remotely-remote-access-after-tunneling.png":::

يسمح ذلك للعميل VPN بإرسال البيانات Microsoft 365 خدمة السحابة مباشرة عبر الإنترنت وأقرب نقطة إدخال إلى شبكة Microsoft وتلقيها.

للحصول على مزيد من المعلومات والإرشادات، راجع تحسين Office 365 للمستخدمين البعيدين [الذين يستخدمون تقسيم VPN بشكل جيد](../enterprise/microsoft-365-vpn-split-tunnel.md).

## <a name="deploy-remote-access-when-all-your-apps-are-web-apps-and-you-have-hybrid-identity"></a>نشر الوصول عن بعد عندما تكون جميع تطبيقاتك تطبيقات ويب والهوية المختلطة

إذا لم يكن العاملون عن بعد يستخدمون عميل VPN تقليدي، وكانت حسابات المستخدمين ومجموعاتك المحلية متزامنة مع Azure AD، يمكنك استخدام وكيل تطبيق Azure AD لتوفير وصول آمن عن بعد للتطبيقات المستندة إلى الويب المستضافة على الخوادم المحلية. تتضمن التطبيقات المستندة إلى الويب SharePoint على خوادم Outlook أو خوادم Web Access أو أي تطبيقات أعمال أخرى مستندة إلى الويب.

فيما يلي مكونات وكيل تطبيق Azure AD.

:::image type="content" source="../media/empower-people-to-work-remotely-remote-access/empower-people-to-work-remotely-remote-access-application-proxy.png" alt-text="مكونات وكيل تطبيق Azure AD." lightbox="../media/empower-people-to-work-remotely-remote-access/empower-people-to-work-remotely-remote-access-application-proxy.png":::

لمزيد من المعلومات، راجع نظرة [عامة حول وكيل تطبيق Azure AD](/azure/active-directory/manage-apps/application-proxy).

> [!NOTE]
> لا يتم تضمين وكيل تطبيق Azure AD مع Microsoft 365 اشتراك. يجب عليك الدفع مقابل الاستخدام باستخدام اشتراك Azure منفصل.

## <a name="deploy-remote-access-when-not-all-your-apps-are-web-apps"></a>نشر الوصول عن بعد عندما لا تكون جميع تطبيقاتك تطبيقات ويب

إذا كان العاملون عن بعد لا يستخدمون عميل VPN تقليدي وكان لديك تطبيقات غير مستندة إلى الويب، يمكنك استخدام VPN من Azure نقطة إلى موقع (P2S).

ينشئ اتصال VPN ل P2S اتصالا آمنا من جهاز عامل عن بعد بشبكة مؤسستك عبر شبكة ظاهرية من Azure.

:::image type="content" source="../media/empower-people-to-work-remotely-remote-access/empower-people-to-work-remotely-remote-access-p2s-vpn.png" alt-text="مكونات Azure P2S VPN." lightbox="../media/empower-people-to-work-remotely-remote-access/empower-people-to-work-remotely-remote-access-p2s-vpn.png":::

لمزيد من المعلومات، راجع نظرة [عامة حول P2S VPN](/azure/vpn-gateway/point-to-site-about).

> [!NOTE]
> لا يتم تضمين Azure P2S VPN مع Microsoft 365 اشتراك. يجب عليك الدفع مقابل الاستخدام باستخدام اشتراك Azure منفصل.

## <a name="deploy-windows-365-to-provide-remote-access-for-remote-workers-using-personal-devices"></a>نشر Windows 365 لتوفير الوصول عن بعد للعاملين عن بعد باستخدام الأجهزة الشخصية

لدعم العاملين عن بعد الذين لا يمكنهم سوى استخدام أجهزتهم الشخصية وغير المراقبة، استخدم Windows 365 لإنشاء أسطح مكتب ظاهرية وتخصيصها للمستخدمين لاستخدامها من المنزل. باستخدام اتصال شبكة (OPNC) المحلي، يمكن أن تعمل Windows 365 Cloud على أجهزة الكمبيوتر الشخصية المتصلة بشبكة مؤسستك تماما.

:::image type="content" source="../media/empower-people-to-work-remotely-remote-access/empower-people-to-work-remotely-remote-access-windows-365.png" alt-text="مكونات Windows 365." lightbox="../media/empower-people-to-work-remotely-remote-access/empower-people-to-work-remotely-remote-access-windows-365.png":::

لمزيد من المعلومات، راجع هذه [النظرة العامة Windows 365](/windows-365/overview).

> [!NOTE]
> Windows 365 غير مضمن مع Microsoft 365 اشتراك. يجب عليك الدفع مقابل الاستخدام باستخدام اشتراك منفصل.

## <a name="protect-your-remote-desktop-services-connections-with-the-remote-desktop-services-gateway"></a>حماية اتصالات خدمات سطح المكتب البعيد باستخدام بوابة خدمات سطح المكتب البعيد

إذا كنت تستخدم خدمات سطح المكتب البعيد (RDS) للسماح للموظفين بالاتصال بأجهزة الكمبيوتر المستندة إلى Windows على الشبكة المحلية، يجب استخدام بوابة خدمات سطح المكتب البعيد لـ Microsoft في شبكة edge. تستخدم البوابة أمان طبقة النقل (TLS) لتشفير حركة المرور ومنع الكمبيوتر المحلي الذي يستضيف RDS من أن يتم عرضه مباشرة على الإنترنت.

:::image type="content" source="../media/empower-people-to-work-remotely-remote-access/empower-people-to-work-remotely-remote-access-remote-desktop.png" alt-text="اتصالات خدمات سطح المكتب البعيد مع بوابة خدمات سطح المكتب البعيد." lightbox="../media/empower-people-to-work-remotely-remote-access/empower-people-to-work-remotely-remote-access-remote-desktop.png":::

راجع [هذه المقالة](https://www.microsoft.com/security/blog/2020/04/16/security-guidance-remote-desktop-adoption/) للحصول على مزيد من المعلومات.

## <a name="admin-technical-resources-for-remote-access"></a>الموارد التقنية للمسؤول للوصول عن بعد

- [كيفية تحسين Office 365 البيانات بسرعة للموظفين البعيدين & تقليل الحمل على البنية الأساسية](https://techcommunity.microsoft.com/t5/office-365-blog/how-to-quickly-optimize-office-365-traffic-for-remote-staff-amp/ba-p/1214571)
- [تحسين Office 365 اتصال المستخدمين البعيدين الذين يستخدمون تقسيم VPN](../enterprise/microsoft-365-vpn-split-tunnel.md)

## <a name="results-of-step-2"></a>نتائج الخطوة 2

بعد نشر حل الوصول عن بعد للعاملين عن بعد:

| تكوين الوصول عن بعد | النتائج |
|:-------|:-----|
| حل VPN للوصول عن بعد في مكانه | لقد قمت بتكوين عميل VPN للوصول عن بعد لتقسيم التقسيم وفئة تحسين نقاط Microsoft 365 نقاط النهاية. |
| لا يوجد حل VPN للوصول عن بعد وأنت بحاجة إلى الوصول عن بعد فقط إلى التطبيقات المستندة إلى الويب | لقد قمت بتكوين وكيل تطبيق Azure. |
| لا يوجد حل VPN للوصول عن بعد وأنت بحاجة إلى الوصول إلى التطبيقات في الموقع، وبعضها لا يستند إلى الويب | لقد قمت بتكوين Azure P2S VPN. |
| يستخدم العاملون عن بعد أجهزتهم الشخصية من المنزل | لقد قمت بتكوين Windows 365. |
| يستخدم العاملون عن بعد اتصالات RDS بنظم | لقد قمت بنشر بوابة خدمات سطح المكتب البعيد في شبكة Edge. |
|||

## <a name="next-step"></a>الخطوة التالية

[![الخطوة 3: نشر Microsoft 365 الأمان والتوافق.](../media/empower-people-to-work-remotely/remote-workers-step-grid-3.png)](empower-people-to-work-remotely-security-compliance.md)

تابع مع [الخطوة 3](empower-people-to-work-remotely-security-compliance.md) لنشر Microsoft 365 الأمان والتوافق لحماية التطبيقات والبيانات والأجهزة.
