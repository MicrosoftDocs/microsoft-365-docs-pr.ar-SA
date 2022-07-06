---
title: التشفير في Azure
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: ''
search.appverid:
- MET150
ms.collection:
- Strat_O365_Enterprise
- M365-security-compliance
- Strat_O365_Enterprise
description: تعرف على التشفير المتوفر في Azure، مثل تشفير قرص Azure
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 66fb4e54c0837534d6943372d84cf3a4864e4739
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/06/2022
ms.locfileid: "66632168"
---
# <a name="encryption-in-azure"></a>التشفير في Azure

تساعد الضمانات التكنولوجية في Azure، مثل الاتصالات المشفرة والعمليات التشغيلية، في الحفاظ على أمان بياناتك. لديك أيضا المرونة لتنفيذ ميزات تشفير إضافية وإدارة مفاتيح التشفير الخاصة بك. بغض النظر عن تكوين العميل، تطبق Microsoft التشفير لحماية بيانات العملاء في Azure. تمكنك Microsoft أيضا من التحكم في بياناتك المستضافة في Azure من خلال مجموعة من التقنيات المتقدمة لتشفير مفاتيح التشفير والتحكم فيها وإدارتها والتحكم في الوصول إلى البيانات وتدقيقها. بالإضافة إلى ذلك، يوفر Azure Storage مجموعة شاملة من قدرات الأمان التي تمكن المطورين معا من إنشاء تطبيقات آمنة.

يوفر Azure العديد من الآليات لحماية البيانات في أثناء انتقالها من موقع إلى آخر. تستخدم Microsoft TLS لحماية البيانات عند التنقل بين الخدمات السحابية والعملاء. تتفاوض مراكز بيانات Microsoft على اتصال TLS بأنظمة العملاء التي تتصل بخدمات Azure. تحمي شركة Perfect Forward Attendeecy (PFS) الاتصالات بين أنظمة العملاء وخدمات Microsoft السحابية من خلال مفاتيح فريدة. تستخدم الاتصالات أيضا أطوال مفتاح التشفير 2048 بت المستندة إلى RSA. تجعل هذه المجموعة من الصعب على شخص ما اعتراض البيانات المتنقلة والوصول إليها.

يمكن تأمين البيانات أثناء النقل بين تطبيق وAzure باستخدام [التشفير من جانب العميل](/azure/storage/storage-client-side-encryption) أو HTTPS أو SMB 3.0. يمكنك تمكين التشفير لنسبة استخدام الشبكة بين أجهزتك الظاهرية (VMs) والمستخدمين. باستخدام [Azure Virtual Networks](https://azure.microsoft.com/services/virtual-network/)، يمكنك استخدام بروتوكول IPsec القياسي في الصناعة لتشفير نسبة استخدام الشبكة بين بوابة VPN الخاصة بالشركة وAzure وكذلك بين الأجهزة الظاهرية الموجودة على شبكتك الظاهرية.

بالنسبة للبيانات الثابتة، يقدم Azure العديد من خيارات التشفير، مثل دعم AES-256، مما يمنحك المرونة لاختيار سيناريو تخزين البيانات الذي يلبي احتياجاتك على أفضل تقدير. يمكن تشفير البيانات تلقائيا عند كتابتها إلى Azure Storage باستخدام [تشفير خدمة التخزين](/azure/storage/storage-service-encryption)، ويمكن تشفير نظام التشغيل وأقراص البيانات المستخدمة من قبل الأجهزة الظاهرية. لمزيد من المعلومات، راجع [توصيات الأمان للأجهزة الظاهرية التي تعمل بنظام Windows في Azure](/azure/security/azure-security-disk-encryption). بالإضافة إلى ذلك، يمكن منح حق الوصول المفوض إلى كائنات البيانات في Azure Storage باستخدام [توقيعات الوصول المشترك](/azure/storage/storage-dotnet-shared-access-signature-part-1). يوفر Azure أيضا تشفير البيانات الثابتة باستخدام [تشفير البيانات الشفافة لقاعدة بيانات Azure SQL ومستودع البيانات](/sql/relational-databases/security/encryption/transparent-data-encryption-azure-sql).

لمزيد من المعلومات حول التشفير في Azure، راجع [نظرة عامة على تشفير Azure](/azure/security/security-azure-encryption-overview) [وAzure Data Encryption-at-Rest](/azure/security/azure-security-encryption-atrest).

## <a name="azure-disk-encryption"></a>تشفير قرص Azure

يتيح لك تشفير قرص Azure تشفير أقراص الجهاز الظاهري ل Windows وLinux كخدمة (IaaS). يستفيد تشفير قرص Azure من ميزة BitLocker لنظام التشغيل Windows وميزة DM-Crypt من Linux لتوفير تشفير على مستوى وحدة التخزين لنظام التشغيل وأقراص البيانات. كما يضمن تشفير جميع البيانات الموجودة على أقراص الجهاز الظاهري الثابتة في تخزين Azure الخاص بك. يتم دمج تشفير قرص Azure مع Azure Key Vault لمساعدتك في التحكم في استخدام مفاتيح التشفير والبيانات السرية وإدارتها وتدقيقها.

لمزيد من المعلومات، راجع [توصيات الأمان للأجهزة الظاهرية التي تعمل بنظام Windows في Azure](/azure/virtual-machines/windows/security-recommendations).

## <a name="azure-storage-service-encryption"></a>تشفير خدمة تخزين Azure

باستخدام [تشفير خدمة التخزين Azure](/azure/storage/storage-service-encryption)، يقوم Azure Storage بتشفير البيانات تلقائيا قبل استمرارها في التخزين وفك تشفير البيانات قبل الاسترداد. عمليات التشفير وفك التشفير وإدارة المفاتيح شفافة تماما للمستخدمين. يمكن استخدام تشفير خدمة تخزين Azure ل [Azure Blob Storage](https://azure.microsoft.com/services/storage/blobs/) [وAzure Files](https://azure.microsoft.com/services/storage/files/). يمكنك أيضا استخدام مفاتيح التشفير التي تديرها Microsoft مع تشفير خدمة التخزين Azure، أو يمكنك استخدام مفاتيح التشفير الخاصة بك. (للحصول على معلومات حول استخدام المفاتيح الخاصة بك، راجع [تشفير خدمة التخزين باستخدام المفاتيح المدارة من قبل العملاء في Azure Key Vault](/azure/storage/common/storage-service-encryption-customer-managed-keys). للحصول على معلومات حول استخدام المفاتيح المدارة من قبل Microsoft، راجع [تشفير خدمة التخزين للبيانات الثابتة](/azure/storage/storage-service-encryption).) بالإضافة إلى ذلك، يمكنك أتمتة استخدام التشفير. على سبيل المثال، يمكنك تمكين تشفير خدمة التخزين أو تعطيله برمجيا على حساب تخزين باستخدام [واجهة برمجة تطبيقات REST لموفر موارد التخزين Azure](/rest/api/storagerp/) أو [مكتبة عميل موفر موارد التخزين ل .NET](/dotnet/api/overview/azure/storage) أو [Azure PowerShell](/powershell/azureps-cmdlets-docs) أو [Azure CLI](/azure/storage/storage-azure-cli).

تستخدم بعض خدمات Microsoft 365 Azure لتخزين البيانات. على سبيل المثال، يقوم SharePoint Online و OneDrive for Business بتخزين البيانات في تخزين Azure Blob، ويخزن Microsoft Teams بيانات خدمة الدردشة الخاصة به في الجداول والكائنات الثنائية كبيرة الحجم وقوائم الانتظار. بالإضافة إلى ذلك، تخزن ميزة Compliance Manager في مدخل التوافق في Microsoft Purview البيانات التي يدخلها العميل والتي يتم تخزينها في شكل مشفر في [Azure Cosmos DB](/azure/cosmos-db/database-encryption-at-rest)، وهي قاعدة بيانات النظام الأساسي كخدمة (PaaS)، وقاعدة بيانات متعددة النماذج موزعة عالميا. يقوم تشفير خدمة تخزين Azure بتشفير البيانات المخزنة في تخزين Azure Blob وفي الجداول، وتشفير قرص Azure البيانات في قوائم الانتظار، بالإضافة إلى أقراص الجهاز الظاهري ل Windows و IaaS لتوفير تشفير وحدة التخزين لنظام التشغيل وقرص البيانات. يضمن الحل تشفير جميع البيانات الموجودة على أقراص الجهاز الظاهري الثابتة في تخزين Azure الخاص بك. يتم تنفيذ [التشفير الثابت في Azure Cosmos DB](/azure/cosmos-db/database-encryption-at-rest) باستخدام العديد من تقنيات الأمان، بما في ذلك أنظمة تخزين المفاتيح الآمنة والشبكات المشفرة وواجهات برمجة التطبيقات المشفرة.

## <a name="azure-key-vault"></a>Azure Key Vault

الإدارة الأساسية الآمنة ليست فقط أساسية لأفضل ممارسات التشفير؛ كما أنه ضروري لحماية البيانات في السحابة. يتيح لك [azure Key Vault](/azure/key-vault/key-vault-whatis) تشفير المفاتيح والأسرار الصغيرة مثل كلمات المرور التي تستخدم المفاتيح المخزنة في وحدات أمان الأجهزة (HSMs). Azure Key Vault هو الحل الموصى به من Microsoft لإدارة الوصول إلى مفاتيح التشفير المستخدمة من قبل الخدمات السحابية والتحكم فيها. يمكن تعيين أذونات الوصول إلى المفاتيح للخدمات أو للمستخدمين الذين لديهم حسابات Azure Active Directory. يخفف azure Key Vault المؤسسات من الحاجة إلى تكوين وتصحيح وصيانة HSMs وبرامج إدارة المفاتيح. باستخدام azure Key Vault، لا ترى Microsoft أبدا المفاتيح والتطبيقات الخاصة بك ليس لديها حق الوصول المباشر إليها؛ يمكنك الحفاظ على التحكم. يمكنك أيضا استيراد المفاتيح أو إنشاءها في HSMs. يمكن للمؤسسات التي لديها اشتراك يتضمن Azure حماية البيانات تكوين مستأجر azure حماية البيانات الخاص بها لاستخدام مفتاح Bring [Your Own Key](/information-protection/plan-design/byok-price-restrictions) (BYOK) الذي [يديره العميل وتسجيل استخدامه](/information-protection/deploy-use/log-analyze-usage).
