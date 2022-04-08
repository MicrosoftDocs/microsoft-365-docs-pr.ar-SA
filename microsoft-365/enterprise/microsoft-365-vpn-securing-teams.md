---
title: تأمين نقل وسائط Teams للاتصال النفقي المنقسم لشبكة VPN
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
description: تأمين نقل وسائط Teams للاتصال النفقي المنقسم لشبكة VPN
ms.openlocfilehash: 715d5e02ef01db9ef1c75a063ef5a2771d425f5c
ms.sourcegitcommit: 1c5f9d17a8b095cd88b23f4874539adc3ae021de
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/08/2022
ms.locfileid: "64715374"
---
# <a name="securing-teams-media-traffic-for-vpn-split-tunneling"></a>تأمين نقل وسائط Teams للاتصال النفقي المنقسم لشبكة VPN

>[!NOTE]
>تشكل هذه المقالة جزءا من مجموعة من المقالات التي تتناول تحسين Microsoft 365 للمستخدمين البعيدين.

>- للحصول على نظرة عامة حول استخدام نفق انقسام VPN لتحسين الاتصال Microsoft 365 للمستخدمين البعيدين، راجع [نظرة عامة: نفق انقسام VPN Microsoft 365](microsoft-365-vpn-split-tunnel.md).
>- للحصول على إرشادات مفصلة حول تنفيذ نفق انقسام VPN، راجع [تنفيذ نفق انقسام VPN Microsoft 365](microsoft-365-vpn-implement-split-tunnel.md).
>- للحصول على قائمة مفصلة بسيناريوهات الاتصال النفقي المنقسم ل VPN، راجع [سيناريوهات الاتصال النفقي لتقسيم VPN الشائعة Microsoft 365](microsoft-365-vpn-common-scenarios.md).
>- للحصول على معلومات حول كيفية تكوين Stream والأحداث المباشرة في بيئات VPN، راجع [الاعتبارات الخاصة ل Stream والأحداث المباشرة في بيئات VPN](microsoft-365-vpn-stream-and-live-events.md).
>- للحصول على معلومات حول تحسين أداء المستأجر Microsoft 365 في جميع أنحاء العالم للمستخدمين في الصين، راجع [تحسين أداء Microsoft 365 لمستخدمي الصين](microsoft-365-networking-china.md).

قد يحتاج بعض مسؤولي Microsoft Teams إلى معلومات مفصلة حول كيفية عمل تدفقات المكالمات في Teams باستخدام نموذج نفق منقسم وكيفية تأمين الاتصالات.

## <a name="configuration"></a>التكوين

بالنسبة إلى كل من المكالمات والاجتماعات، طالما أن الشبكات الفرعية لتحسين IP المطلوبة لوسائط Teams في مكانها الصحيح في جدول التوجيه، عندما يستدعي Teams الدالة [GetBestRoute](/windows/win32/api/iphlpapi/nf-iphlpapi-getbestroute) لتحديد الواجهة المحلية التي تتوافق مع المسار الذي يجب استخدامه لوجهة معينة، سيتم إرجاع الواجهة المحلية لوجهات Microsoft في كتل MICROSOFT IP المذكورة أعلاه.

تسمح بعض برامج عميل VPN بمعالجة التوجيه استنادا إلى عنوان URL. ومع ذلك، Teams نسبة استخدام الوسائط ليس لها عنوان URL مقترن بها، لذلك يجب أن يتم التحكم في توجيه نسبة استخدام الشبكة هذه باستخدام الشبكات الفرعية IP.

في سيناريوهات معينة، غالبا ما تكون غير مرتبطة بتكوين العميل Teams، لا تزال حركة مرور الوسائط تجتاز نفق VPN حتى مع المسارات الصحيحة. إذا واجهت هذا السيناريو، فإن استخدام قاعدة جدار حماية لحظر الشبكات الفرعية أو المنافذ Teams IP من استخدام VPN يجب أن يكون كافيا.

>[!IMPORTANT]
>لضمان توجيه حركة مرور الوسائط Teams عبر الأسلوب المطلوب في جميع سيناريوهات VPN، يرجى التأكد من تشغيل المستخدمين Microsoft Teams إصدار العميل **1.3.00.13565** أو الإصدارات الأحدث. يتضمن هذا الإصدار تحسينات في كيفية اكتشاف العميل لمسارات الشبكة المتوفرة.

يتم تنفيذ الإشارة إلى نسبة استخدام الشبكة عبر HTTPS وهي ليست حساسة لزمن الانتقال مثل حركة مرور الوسائط ويتم وضع **علامة السماح في** بيانات عنوان URL/IP ومن ثم يمكن توجيهها بأمان من خلال عميل VPN إذا رغبت في ذلك.

>[!NOTE]
>يدعم Microsoft Edge **96 وما فوق** أيضا نفق VPN المنقسم لنسبة استخدام الشبكة من نظير إلى نظير. وهذا يعني أنه يمكن للعملاء الاستفادة من الاتصال النفقي المنقسم VPN لعملاء الويب Teams على Edge، على سبيل المثال. يمكن للعملاء الذين يرغبون في إعداده لمواقع الويب التي تعمل على Edge تحقيق ذلك من خلال اتخاذ الخطوة الإضافية لتعطيل نهج Edge [WebRtcRespectOsRoutingTableEnabled](/deployedge/microsoft-edge-policies#webrtcrespectosroutingtableenabled) .

### <a name="security"></a>الأمان

إحدى الوسيطة الشائعة لتجنب الأنفاق المنقسمة هي أنه من الأقل أمانا القيام بذلك، على سبيل المثال لن تستفيد أي حركة مرور لا تمر عبر نفق VPN من أي مخطط تشفير يتم تطبيقه على نفق VPN، وبالتالي فهي أقل أمانا.

الوسيطة المقابلة الرئيسية لهذا هي أن حركة مرور الوسائط مشفرة بالفعل عبر _بروتوكول النقل الآمن Real-Time (SRTP)،_ وهو ملف تعريف لبروتوكول النقل Real-Time (RTP) الذي يوفر السرية والمصادقة وإعادة تشغيل الحماية من الهجوم لنسبة استخدام الشبكة RTP. يعتمد SRTP نفسه على مفتاح جلسة عمل تم إنشاؤه عشوائيا، والذي يتم تبادله عبر قناة الإشارة الآمنة TLS. يتم تناول هذا بالتفصيل الكبير ضمن [دليل الأمان هذا](/skypeforbusiness/optimizing-your-network/security-guide-for-skype-for-business-online)، ولكن القسم الأساسي الذي يهمك هو تشفير الوسائط.

يتم تشفير حركة مرور الوسائط باستخدام SRTP، والذي يستخدم مفتاح جلسة عمل تم إنشاؤه بواسطة منشئ أرقام عشوائي آمن ومتبادل باستخدام قناة TLS الإشارة. بالإضافة إلى ذلك، يتم أيضا تشفير الوسائط المتدفقة في كلا الاتجاهين بين خادم التوسط والوثبة التالية الداخلية الخاصة به باستخدام SRTP.

Skype for Business Online ينشئ اسم المستخدم/كلمات المرور للوصول الآمن إلى ترحيلات الوسائط عبر _اجتياز باستخدام المرحلات حول NAT (TURN)._ تتبادل ترحيلات الوسائط اسم المستخدم/كلمة المرور عبر قناة SIP مؤمنة بواسطة TLS. تجدر الإشارة إلى أنه على الرغم من أنه قد يتم استخدام نفق VPN لتوصيل العميل بشبكة الشركة، فإن نسبة استخدام الشبكة لا تزال بحاجة إلى التدفق في نموذج SRTP الخاص بها عندما تغادر شبكة الشركة للوصول إلى الخدمة.

يمكن العثور على معلومات حول كيفية Teams التخفيف من المخاوف الأمنية الشائعة مثل الصوت أو _أدوات اجتياز الجلسة لهجمات تضخيم NAT (STUN)_ في [5.1 اعتبارات أمنية للمنفذين](/openspecs/office_protocols/ms-ice2/69525351-8c68-4864-b8a6-04bfbc87785c).

يمكنك أيضا القراءة حول عناصر التحكم في الأمان الحديثة في سيناريوهات العمل عن بعد [بطرق بديلة لمحترفي الأمان و تكنولوجيا المعلومات لتحقيق عناصر تحكم الأمان الحديثة في سيناريوهات العمل عن بعد الفريدة اليوم (مدونة فريق أمان Microsoft)](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/).

### <a name="testing"></a>اختبار

بمجرد تطبيق النهج، يجب عليك تأكيد أنه يعمل كما هو متوقع. هناك طرق متعددة لاختبار المسار الذي تم تعيينه بشكل صحيح لاستخدام اتصال الإنترنت المحلي:

- قم بتشغيل [اختبار الاتصال Microsoft 365](https://aka.ms/netonboard) الذي سيقوم بتشغيل اختبارات الاتصال لك بما في ذلك مسارات التتبع كما هو موضح أعلاه. نضيف أيضا اختبارات VPN إلى هذه الأدوات التي يجب أن توفر أيضا رؤى إضافية.

- يجب أن يظهر **التتبع** البسيط إلى نقطة نهاية داخل نطاق النفق المنقسم المسار الملتقط، على سبيل المثال:

  ```powershell
  tracert worldaz.tr.teams.microsoft.com
  ```

  يجب أن تشاهد بعد ذلك مسارا عبر ISP المحلي إلى نقطة النهاية هذه التي يجب أن تحل إلى IP في نطاقات Teams التي قمنا بتكوينها للنفق المقسم.

- التقاط شبكة باستخدام أداة مثل Wireshark. قم بالتصفية على UDP أثناء مكالمة ويجب أن ترى نسبة استخدام الشبكة تتدفق إلى IP **في نطاق تحسين** Teams. إذا كان يتم استخدام نفق VPN لنسبة استخدام الشبكة هذه، فلن تكون حركة مرور الوسائط مرئية في التتبع.

## <a name="additional-support-logs"></a>سجلات دعم إضافية

إذا كنت بحاجة إلى مزيد من البيانات لاستكشاف الأخطاء وإصلاحها، أو كنت تطلب المساعدة من دعم Microsoft، فإن الحصول على المعلومات التالية يجب أن يسمح لك بتسريع العثور على حل. يمكن أن تساعدك مجموعة **أدوات البرنامج النصي العام لاستكشاف الأخطاء وإصلاحها المستندة إلى CMD Windows دعم** Microsoft على جمع السجلات ذات الصلة بطريقة بسيطة. يمكن العثور على الأداة والتعليمات عند الاستخدام في <https://aka.ms/TssTools>.

## <a name="related-articles"></a>المقالات ذات الصلة

[نظرة عامة: الاتصال النفقي المنقسم ل VPN Microsoft 365](microsoft-365-vpn-split-tunnel.md)

[تنفيذ نفق انقسام VPN Microsoft 365](microsoft-365-vpn-implement-split-tunnel.md)

[سيناريوهات الاتصال النفقي لتقسيم VPN الشائعة Microsoft 365](microsoft-365-vpn-common-scenarios.md)

[اعتبارات خاصة ل Stream والأحداث المباشرة في بيئات VPN](microsoft-365-vpn-stream-and-live-events.md)

[تحسين الأداء Microsoft 365 لمستخدمي الصين](microsoft-365-networking-china.md)

[مبادئ اتصال الشبكة Microsoft 365](microsoft-365-network-connectivity-principles.md)

[تقييم اتصال الشبكة Microsoft 365](assessing-network-connectivity.md)

[Microsoft 365 الشبكة وضبط الأداء](network-planning-and-performance.md)

[طرق بديلة لمحترفي الأمان و تكنولوجيا المعلومات لتحقيق عناصر التحكم الأمنية الحديثة في سيناريوهات العمل عن بعد الفريدة اليوم (مدونة فريق أمان Microsoft)](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/)

[تحسين أداء VPN في Microsoft: استخدام ملفات تعريف VPN Windows 10 للسماح باتصالات التشغيل التلقائي](https://www.microsoft.com/itshowcase/enhancing-remote-access-in-windows-10-with-an-automatic-vpn-profile)

[التشغيل على VPN: كيف تحافظ Microsoft على اتصال القوى العاملة عن بعد](https://www.microsoft.com/itshowcase/blog/running-on-vpn-how-microsoft-is-keeping-its-remote-workforce-connected/?elevate-lv)

[شبكة Microsoft العمومية](/azure/networking/microsoft-global-network)
