---
title: قائمة أحداث API في Microsoft 365 Defender
description: تعرف على كيفية سرد أحداث API في Microsoft 365 Defender
keywords: قائمة، حادث، أحداث، api
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.custom: api
ms.openlocfilehash: 03fbcb70588158919b54c9153b5d8d32d416cc75
ms.sourcegitcommit: 6f3bc00a5cf25c48c61eb3835ac069e9f41dc4db
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 01/24/2022
ms.locfileid: "63575736"
---
# <a name="list-incidents-api-in-microsoft-365-defender"></a>قائمة أحداث API في Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**ينطبق على:**

- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> [!IMPORTANT]
> تتعلق بعض المعلومات بالمنتج الذي تم إصداره مسبقا والذي قد يتم تعديله بشكل كبير قبل طرحه تجاريا. لا تقدم Microsoft أي ضمانات، صريحة أو ضمنية، فيما يتعلق بالمعلومات المتوفرة هنا.

## <a name="api-description"></a>وصف API

تسمح لك API لحوادث القائمة بالفرز عبر الأحداث لإنشاء استجابة مخبرة حول الأمان الإلكتروني. ويعرض مجموعة من الأحداث التي تم وضع علامة عليها في شبكتك، ضمن النطاق الزمني الذي حددته في نهج استبقاء البيئة. يتم عرض الأحداث الأخيرة في أعلى القائمة. يحتوي كل حادث على صفيف من التنبيهات ذات الصلة والكيانات ذات الصلة بها.

تدعم API عوامل **تشغيل OData** التالية:

- `$filter``lastUpdateTime`على الخصائص و `createdTime`و `status`و `assignedTo`
- `$top`، مع الحد الأقصى لقيمة **100**
- `$skip`

## <a name="limitations"></a>القيود

1. الحد الأقصى لحجم الصفحة **هو 100 حادث**.
2. الحد الأقصى لعدد الطلبات هو **50 مكالمة في الدقيقة** **و1500 مكالمة في الساعة**.

## <a name="permissions"></a>الأذونات

أحد الأذونات التالية مطلوبة لاستدعاء API هذه. لمعرفة المزيد، بما في ذلك كيفية اختيار الأذونات، راجع [الوصول Microsoft 365 Defender واجهات برمجة التطبيقات](api-access.md)

نوع الإذن|الإذن|اسم عرض الأذونات
---|---|---
Application|Incident.read.All|قراءة كل الأحداث
Application|Incident.ReadWrite.All|قراءة كل الأحداث وكتابتها
مفوض (حساب العمل أو المدرسة)|Incident.Read|قراءة الأحداث
مفوض (حساب العمل أو المدرسة)|Incident.ReadWrite|أحداث القراءة والكتابة

> [!NOTE]
> عند الحصول على رمز مميز باستخدام بيانات اعتماد المستخدم:
>
> - يجب أن يكون لدى المستخدم إذن عرض للحوادث في المدخل.
> - ستتضمن الاستجابة فقط الأحداث التي يتعرض لها المستخدم.

## <a name="http-request"></a>طلب HTTP

```HTTP
GET /api/incidents
```

## <a name="request-headers"></a>طلب رؤوس

الاسم|النوع|الوصف
---|---|---
التخويل|سلسلة|حامل {token}. **مطلوب**

## <a name="request-body"></a>طلب الحصول على "هيئة"

بلا.

## <a name="response"></a>الاستجابة

إذا نجح هذا الأسلوب، فيرجع `200 OK`، وقائمة بالحوادث [في جزء](api-incident.md) الاستجابة.

## <a name="schema-mapping"></a>تعيين المخطط

### <a name="incident-metadata"></a>بيانات تعريف الحادث

اسم الحقل|الوصف|قيمة المثال
---|---|---
incidentId|معرف فريد لتمثيل الحادث|924565
redirectIncidentId|ولا يتم ملؤها إلا في حالة تجميع حادث مع حادث آخر، كجزء من منطق معالجة الحادث.|924569
incidentName|قيمة السلسلة متوفرة لكل حادث.|نشاط برامج الفدية الضارة
createdTime|وقت إنشاء الحادث للمرة الأولى.|2020-09-06T14:46:57.0733333Z
lastUpdateTime|الوقت الذي تم فيه آخر تحديث للحادث على الواجهة الخلفية. <p> يمكن استخدام هذا الحقل عند تعيين معلمة الطلب لنطاق الوقت الذي يتم فيه استرداد الأحداث.|2020-09-06T14:46:57.29Z
assignedTo|مالك الحادث، أو *قيمة خالية* إذا لم يتم تعيين مالك.|secop2@contoso.com
تصنيف|مواصفات الحادث. قيم الخاصية هي: *غير معروف*، *FalsePositive*، *TruePositive*|غير معروف
تحديد|تحدد تحديد الحادث. قيم الخاصية هي: *NotAvailable* و *Apt* و *Malware* *و SecurityPersonnel* و *SecurityTesting* و *UnwantedSoftware* و *Other*|غير متوفر
detectionSource|يحدد مصدر الكشف.|Defender for Cloud Apps
الحالة|تصنيف الأحداث *(ك نشط* أو *تم الحل*). يمكن أن يساعدك على تنظيم استجابتك للحوادث وإدارتها.|نشط
الخطورة|تشير إلى التأثير المحتمل على الأصول. كلما زادت الخطورة زاد التأثير. عادة ما تتطلب عناصر الخطورة الأعلى انتباها فوريا. <p> إحدى القيم التالية: *معلوماتية ودنيا* و*متوسطة *وأعلى*. |متوسط
العلامات|صفيف من العلامات المخصصة المقترنة بحادث، على سبيل المثال، وضع علامة على مجموعة من الأحداث ذات سمة مشتركة.|\[\]
التعليقات|صفيف من التعليقات التي تم إنشاؤها بواسطة secops عند إدارة الحادث، على سبيل المثال معلومات إضافية حول تحديد التصنيف.|\[\]
التنبيهات|صفيف يحتوي على كل التنبيهات المتعلقة بالحادث، بالإضافة إلى معلومات أخرى، مثل الخطورة والكيانات التي كانت متضمنة في التنبيه ومصدر التنبيهات.|\[\] (راجع التفاصيل حول حقول التنبيه أدناه)

### <a name="alerts-metadata"></a>تنبيهات بيانات التعريف

اسم الحقل|الوصف|قيمة المثال
---|---|---
alertId|معرف فريد لتمثيل التنبيه|caD70CFEE2-1F54-32DB-9988-3A868A1EBFAC
incidentId|معرف فريد لتمثيل الحادث المقترن بهذا التنبيه|924565
serviceSource|الخدمة التي ينشأ منها التنبيه، مثل Microsoft Defender ل Endpoint أو Microsoft Defender for Cloud Apps أو Microsoft Defender for Identity أو Microsoft Defender for Office 365.|MicrosoftCloudAppSecurity
creationTime|وقت إنشاء التنبيه للمرة الأولى.|2020-09-06T14:46:55.7182276Z
lastUpdatedTime|الوقت الذي تم فيه آخر تحديث للتنبيه على الواجهة الخلفية.|2020-09-06T14:46:57.2433333Z
resolvedTime|وقت حل التنبيه.|2020-09-10T05:22:59Z
أول نشاط|الوقت الذي تم فيه إرسال تنبيه لأول مرة تم فيه تحديث هذا النشاط في الخلفية.|2020-09-04T05:22:59Z
العنوان|تعريف مختصر لقيمة السلسلة المتوفرة لكل تنبيه.|نشاط برامج الفدية الضارة
الوصف|قيمة السلسلة التي تصف كل تنبيه.|يعالج المستخدم Test User2 (testUser2@contoso.com) 99 ملفا بملحقات متعددة تنتهي *بملحقها غير المألوف herunterladen*. هذا عدد غير معتاد من المعالجة للملفات ويحتمل أن يكون هجمة برامج الفدية الضارة.
الفئة|طريقة عرض مرئية رقمية ل مدى تقدم الهجوم على طول سلسلة الاقتات. محاذاتها مع [إطار عمل MITRE ATT&CK™](https://attack.mitre.org/).|التأثير
الحالة|تصنيف التنبيهات (ك *تنبيهات* جديدة أو *نشطة* *أو تم حلها*). يمكن أن يساعدك ذلك على تنظيم استجابتك للتنبيهات وإدارتها.|الجديد
الخطورة|تشير إلى التأثير المحتمل على الأصول. كلما زادت الخطورة زاد التأثير. عادة ما تتطلب عناصر الخطورة الأعلى انتباها فوريا.<br>إحدى القيم التالية: *معلوماتية* وانخفاض *ومتوسطة* *وأعلى*. |متوسط
investigationId|تم تشغيل "ID" التحقيق التلقائي بواسطة هذا التنبيه.|1234
investigationState|معلومات حول الحالة الحالية التحقيق. إحدى القيم *التالية: غير* معروف، منته، تم بنجاح المعالجة، وليد، فشل، معالجة جزئية، تشغيل، *PendingApproval*، *PendingResource*، *جزئيInvestigated*، *TerminatedByUser*، *TerminatedBySystem**، قائمة* الانتظار، *InnerFailure*، *PreexistingAlert*، *UnsupportedOs، UnsupportedAlertType*، *SuppressedAlert*.|UnsupportedAlertType
تصنيف|مواصفات الحادث. قيم الخاصية هي: *غير معروف* أو *FalsePositive* أو *TruePositive* أو *null*|غير معروف
تحديد|تحدد تحديد الحادث. قيم الخاصية هي: *NotAvailable* أو *Apt* أو *Malware* أو *SecurityPersonnel* أو *SecurityTesting* أو *UnwantedSoftware* أو *Other* أو  *null*|Apt
assignedTo|مالك الحادث، أو *قيمة خالية* إذا لم يتم تعيين مالك.|secop2@contoso.com
تمثيلName|مجموعة النشاط، إن وجدت، المقترنة بهذا التنبيه.|BORON
threatFamilyName|عائلة التهديدات المقترنة بهذا التنبيه.|null
mitreTechniques|تقنيات الهجوم، كما تتماشى مع [إطار عمل MITRE ATT&CK](https://attack.mitre.org/)™.|\[\]
الأجهزة|كل الأجهزة التي تم إرسال التنبيهات المتعلقة بالحادث فيها.|\[\] (راجع التفاصيل حول حقول الكيانات أدناه)

### <a name="device-format"></a>تنسيق الجهاز

اسم الحقل|الوصف|قيمة المثال
---|---|---
DeviceId|"معرّف الجهاز" كما تم تعيينه في Microsoft Defender لنقطة النهاية.|24c222b0b60fe148eeece49ac83910cc6a7ef491
aadDeviceId|"معرّف الجهاز" كما تم تعيينه في [Azure Active Directory](/azure/active-directory/fundamentals/active-directory-whatis). متوفر فقط للأجهزة المنضمة إلى المجال.|null
deviceDnsName|اسم المجال المؤهل بالكامل للجهاز.|user5cx.middleeast.corp.contoso.com
osPlatform|نظام التشغيل الأساسي الذي يعمل به الجهاز.|WindowsServer2016
osBuild|إصدار إصدار نظام التشغيل الذي يعمل به الجهاز.|14393
rbacGroupName|مجموعة [التحكم بالوصول](/azure/role-based-access-control/overview) المستند إلى الدور (RBAC) المقترنة بجهاز.|WDATP-Ring0
firstSeen|وقت رؤية الجهاز للمرة الأولى.|2020-02-06T14:16:01.9330135Z
healthStatus|حالة صحة الجهاز.|نشط
riskScore|درجة المخاطر للجهاز.|عال
الكيانات|جميع الكيانات التي تم تحديد أنها جزء من تنبيه معين أو ذات صلة به.|\[\] (راجع التفاصيل حول حقول الكيانات أدناه)

### <a name="entity-format"></a>تنسيق الكيان

اسم الحقل|الوصف|قيمة المثال
---|---|---
entityType|الكيانات التي تم تحديد أنها جزء من تنبيه معين أو ذات صلة به.<br>قيم الخصائص هي: *User وIp* *وUrl* و *File* و *Process* و *MailBox* و *MailMessage* و *MailCluster و* *Registry* |User
sha1|متوفر إذا كان entityType هو *ملف*.<br>يشح ملف التنبيهات المقترنة بملف أو عملية.|5de839186691aa96ee2ca6d74f0a38fb8d1bd6dd
sha256|متوفر إذا كان entityType هو *ملف*.<br>يشح ملف التنبيهات المقترنة بملف أو عملية.|28cb017dfc99073aa1b47c1b30f413e3ce774c4991eb4158de50f9dbb36d8043
fileName|متوفر إذا كان entityType هو *ملف*.<br>اسم الملف للتنبيهات المقترنة بملف أو عملية|Detector.UnitTests.dll
filePath|متوفر إذا كان entityType هو *ملف*.<br>مسار الملف للتنبيهات المقترنة بملف أو عملية|C:\\\agent_work_temp\Deploy\SYSTEM\2020-09-06 12_14_54\Out
processId|متوفر إذا كانت entityType هي *Process*.|24348
processCommandLine|متوفر إذا كانت entityType هي *Process*.|"الملف جاهز للتنزيل1911150169.exe\_ "
processCreationTime|متوفر إذا كانت entityType هي *Process*.|2020-07-18T03:25:38.5269993Z
parentProcessId|متوفر إذا كانت entityType هي *Process*.|16840
parentProcessCreationTime|متوفر إذا كانت entityType هي *Process*.|2020-07-18T02:12:32.8616797Z
ipAddress|متوفر إذا كانت entityType *Ip.* <br>عنوان IP للتنبيهات المقترنة بالأحداث على الشبكة، مثل *الاتصال بوجهة شبكة ضارة*.|62.216.203.204
url|متوفر إذا كان entityType هو *Url*. <br>Url للتنبيهات المقترنة بالأحداث على الشبكة، مثل الاتصال *بوجهة شبكة ضارة*.|down.esales360.cn
accountName|متوفر إذا كان entityType هو *User*.|testUser2
domainName|متوفر إذا كان entityType هو *User*.|europe.corp.contoso
userSid|متوفر إذا كان entityType هو *User*.|S-1-5-21-1721254763-462695806-1538882281-4156657
aadUserId|متوفر إذا كان entityType هو *User*.|fc8f7484-f813-4db2-afab-bc1507913fb6
userPrincipalName|متوفر إذا entityType هو *UserMailBoxMailMessage*//.|testUser2@contoso.com
mailboxDisplayName|متوفر إذا كانت entityType هي *MailBox*.|اختبار User2
علبة البريدAddress|متوفر إذا entityType هو *UserMailBoxMailMessage*//.|testUser2@contoso.com
clusterBy|متوفر إذا entityType هو  *MailCluster*.|الموضوع؛ P2SenderDomain; ContentType
المرسل|متوفر إذا entityType هو *UserMailBoxMailMessage*//.|user.abc@mail.contoso.co.in
المستلم|متوفر إذا كانت entityType هي *MailMessage*.|testUser2@contoso.com
الموضوع|متوفر إذا كانت entityType هي *MailMessage*.|\[الانتباه\] الخارجي
deliveryAction|متوفر إذا كانت entityType هي *MailMessage*.|تم التسليم
securityGroupId|متوفر إذا كانت entityType هي  *مجموعة الأمان*.|301c47c8-e15f-4059-ab09-e2ba9ffd372b
securityGroupName|متوفر إذا كانت entityType هي  *مجموعة الأمان*.|عوامل تشغيل تكوين الشبكة
registryHive|متوفر إذا كان entityType هو  *Registry*.|HKEYLOCALMACHINE\_\_|
registryKey|متوفر إذا كان entityType هو  *Registry*.|SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon
registryValueType|متوفر إذا كان entityType هو  *Registry*.|سلسلة
registryValue|متوفر إذا كان entityType هو  *Registry*.|31-00-00-00
deviceId|الم ID، إن وجدت، للجهاز المرتبط بالكيان.|986e5df8b73dacd43c8917d17e523e76b13c75cd

## <a name="example"></a>مثال

### <a name="request-example"></a>مثال على طلب

```HTTP
GET https://api.security.microsoft.com/api/incidents
```

### <a name="response-example"></a>مثال على الاستجابة

```json
{
    "@odata.context": "https://api.security.microsoft.com/api/$metadata#Incidents",
    "value": [
            {
            "incidentId": 924565,
            "redirectIncidentId": null,
            "incidentName": "Ransomware activity",
            "createdTime": "2020-09-06T14:46:57.0733333Z",
            "lastUpdateTime": "2020-09-06T14:46:57.29Z",
            "assignedTo": null,
            "classification": "Unknown",
            "determination": "NotAvailable",
            "status": "Active",
            "severity": "Medium",
            "tags": [],
            "comments": [
                {
                    "comment": "test comment for docs",
                    "createdBy": "secop123@contoso.com",
                    "createdTime": "2021-01-26T01:00:37.8404534Z"
                }
            ],
            "alerts": [
                {
                    "alertId": "caD70CFEE2-1F54-32DB-9988-3A868A1EBFAC",
                    "incidentId": 924565,
                    "serviceSource": "MicrosoftCloudAppSecurity",
                    "creationTime": "2020-09-06T14:46:55.7182276Z",
                    "lastUpdatedTime": "2020-09-06T14:46:57.2433333Z",
                    "resolvedTime": null,
                    "firstActivity": "2020-09-04T05:22:59Z",
                    "lastActivity": "2020-09-04T05:22:59Z",
                    "title": "Ransomware activity",
                    "description": "The user Test User2 (testUser2@contoso.com) manipulated 99 files with multiple extensions ending with the uncommon extension herunterladen. This is an unusual number of file manipulations and is indicative of a potential ransomware attack.",
                    "category": "Impact",
                    "status": "New",
                    "severity": "Medium",
                    "investigationId": null,
                    "investigationState": "UnsupportedAlertType",
                    "classification": null,
                    "determination": null,
                    "detectionSource": "MCAS",
                    "assignedTo": null,
                    "actorName": null,
                    "threatFamilyName": null,
                    "mitreTechniques": [],
                    "devices": [],
                    "entities": [
                        {
                            "entityType": "User",
                            "sha1": null,
                            "sha256": null,
                            "fileName": null,
                            "filePath": null,
                            "processId": null,
                            "processCommandLine": null,
                            "processCreationTime": null,
                            "parentProcessId": null,
                            "parentProcessCreationTime": null,
                            "ipAddress": null,
                            "url": null,
                            "accountName": "testUser2",
                            "domainName": "europe.corp.contoso",
                            "userSid": "S-1-5-21-1721254763-462695806-1538882281-4156657",
                            "aadUserId": "fc8f7484-f813-4db2-afab-bc1507913fb6",
                            "userPrincipalName": "testUser2@contoso.com",
                            "mailboxDisplayName": null,
                            "mailboxAddress": null,
                            "clusterBy": null,
                            "sender": null,
                            "recipient": null,
                            "subject": null,
                            "deliveryAction": null,
                            "securityGroupId": null,
                            "securityGroupName": null,
                            "registryHive": null,
                            "registryKey": null,
                            "registryValueType": null,
                            "registryValue": null,
                            "deviceId": null
                        },
                        {
                            "entityType": "Ip",
                            "sha1": null,
                            "sha256": null,
                            "fileName": null,
                            "filePath": null,
                            "processId": null,
                            "processCommandLine": null,
                            "processCreationTime": null,
                            "parentProcessId": null,
                            "parentProcessCreationTime": null,
                            "ipAddress": "62.216.203.204",
                            "url": null,
                            "accountName": null,
                            "domainName": null,
                            "userSid": null,
                            "aadUserId": null,
                            "userPrincipalName": null,
                            "mailboxDisplayName": null,
                            "mailboxAddress": null,
                            "clusterBy": null,
                            "sender": null,
                            "recipient": null,
                            "subject": null,
                            "deliveryAction": null,
                            "securityGroupId": null,
                            "securityGroupName": null,
                            "registryHive": null,
                            "registryKey": null,
                            "registryValueType": null,
                            "registryValue": null,
                            "deviceId": null
                        }
                    ]
                }
            ]
        },
        {
            "incidentId": 924521,
            "redirectIncidentId": null,
            "incidentName": "'Mimikatz' hacktool was detected on one endpoint",
            "createdTime": "2020-09-06T12:18:03.6266667Z",
            "lastUpdateTime": "2020-09-06T12:18:03.81Z",
            "assignedTo": null,
            "classification": "Unknown",
            "determination": "NotAvailable",
            "status": "Active",
            "severity": "Low",
            "tags": [],
            "comments": [],
            "alerts": [
                {
                    "alertId": "da637349914833441527_393341063",
                    "incidentId": 924521,
                    "serviceSource": "MicrosoftDefenderATP",
                    "creationTime": "2020-09-06T12:18:03.3285366Z",
                    "lastUpdatedTime": "2020-09-06T12:18:04.2566667Z",
                    "resolvedTime": null,
                    "firstActivity": "2020-09-06T12:15:07.7272048Z",
                    "lastActivity": "2020-09-06T12:15:07.7272048Z",
                    "title": "'Mimikatz' hacktool was detected",
                    "description": "Readily available tools, such as hacking programs, can be used by unauthorized individuals to spy on users. When used by attackers, these tools are often installed without authorization and used to compromise targeted machines.\n\nThese tools are often used to collect personal information from browser records, record key presses, access email and instant messages, record voice and video conversations, and take screenshots.\n\nThis detection might indicate that Windows Defender Antivirus has stopped the tool from being installed and used effectively. However, it is prudent to check the machine for the files and processes associated with the detected tool.",
                    "category": "Malware",
                    "status": "New",
                    "severity": "Low",
                    "investigationId": null,
                    "investigationState": "UnsupportedOs",
                    "classification": null,
                    "determination": null,
                    "detectionSource": "WindowsDefenderAv",
                    "assignedTo": null,
                    "actorName": null,
                    "threatFamilyName": "Mimikatz",
                    "mitreTechniques": [],
                    "devices": [
                        {
                            "mdatpDeviceId": "24c222b0b60fe148eeece49ac83910cc6a7ef491",
                            "aadDeviceId": null,
                            "deviceDnsName": "user5cx.middleeast.corp.contoso.com",
                            "osPlatform": "WindowsServer2016",
                            "version": "1607",
                            "osProcessor": "x64",
                            "osBuild": 14393,
                            "healthStatus": "Active",
                            "riskScore": "High",
                            "rbacGroupName": "WDATP-Ring0",
                            "rbacGroupId": 9,
                            "firstSeen": "2020-02-06T14:16:01.9330135Z"
                        }
                    ],
                    "entities": [
                        {
                            "entityType": "File",
                            "sha1": "5de839186691aa96ee2ca6d74f0a38fb8d1bd6dd",
                            "sha256": null,
                            "fileName": "Detector.UnitTests.dll",
                            "filePath": "C:\\Agent\\_work\\_temp\\Deploy_SYSTEM 2020-09-06 12_14_54\\Out",
                            "processId": null,
                            "processCommandLine": null,
                            "processCreationTime": null,
                            "parentProcessId": null,
                            "parentProcessCreationTime": null,
                            "ipAddress": null,
                            "url": null,
                            "accountName": null,
                            "domainName": null,
                            "userSid": null,
                            "aadUserId": null,
                            "userPrincipalName": null,
                            "mailboxDisplayName": null,
                            "mailboxAddress": null,
                            "clusterBy": null,
                            "sender": null,
                            "recipient": null,
                            "subject": null,
                            "deliveryAction": null,
                            "securityGroupId": null,
                            "securityGroupName": null,
                            "registryHive": null,
                            "registryKey": null,
                            "registryValueType": null,
                            "registryValue": null,
                            "deviceId": "24c222b0b60fe148eeece49ac83910cc6a7ef491"
                        }
                    ]
                }
            ]
        },
        {
            "incidentId": 924518,
            "redirectIncidentId": null,
            "incidentName": "Email reported by user as malware or phish",
            "createdTime": "2020-09-06T12:07:55.1366667Z",
            "lastUpdateTime": "2020-09-06T12:07:55.32Z",
            "assignedTo": null,
            "classification": "Unknown",
            "determination": "NotAvailable",
            "status": "Active",
            "severity": "Informational",
            "tags": [],
            "comments": [],
            "alerts": [
                {
                    "alertId": "faf8edc936-85f8-a603-b800-08d8525cf099",
                    "incidentId": 924518,
                    "serviceSource": "OfficeATP",
                    "creationTime": "2020-09-06T12:07:54.3716642Z",
                    "lastUpdatedTime": "2020-09-06T12:37:40.88Z",
                    "resolvedTime": null,
                    "firstActivity": "2020-09-06T12:04:00Z",
                    "lastActivity": "2020-09-06T12:04:00Z",
                    "title": "Email reported by user as malware or phish",
                    "description": "This alert is triggered when any email message is reported as malware or phish by users -V1.0.0.2",
                    "category": "InitialAccess",
                    "status": "InProgress",
                    "severity": "Informational",
                    "investigationId": null,
                    "investigationState": "Queued",
                    "classification": null,
                    "determination": null,
                    "detectionSource": "OfficeATP",
                    "assignedTo": "Automation",
                    "actorName": null,
                    "threatFamilyName": null,
                    "mitreTechniques": [],
                    "devices": [],
                    "entities": [
                        {
                            "entityType": "MailBox",
                            "sha1": null,
                            "sha256": null,
                            "fileName": null,
                            "filePath": null,
                            "processId": null,
                            "processCommandLine": null,
                            "processCreationTime": null,
                            "parentProcessId": null,
                            "parentProcessCreationTime": null,
                            "ipAddress": null,
                            "url": null,
                            "accountName": null,
                            "domainName": null,
                            "userSid": null,
                            "aadUserId": null,
                            "userPrincipalName": "testUser3@contoso.com",
                            "mailboxDisplayName": "test User3",
                            "mailboxAddress": "testUser3@contoso.com",
                            "clusterBy": null,
                            "sender": null,
                            "recipient": null,
                            "subject": null,
                            "deliveryAction": null,
                            "securityGroupId": null,
                            "securityGroupName": null,
                            "registryHive": null,
                            "registryKey": null,
                            "registryValueType": null,
                            "registryValue": null,
                            "deviceId": null
                        },
                        {
                            "entityType": "MailBox",
                            "sha1": null,
                            "sha256": null,
                            "fileName": null,
                            "filePath": null,
                            "processId": null,
                            "processCommandLine": null,
                            "processCreationTime": null,
                            "parentProcessId": null,
                            "parentProcessCreationTime": null,
                            "ipAddress": null,
                            "url": null,
                            "accountName": null,
                            "domainName": null,
                            "userSid": null,
                            "aadUserId": null,
                            "userPrincipalName": "testUser4@contoso.com",
                            "mailboxDisplayName": "test User4",
                            "mailboxAddress": "test.User4@contoso.com",
                            "clusterBy": null,
                            "sender": null,
                            "recipient": null,
                            "subject": null,
                            "deliveryAction": null,
                            "securityGroupId": null,
                            "securityGroupName": null,
                            "registryHive": null,
                            "registryKey": null,
                            "registryValueType": null,
                            "registryValue": null,
                            "deviceId": null
                        },
                        {
                            "entityType": "MailMessage",
                            "sha1": null,
                            "sha256": null,
                            "fileName": null,
                            "filePath": null,
                            "processId": null,
                            "processCommandLine": null,
                            "processCreationTime": null,
                            "parentProcessId": null,
                            "parentProcessCreationTime": null,
                            "ipAddress": null,
                            "url": null,
                            "accountName": null,
                            "domainName": null,
                            "userSid": null,
                            "aadUserId": null,
                            "userPrincipalName": "test.User4@contoso.com",
                            "mailboxDisplayName": null,
                            "mailboxAddress": null,
                            "clusterBy": null,
                            "sender": "user.abc@mail.contoso.co.in",
                            "recipient": "test.User4@contoso.com",
                            "subject": "[EXTERNAL] Attention",
                            "deliveryAction": null,
                            "securityGroupId": null,
                            "securityGroupName": null,
                            "registryHive": null,
                            "registryKey": null,
                            "registryValueType": null,
                            "registryValue": null,
                            "deviceId": null
                        },
                        {
                            "entityType": "MailCluster",
                            "sha1": null,
                            "sha256": null,
                            "fileName": null,
                            "filePath": null,
                            "processId": null,
                            "processCommandLine": null,
                            "processCreationTime": null,
                            "parentProcessId": null,
                            "parentProcessCreationTime": null,
                            "ipAddress": null,
                            "url": null,
                            "accountName": null,
                            "domainName": null,
                            "userSid": null,
                            "aadUserId": null,
                            "userPrincipalName": null,
                            "mailboxDisplayName": null,
                            "mailboxAddress": null,
                            "clusterBy": "Subject;P2SenderDomain;ContentType",
                            "sender": null,
                            "recipient": null,
                            "subject": null,
                            "deliveryAction": null,
                            "securityGroupId": null,
                            "securityGroupName": null,
                            "registryHive": null,
                            "registryKey": null,
                            "registryValueType": null,
                            "registryValue": null,
                            "deviceId": null
                        },
                        {
                            "entityType": "MailCluster",
                            "sha1": null,
                            "sha256": null,
                            "fileName": null,
                            "filePath": null,
                            "processId": null,
                            "processCommandLine": null,
                            "processCreationTime": null,
                            "parentProcessId": null,
                            "parentProcessCreationTime": null,
                            "ipAddress": null,
                            "url": null,
                            "accountName": null,
                            "domainName": null,
                            "userSid": null,
                            "aadUserId": null,
                            "userPrincipalName": null,
                            "mailboxDisplayName": null,
                            "mailboxAddress": null,
                            "clusterBy": "Subject;SenderIp;ContentType",
                            "sender": null,
                            "recipient": null,
                            "subject": null,
                            "deliveryAction": null,
                            "securityGroupId": null,
                            "securityGroupName": null,
                            "registryHive": null,
                            "registryKey": null,
                            "registryValueType": null,
                            "registryValue": null,
                            "deviceId": null
                        },
                        {
                            "entityType": "MailCluster",
                            "sha1": null,
                            "sha256": null,
                            "fileName": null,
                            "filePath": null,
                            "processId": null,
                            "processCommandLine": null,
                            "processCreationTime": null,
                            "parentProcessId": null,
                            "parentProcessCreationTime": null,
                            "ipAddress": null,
                            "url": null,
                            "accountName": null,
                            "domainName": null,
                            "userSid": null,
                            "aadUserId": null,
                            "userPrincipalName": null,
                            "mailboxDisplayName": null,
                            "mailboxAddress": null,
                            "clusterBy": "BodyFingerprintBin1;P2SenderDomain;ContentType",
                            "sender": null,
                            "recipient": null,
                            "subject": null,
                            "deliveryAction": null,
                            "securityGroupId": null,
                            "securityGroupName": null,
                            "registryHive": null,
                            "registryKey": null,
                            "registryValueType": null,
                            "registryValue": null,
                            "deviceId": null
                        },
                        {
                            "entityType": "MailCluster",
                            "sha1": null,
                            "sha256": null,
                            "fileName": null,
                            "filePath": null,
                            "processId": null,
                            "processCommandLine": null,
                            "processCreationTime": null,
                            "parentProcessId": null,
                            "parentProcessCreationTime": null,
                            "ipAddress": null,
                            "url": null,
                            "accountName": null,
                            "domainName": null,
                            "userSid": null,
                            "aadUserId": null,
                            "userPrincipalName": null,
                            "mailboxDisplayName": null,
                            "mailboxAddress": null,
                            "clusterBy": "BodyFingerprintBin1;SenderIp;ContentType",
                            "sender": null,
                            "recipient": null,
                            "subject": null,
                            "deliveryAction": null,
                            "securityGroupId": null,
                            "securityGroupName": null,
                            "registryHive": null,
                            "registryKey": null,
                            "registryValueType": null,
                            "registryValue": null,
                            "deviceId": null
                        },
                        {
                            "entityType": "Ip",
                            "sha1": null,
                            "sha256": null,
                            "fileName": null,
                            "filePath": null,
                            "processId": null,
                            "processCommandLine": null,
                            "processCreationTime": null,
                            "parentProcessId": null,
                            "parentProcessCreationTime": null,
                            "ipAddress": "49.50.81.121",
                            "url": null,
                            "accountName": null,
                            "domainName": null,
                            "userSid": null,
                            "aadUserId": null,
                            "userPrincipalName": null,
                            "mailboxDisplayName": null,
                            "mailboxAddress": null,
                            "clusterBy": null,
                            "sender": null,
                            "recipient": null,
                            "subject": null,
                            "deliveryAction": null,
                            "securityGroupId": null,
                            "securityGroupName": null,
                            "registryHive": null,
                            "registryKey": null,
                            "registryValueType": null,
                            "registryValue": null,
                            "deviceId": null
                        }
                    ]
                }
            ]
        },
        ...
    ]
}
```

## <a name="related-articles"></a>المقالات ذات الصلة

- [الوصول إلى Microsoft 365 Defender واجهات برمجة التطبيقات](api-access.md)
- [التعرف على حدود API والترخيص](api-terms.md)
- [فهم رموز الخطأ](api-error-codes.md)
- [نظرة عامة حول الأحداث](incidents-overview.md)
- [واجهات برمجة التطبيقات للحوادث](api-incident.md)
- [API لحادث التحديث](api-update-incidents.md)
