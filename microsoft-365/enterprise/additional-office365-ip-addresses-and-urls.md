---
title: نقاط النهاية الأخرى غير المضمنة في عنوان IP Office 365 URL وخدمة URL على الويب
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 01/31/2022
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- MOM160
- BCS160
ms.assetid: ''
description: 'ملخص: لا تتضمن خدمة نقاط النهاية الجديدة على الويب بضع نقاط نهاية لسيناريوهات معينة.'
hideEdit: true
ms.openlocfilehash: 0453efbea7957c3cf859c59da7a2cff7db04b4f0
ms.sourcegitcommit: 7fd1bcbd8246501029837e3ea92adea64c3406e1
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/01/2022
ms.locfileid: "63575323"
---
# <a name="other-endpoints-not-included-in-the-office-365-ip-address-and-url-web-service"></a>نقاط النهاية الأخرى غير المضمنة في عنوان IP Office 365 URL وخدمة URL على الويب

تم نشر بعض نقاط نهاية الشبكة مسبقا ولم يتم تضمينها في Office 365 [IP وURL Web Service](microsoft-365-ip-web-service.md). تنشر خدمة الويب نقاط نهاية الشبكة المطلوبة Office 365 عبر شبكة محيطة للمؤسسة. لا يتضمن هذا النطاق حاليا:

1. اتصال الشبكة الذي قد يكون مطلوبا من مركز بيانات Microsoft إلى شبكة عملاء (حركة مرور شبكة خادم مختلط وارد).
2. اتصال الشبكة من الخوادم على شبكة العملاء عبر محيط المؤسسة (حركة مرور شبكة الخادم الخارجي).
3. سيناريوهات شائعة لمتطلبات اتصال الشبكة من مستخدم.
4. متطلبات اتصال دقة DNS (غير مذكورة أدناه).
5. Internet Explorer أو Microsoft Edge الموثوق بها.

وبصرف النظر عن DNS، تكون كل هذه المثيلات اختيارية لمعظم العملاء إلا إذا كنت بحاجة إلى سيناريو محدد تم وصفه.

<br>

****

|صف|الغرض|الوجهة|النوع|
|---|---|---|---|
|1|**[خدمة الاستيراد](https://support.office.com/article/use-network-upload-to-import-your-organization-pst-files-to-office-365-103f940c-0468-4e1a-b527-cc8ad13a5ea6) ل PST واستيراد الملفات**|راجع خدمة [الاستيراد للحصول](https://support.office.com/article/use-network-upload-to-import-your-organization-pst-files-to-office-365-103f940c-0468-4e1a-b527-cc8ad13a5ea6) على مزيد من المتطلبات.|سيناريو الصادر غير الشائع|
|2|**[Microsoft مساعد الإصلاح والدعم Office 365](https://diagnostics.office.com/#/)**|<https://autodiscover.outlook.com> <br> <https://officecdn.microsoft.com> <br> <https://api.diagnostics.office.com> <br> <https://apibasic.diagnostics.office.com> <br> <https://autodiscover-s.outlook.com> <br> <https://cloudcheckenabler.azurewebsites.net> <br> <https://login.live.com> <br> <https://login.microsoftonline.com> <br> <https://login.windows.net> <br> <https://o365diagtelemetry.trafficmanager.net> <br> <https://odc.officeapps.live.com> <br> <https://offcatedge.azureedge.net> <br> <https://officeapps.live.com> <br> <https://outlook.office365.com> <br> <https://outlookdiagnostics.azureedge.net>|حركة مرور الخادم الصادر|
|3|**Azure AD الاتصال (خيار w/SSO)** <p> WinRM & البعيد في PowerShell|بيئة العملاء STS (خادم AD FS ووكيل AD FS) \| منافذ TCP 80 & 443|حركة مرور الخادم الوارد|
|4|**STS** مثل خادم وكيل AD FS (للعملاء المتحدة فقط)|منافذ TCP 443 أو TCP 49443 w/ClientTLS ل TCP (مثل وكيل AD FS) \||حركة مرور الخادم الوارد|
|5|**[Exchange Online المراسلة الموحدة/تكامل SBC](/exchange/voice-mail-unified-messaging/telephone-system-integration-with-um/configuration-notes-for-session-border-controllers)**|ثنائية الاتجاه بين وحدة التحكم في حدود جلسة العمل \*في الموقع و .um.outlook.com|حركة مرور الخادم الصادر فقط|
|6|**ترحيل علبة البريد**<p>عند بدء ترحيل علبة البريد من Exchange المختلطة المحلية إلى [](/exchange/exchange-deployment-assistant) Office 365، سيتصل Office 365 بخادم خدمات ويب ل Exchange (EWS) /Mailbox Replication Services (MRS) المنشور. إذا كنت بحاجة إلى عناوين IP NAT المستخدمة بواسطة خوادم Exchange Online لتقييد الاتصالات الواردة من نطاقات IP المصدر المحددة، يتم سردها في [نطاقات Office 365 URL & URL &](urls-and-ip-address-ranges.md) ضمن منطقة الخدمة "Exchange Online". <p> يجب الحرص على ضمان عدم تأثير الوصول إلى نقاط نهاية EWS المنشورة مثل OWA من خلال ضمان حل وكيل MRS إلى FQDN منفصل وعنوان IP عام قبل تقييد اتصالات TCP 443 من نطاقات IP المصدر المحددة.|وكيل العميل في EWS/MRS <br> منفذ TCP 443|حركة مرور الخادم الوارد|
|7|**[Exchange المشترك](/exchange/exchange-deployment-assistant) المختلط مثل** المشاركة الحرر/الانشغال.|خادم العميل Exchange|حركة مرور الخادم الوارد|
|8|**[Exchange الوكيل المختلط](/exchange/exchange-deployment-assistant)**|STS (STS) في موقع العميل|حركة مرور الخادم الوارد|
|9|يستخدم لتكوين Exchange [المختلط](/exchange/exchange-deployment-assistant)، باستخدام Exchange **[التكوين المختلط](/exchange/hybrid-configuration-wizard)** <p> ملاحظة: نقاط النهاية هذه مطلوبة فقط لتكوين Exchange المختلط|domains.live.com على منافذ TCP 80 & 443، مطلوب فقط لمعالج التكوين المختلط Exchange 2010 SP3 <p> سحابة القطاع الحكومي عناوين IP عالية و DoD: 40.118.209.192/32؛ 168.62.190.41/32 <p> المنتجات التجارية & سحابة القطاع الحكومي: \*.store.core.windows.net; asl.configure.office.com; tds.configure.office.com; mshybridservice.trafficmanager.net ; <br> aka.ms/hybridwizard; <br> \*shcwreleaseprod.blob.core.windows.net/shcw/;|حركة مرور الخادم الصادر فقط|
|10|يتم **استخدام خدمة "كشف** تلقائي" في [Exchange المختلطة](/exchange/exchange-deployment-assistant) مع "المصادقة الحديثة المختلطة" مع Outlook [لنظامي التشغيل iOS وAndroid](/Exchange/clients/outlook-for-ios-and-android/use-hybrid-modern-auth) <p> `*.acompli.net` <br> `*.outlookmobile.com` <br> `*.outlookmobile.us` <br> `52.125.128.0/20` <br> `52.127.96.0/23`|خادم العميل Exchange على TCP 443|حركة مرور الخادم الوارد|
|11|**Exchange مصادقة Azure AD المختلطة**|*.msappproxy.net|حركة مرور الخادم الصادرة فقط في TCP|
|12|Skype for Business في Office 2016 مشاركة الشاشة المستندة إلى الفيديو، والتي تستخدم منافذ UDP. قبل Skype for Business العملاء Office 2013 وRDP المستخدم سابقا عبر منفذ TCP 443.|يفتح منفذ TCP 443 إلى 52.112.0.0/14|Skype for Business العميل الأقدم في Office 2013 والإصدارات السابقة|
|13|**Skype for Business اتصال الخادم المختلط في** الموقع Skype for Business Online|13.107.64.0/18, 52.112.0.0/14 <br> منافذ UDP 50,000-59,999 <br> منافذ TCP 50,000-59,999; 5061|Skype for Business اتصال الخادم الصادر|
|14|**تتطلب خدمة PSTN في** السحابة التي بها اتصال مختلط في الموقع اتصال شبكة مفتوح للمضيفين في الموقع. لمزيد من التفاصيل حول Skype for Business التكوين المختلط عبر الإنترنت|راجع [تخطيط الاتصال المختلط بين Skype for Business Server Office 365](/skypeforbusiness/hybrid/plan-hybrid-connectivity)|Skype for Business الوارد المختلطة|
|15|**مصادقة والهوية FQDN** <p> يجب أن تكون FQDN `secure.aadcdn.microsoftonline-p.com` في Internet Explorer (IE) أو منطقة مواقع Edge الموثوق بها لكي تعمل.||المواقع الموثوق بها|
|16|**Microsoft Teams FQDN** <p> إذا كنت تستخدم Internet Explorer أو Microsoft Edge، ستحتاج إلى تمكين ملفات تعريف الارتباط الأولى وملفات تعريف الارتباط الخاصة ب جهة خارجية وإضافة FQDNs Teams إلى المواقع الموثوق بها. هذا بالإضافة إلى FQDNs وCDN وCDN على مستوى المجموعة والليقية المدرجة في الصف 14. راجع [المشاكل المعروفة Microsoft Teams](/microsoftteams/known-issues) للحصول على مزيد من المعلومات.||المواقع الموثوق بها|
|17|**SharePoint عبر الإنترنت OneDrive for Business FQDN** <p> يجب أن sharepoint.com FQDN مع '\<tenant\>' في FQDN في IE أو منطقة مواقع Edge الموثوق بها للعميل لكي تعمل. بالإضافة إلى FQDNs وCDN وCDN على مستوى المجموعة المذكورة في الصف 14، ستحتاج أيضا إلى إضافة نقاط النهاية هذه.||المواقع الموثوق بها|
|18|**Yammer**  <br> Yammer يتوفر فقط في المستعرض ويتطلب من المستخدم المصادق عليه المرور عبر وكيل. يجب Yammer FQDN في IE أو منطقة مواقع Edge الموثوق بها للعميل لكي تعمل.||المواقع الموثوق بها|
|19|استخدم **[Azure AD الاتصال](/azure/active-directory/hybrid/)** لمزامنة حسابات المستخدمين في الموقع إلى Azure AD.|راجع [المنافذ والبروتوكولات](/azure/active-directory/hybrid/reference-connect-ports) المطلوبة للهوية المختلطة، وإصلاح اتصال [Azure AD](/azure/active-directory/hybrid/tshoot-connect-connectivity)[، و Azure AD الاتصال تثبيت عامل حماية](/azure/active-directory/hybrid/how-to-connect-health-agent-install#outbound-connectivity-to-the-azure-service-endpoints).|حركة مرور الخادم الصادر فقط|
|20|**[Azure AD الاتصال](/azure/active-directory/hybrid/)** مع 21 ViaNet في الصين لمزامنة حسابات المستخدمين في الموقع مع Azure AD.|\*.digicert.com:80 <BR> \*.entrust.net:80 <BR> \*.chinacloudapi.cn:443 <br> secure.aadcdn.partner.microsoftonline-p.cn:443 <br> \*.partner.microsoftonline.cn:443 <p> راجع أيضا [استكشاف مشاكل اتصال Azure AD وإصلاحها](https://docs.azure.cn/zh-cn/active-directory/hybrid/tshoot-connect-connectivity).|حركة مرور الخادم الصادر فقط|
|21|**Microsoft Stream** (يحتاج إلى الرمز المميز لمستخدم Azure AD). <br> Office 365 حول العالم (بما في ذلك سحابة القطاع الحكومي)|\*.cloudapp.net <br> \*.api.microsoftstream.com <br> \*.notification.api.microsoftstream.com <br> amp.azure.net <br> api.microsoftstream.com <br> az416426.vo.msecnd.net <br> s0.assets-yammer.com <br> vortex.data.microsoft.com <br> web.microsoftstream.com <br> منفذ TCP 443|حركة مرور الخادم الوارد|
|22|استخدم **خادم المصادقة** متعددة العوامل لطلبات المصادقة متعددة العوامل، كل من عمليات التثبيت الجديدة للخادم وإعداده باستخدام خدمات مجال Active Directory (AD DS).|راجع [بدء استخدام خادم المصادقة متعددة العوامل من Azure AD](/azure/active-directory/authentication/howto-mfaserver-deploy#plan-your-deployment).|حركة مرور الخادم الصادر فقط|
|23|**تغيير Graph Microsoft** <p> يمكن للمطورين استخدام [إعلامات التغيير](/graph/webhooks?context=graph%2fapi%2f1.0&view=graph-rest-1.0) للاشتراك في الأحداث في Microsoft Graph.|Public Cloud: 52.159.23.209, 52.159.17.84, 52.147.213.251, 52.147.213.181, 13.85.192.59, 13.85.192.123, 13.89.108.233, 13.89.104.147, 20.96.21.67, 20.69.245.215, 137.135.11.161, 137.135.11.116, 52.159.107.50, 52.159.107.4, 52.229.38.131, 52.183.67.212, 52.142.114.29, 52.142.115.31, 51.124.75.43, 51.124.73.177, 20.44.210.83, 20.44.210.146, 40.80.232.177, 40.80.232.118, 20.48.12.75, 20.48.11.201, 104.215.13.23, 104.215.6.169, 52.148.24.136, 52.148.27.39, 40.76.162.99, 40.76.162.42 , 40.74.203.28, 40.74.203.27, 13.86.37.15, 52.154.246.238, 20.96.21.98, 20.96.21.115, 137.135.11.222, 137.135.11.250, 52.159.109.205, 52.159.102.72, 52.151.30.78, 52.191.173.85, 51.104.159.213, 51.104.159.181, 51.138.90.7, 51.138.90.52, 52.148.115.48, 52.148.114.238, 40.80.233.14, 40.80.239.196, 20.48.14.35, 20.48.15.147, 104.215.18.55, 104.215.12.254, 20.199.102.157, 20.199.102.73, 13.87.81.123, 13.87.81.35, 20.111.9.46, 20.111.9.77, 13.87.81.133, 13.87.81.141 <p> Microsoft Cloud for US Government: 52.244.33.45، 52.244.35.174، 52.243.157.104، 52.243.157.105، 52.182.25.254، 52.182.25.110، 52.181.25.67، 52.181.25.66، 52.244.111.156، 52.244.111.170، 52.243.147.249، 52.243.148.1 9، 52.182.32.51، 52.182.32.143، 52.181.24.199، 52.181.24.220 <p> Microsoft Cloud China الذي يتم تشغيله بواسطة 21Vianet: 42.159.72.35، 42.159.72.47، 42.159.180.55، 42.159.180.56، 40.125.138.23، 40.125.136.69، 40.72.155.199، 40.72.155.216 <br> منفذ TCP 443 <p> ملاحظة: يمكن للمطورين تحديد منافذ مختلفة عند إنشاء الاشتراكات.|حركة مرور الخادم الوارد|
|24|**مؤشر حالة اتصال الشبكة**<p>يستخدمه Windows 10 و11 لتحديد ما إذا كان الكمبيوتر متصلا بالإنترنت (لا ينطبق على العملاء Windows غير المتصلين). عندما يتعذر الوصول إلى عنوان URL هذا، سيفترض Windows أنه غير متصل بالإنترنت ولن تحاول تطبيقات M365 للمؤسسات التحقق من حالة التنشيط، مما يؤدي إلى فشل الاتصالات Exchange وخدمات أخرى.|www.mstfconnecttest.com <br> 13.107.4.52<p>راجع أيضا [إدارة نقاط نهاية](/windows/privacy/manage-windows-11-endpoints) الاتصال Windows 11 Enterprise نقاط نهاية الاتصال Windows 10 Enterprise [21H2](/windows/privacy/manage-windows-21h2-endpoints).|حركة مرور الخادم الصادر فقط|
|

## <a name="related-topics"></a>مواضيع ذات صلة

[إدارة Office 365 نقاط النهاية](managing-office-365-endpoints.md)
  
[مراقبة Microsoft 365 الاتصال](./monitor-connectivity.md)
  
[اتصال العميل](https://support.office.com/article/client-connectivity-4232abcf-4ae5-43aa-bfa1-9a078a99c78b)
  
[شبكات تسليم المحتوى](https://support.office.com/article/content-delivery-networks-0140f704-6614-49bb-aa6c-89b75dcd7f1f)
  
[نطاقات IP والعلامات الخاصة ب Azure – السحابة العامة](https://www.microsoft.com/download/details.aspx?id=56519)

[نطاقات IP والعلامات الخاصة ب Azure – Us Government Cloud](https://www.microsoft.com/download/details.aspx?id=57063)

[نطاقات IP والعلامات الخاصة ب Azure – Germany Cloud](https://www.microsoft.com/download/details.aspx?id=57064)

[نطاقات IP والعلامات الخاصة ب Azure – China Cloud](https://www.microsoft.com/download/details.aspx?id=57062)
  
[Microsoft Public IP Space](https://www.microsoft.com/download/details.aspx?id=53602)
