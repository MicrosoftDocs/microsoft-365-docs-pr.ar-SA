---
title: تأمين Teams الوسائط من أجل تقسيم VPN
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 3/3/2022
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- remotework
f1.keywords:
- NOCSH
description: تأمين Teams الوسائط من أجل تقسيم VPN
ms.openlocfilehash: 0f16ed8f7f9721a79375f05f7b889bc8aab2d824
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63704933"
---
# <a name="securing-teams-media-traffic-for-vpn-split-tunneling"></a>تأمين Teams الوسائط من أجل تقسيم VPN

>[!NOTE]
>هذه المقالة هي جزء من مجموعة من المقالات التي تعالج Microsoft 365 للمستخدمين البعيدين.

>- للحصول على نظرة عامة حول استخدام تقسيم VPN لتحسين Microsoft 365 للمستخدمين البعيدين، راجع نظرة عامة[: تقسيم VPN](microsoft-365-vpn-split-tunnel.md) للتحكم Microsoft 365.
>- للحصول على إرشادات مفصلة حول تنفيذ تقسيم VPN، راجع تنفيذ تقسيم [VPN Microsoft 365](microsoft-365-vpn-implement-split-tunnel.md).
>- للحصول على قائمة تفصيلية بسيناريوهات تقسيم VPN التي تم تقسيمها، راجع سيناريوهات تقسيم VPN الشائعة [لسيناريوهات](microsoft-365-vpn-common-scenarios.md) تقسيم VPN Microsoft 365.
>- للحصول على معلومات حول كيفية تكوين الدفق والأحداث المباشرة في بيئات VPN، راجع اعتبارات خاصة للبث والأحداث المباشرة [في بيئات VPN](microsoft-365-vpn-stream-and-live-events.md).
>- للحصول على معلومات حول تحسين Microsoft 365 المستأجر على مستوى العالم للمستخدمين في الصين، راجع Microsoft 365 تحسين أداء [المستخدمين في الصين](microsoft-365-networking-china.md).

قد Microsoft Teams بعض المسؤولين معلومات مفصلة حول كيفية عمل تدفقات الاتصال في Teams استخدام نموذج تقسيمي للتدفقات وكيفية تأمين الاتصالات.

## <a name="configuration"></a>تكوين

بالنسبة للمكالمات والاجتماعات، طالما أن الشبكة الفرعية لتحسين IP المطلوبة ل وسائط Teams في مكانها الصحيح في جدول المسار، عندما يتصل Teams بدالة [GetBestRoute](/windows/win32/api/iphlpapi/nf-iphlpapi-getbestroute) لتحديد الواجهة المحلية التي تتوافق مع المسار الذي يجب أن تستخدمه لوجهة معينة، سيتم إرجاع الواجهة المحلية لوجهات Microsoft في كتل IP من Microsoft المذكورة أعلاه.

تسمح بعض برامج عميل VPN بالتعامل مع التوجيه استنادا إلى عنوان URL. ومع ذلك Teams لا يوجد عنوان URL مقترن بترحيل الوسائط، لذا يجب أن يتم التحكم في التوجيه لحركة المرور هذه باستخدام عناوين IP الفرعية.

في سيناريوهات معينة، غالبا ما تكون غير مرتبطة Teams العميل، لا تزال حركة الوسائط تجتاز مسار VPN حتى مع المسارات الصحيحة في مكانها. إذا واجهت هذا السيناريو، فمن المفترض أن يكون استخدام قاعدة جدار الحماية لمنع Teams IP الفرعية أو المنافذ من استخدام VPN كافيا.

>[!IMPORTANT]
>لضمان Teams توجيه حركة الوسائط عبر الأسلوب المطلوب في كل سيناريوهات VPN، يرجى التأكد من أن المستخدمين قيد تشغيل إصدار عميل Microsoft Teams **1.3.00.13565** أو الإصدارات الأحدث. يتضمن هذا الإصدار تحسينات في كيفية اكتشاف العميل لمسارات الشبكة المتوفرة.

يتم تنفيذ الإشارة إلى نقل البيانات عبر HTTPS ولا يتحسس زمن الوصول مثل نقل الوسائط، كما يتم وضع علامة السماح في بيانات  URL/IP وبالتالي يمكن توجيهه بأمان عبر عميل VPN إذا أردت ذلك.

>[!NOTE]
>Microsoft Edge **96** والأعلى من ذلك إلى دعم تقسيم VPN لتكاتف حركة مرور النظير إلى النظير. وهذا يعني أن العملاء يمكنهم الاستفادة من تقسيم VPN Teams ويب على Edge، على سبيل المثال. يمكن للعملاء الذين يرغبون في إعداده لمواقع الويب التي تعمل على Edge تحقيق ذلك من خلال اتخاذ خطوة إضافية لتمكين نهج Edge [WebRtcRespectOsRoutingTableEnabled](/deployedge/microsoft-edge-policies#webrtcrespectosroutingtableenabled) .

### <a name="security"></a>الأمان

إحدى الوسيطات الشائعة لتجنب الانقسامات هو أن القيام بذلك أقل أمانا، أي لن تستفيد أي حركة مرور لا تمر عبر شبكة VPN من أي نظام تشفير يتم تطبيقه على نظام VPN، وبالتالي فهي أقل أمانا.

وتتمثل الوسيطة الرئيسية في هذا الأمر في أن نقل الوسائط مشفر بالفعل عبر بروتوكول النقل _الآمن Real-Time (SRTP)،_ وهو ملف تعريف لبروتوكول نقل Real-Time (RTP) يوفر السرية والمصادقة وإعادة عرض الحماية من الهجمات لنقل البيانات في RTP. يعتمد SRTP نفسه على مفتاح جلسة عمل تم إنشاؤه عشوائيا، يتم تبادله عبر قناة إشارات TLS الآمنة. يتم تناول ذلك بتفاصيل كبيرة في [دليل](/skypeforbusiness/optimizing-your-network/security-guide-for-skype-for-business-online) الأمان هذا، ولكن القسم الأساسي الذي يهمك هو تشفير الوسائط.

يتم تشفير حركة مرور الوسائط باستخدام SRTP، الذي يستخدم مفتاح جلسة عمل تم إنشاؤه بواسطة منشئ أرقام عشوائي آمن ومتبادل باستخدام قناة TLS للإشارة. بالإضافة إلى ذلك، يتم أيضا تشفير الوسائط التي تتدفق في الاتجاهين بين "خادم وساطة" واتجاهها الداخلي التالي باستخدام SRTP.

Skype for Business Online اسم المستخدم/كلمات المرور للوصول الآمن إلى ترحيلات الوسائط عبر العطف باستخدام الترحيلات حول _NAT (TURN)_. تبادل ترحيلات الوسائط اسم المستخدم/كلمة المرور عبر قناة SIP آمنة من TLS. تجدر الإشارة إلى أنه على الرغم من أنه قد يتم استخدام شبكة VPN لتوصيل العميل بشبكة الشركة، إلا أن حركة المرور لا تزال بحاجة إلى التدفق في نموذج SRTP الخاص بها عند مغادرتها شبكة الشركة للوصول إلى الخدمة.

يمكن العثور على معلومات Teams تقليل المشاكل الأمنية الشائعة مثل الصوت أو الأدوات المساعدة في جلسة العمل لهجمات تضخيم _NAT (STUN)_ في [5.1](/openspecs/office_protocols/ms-ice2/69525351-8c68-4864-b8a6-04bfbc87785c) اعتبارات الأمان للمنفذين.

يمكنك أيضا القراءة حول عناصر التحكم في الأمان الحديثة في سيناريوهات العمل عن بعد في طرق بديلة لمحترفي الأمان تكنولوجيا المعلومات لتحقيق عناصر تحكم الأمان الحديثة في سيناريوهات العمل عن بعد الفريدة اليوم [(مدونة فريق أمان Microsoft)](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/).

### <a name="testing"></a>الاختبار

بمجرد وضع النهج في مكانه، يجب أن تؤكد أنه يعمل كما هو متوقع. هناك طرق متعددة لاختبار المسار الذي تم تعيينه بشكل صحيح لاستخدام اتصال الإنترنت المحلي:

- تشغيل اختبار [Microsoft 365](https://aka.ms/netonboard) الذي سيتم تشغيل اختبارات الاتصال لك بما في ذلك تتبع المسارات كما هو أعلاه. نحن نعمل أيضا على إضافة اختبارات VPN إلى هذه الأداة التي يجب أن توفر أيضا نتائج تحليلات إضافية.

- يجب أن **يظهر تتبع** بسيط لنقطة نهاية ضمن نطاق الانقسام المنقسم المسار الذي تم اتخاذه، على سبيل المثال:

  ```powershell
  tracert worldaz.tr.teams.microsoft.com
  ```

  يجب أن ترى بعد ذلك مسارا عبر ISP المحلي إلى نقطة النهاية هذه التي يجب أن يتم حلها إلى IP في نطاقات Teams التي قمنا بتكوينها لتقسيم التقسيم.

- التقط لقطة شبكة باستخدام أداة مثل Wireshark. قم بالتصفية على UDP أثناء المكالمة ويجب أن ترى حركة المرور تتدفق إلى IP في Teams **تحسين**. إذا كان يتم استخدام خدمة VPN في عملية النقل هذه، فلن تكون حركة النقل في الوسائط مرئية في عملية التتبع.

## <a name="additional-support-logs"></a>سجلات الدعم الإضافية

إذا كنت بحاجة إلى مزيد من البيانات من أجل استكشاف الأخطاء وإصلاحها، أو إذا كنت تطلب المساعدة من دعم Microsoft، فمن المفترض أن يسمح لك الحصول على المعلومات التالية بالتسريع في العثور على حل. يمكن أن تساعدك مجموعة أدوات البرنامج **النصي Windows TSS** المستندة إلى CMD في تجميع السجلات ذات الصلة بطريقة بسيطة. يمكن العثور على الأداة والتعليمات حول الاستخدام في <https://aka.ms/TssTools>.

## <a name="related-articles"></a>المقالات ذات الصلة

[نظرة عامة: تقسيم VPN إلى تقسيم Microsoft 365](microsoft-365-vpn-split-tunnel.md)

[تنفيذ تقسيم VPN لتنفيذ Microsoft 365](microsoft-365-vpn-implement-split-tunnel.md)

[سيناريوهات تقسيم VPN الشائعة للانقسام Microsoft 365](microsoft-365-vpn-common-scenarios.md)

[اعتبارات خاصة للبث والأحداث المباشرة في بيئات VPN](microsoft-365-vpn-stream-and-live-events.md)

[Microsoft 365 تحسين أداء المستخدمين في الصين](microsoft-365-networking-china.md)

[Microsoft 365 "مبادئ اتصال الشبكة"](microsoft-365-network-connectivity-principles.md)

[تقييم Microsoft 365 الشبكة](assessing-network-connectivity.md)

[Microsoft 365 الشبكة وضبط الأداء](network-planning-and-performance.md)

[طرق بديلة لمحترفي الأمان تكنولوجيا المعلومات لتحقيق عناصر التحكم الحديثة في الأمان في سيناريوهات العمل عن بعد الفريدة اليوم (مدونة فريق أمان Microsoft)](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/)

[تحسين أداء VPN في Microsoft: Windows 10 ملفات تعريف VPN للسماح باتصالات التشغيل التلقائي](https://www.microsoft.com/itshowcase/enhancing-remote-access-in-windows-10-with-an-automatic-vpn-profile)

[تشغيل VPN: كيف تحافظ Microsoft على اتصال القوى العاملة البعيدة](https://www.microsoft.com/itshowcase/blog/running-on-vpn-how-microsoft-is-keeping-its-remote-workforce-connected/?elevate-lv)

[شبكة Microsoft العامة](/azure/networking/microsoft-global-network)
