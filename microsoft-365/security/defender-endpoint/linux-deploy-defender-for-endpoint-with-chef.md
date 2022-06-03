---
title: كيفية توزيع Defender لنقطة النهاية على Linux مع Chef
description: تعرف على كيفية نشر Defender لنقطة النهاية على Linux باستخدام Chef
keywords: microsoft، defender، atp، linux، عمليات الفحص، مكافحة الفيروسات، microsoft Defender لنقطة النهاية (linux)
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: lovina-saldanha
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 8f610821b6c0bef7694d6ce8acd256f59f761f06
ms.sourcegitcommit: 35f167725bec5fd4fe131781a53d96b060cf232d
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/03/2022
ms.locfileid: "65872907"
---
# <a name="deploy-defender-for-endpoint-on-linux-with-chef"></a>نشر Defender لنقطة النهاية على Linux باستخدام Chef

**ينطبق على:**

- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

قبل البدء: قم بتثبيت إلغاء ضغط إذا لم يكن مثبتا بالفعل.

مكونات Chef مثبتة بالفعل ومستودع Chef (إنشاء \<reponame\>مستودع chef) لتخزين دفتر التعليمات الذي سيتم استخدامه للنشر إلى Defender لنقطة النهاية على خوادم Linux المدارة من Chef.

يمكنك إنشاء كتاب طهي جديد في مستودعك الحالي عن طريق تشغيل الأمر التالي من داخل مجلد كتاب التعليمات الموجود في مستودع chef الخاص بك:

```bash
chef generate cookbook mdatp
```

سيقوم هذا الأمر بإنشاء بنية مجلد جديدة لمصنف التعليمات الجديد المسمى mdatp. يمكنك أيضا استخدام كتاب طهي موجود إذا كان لديك بالفعل كتاب تريد استخدامه لإضافة نشر MDE إليه.
بعد إنشاء كتاب التعليمات، أنشئ مجلد ملفات داخل مجلد كتاب التعليمات الذي تم إنشاؤه للتو:

```bash
mkdir mdatp/files
```

نقل ملف مضغوط لإلحاق خادم Linux الذي يمكن تنزيله من مدخل Microsoft 365 Defender إلى مجلد الملفات الجديد هذا.

في محطة عمل Chef، انتقل إلى مجلد mdatp/recipes. يتم إنشاء هذا المجلد عند إنشاء كتاب التعليمات. استخدم محرر النص المفضل لديك (مثل vi أو nano) لإضافة الإرشادات التالية إلى نهاية الملف default.rb:

- include_recipe '::onboard_mdatp'
- include_recipe '::install_mdatp'

ثم احفظ الملف default.rb وأغلقه.

بعد ذلك، قم بإنشاء ملف وصفة جديد باسم install_mdatp.rb في مجلد الوصفات وأضف هذا النص إلى الملف:

```powershell
#Add Microsoft Defender
Repo
case node['platform_family']
when 'debian'
 apt_repository 'MDAPRepo' do
   arch               'amd64'
   cache_rebuild      true
   cookbook           false
   deb_src            false
   key                'BC528686B50D79E339D3721CEB3E94ADBE1229CF'
   keyserver          "keyserver.ubuntu.com"
   distribution       'focal'
   repo_name          'microsoft-prod'
   components         ['main']
   trusted            true
   uri                "https://packages.microsoft.com/config/ubuntu/20.04/prod"
 end
 apt_package "mdatp"
when 'rhel'
 yum_repository 'microsoft-prod' do
   baseurl            "https://packages.microsoft.com/config/rhel/7/prod/"
   description        "Microsoft Defender for Endpoint"
   enabled            true
   gpgcheck           true
   gpgkey             "https://packages.microsoft.com/keys/microsoft.asc"
 end
 if node['platform_version'] <= 8 then
    yum_package "mdatp"
 else
    dnf_package "mdatp"
 end
end
```

ستحتاج إلى تعديل رقم الإصدار والتوزيع واسم المستودع لمطابقة الإصدار الذي تقوم بنشره والقناة التي تريد نشرها.
بعد ذلك، يجب إنشاء ملف onboard_mdatp.rb في مجلد mdatp/recipies. أضف النص التالي إلى هذا الملف:

```powershell
#Create MDATP Directory
mdatp = "/etc/opt/microsoft/mdatp"
zip_path = "/path/to/chef-repo/cookbooks/mdatp/files/WindowsDefenderATPOnboardingPackage.zip"

directory "#{mdatp}" do
  owner 'root'
  group 'root'
  mode 0755
  recursive true
end

#Extract WindowsDefenderATPOnbaordingPackage.zip into /etc/opt/microsoft/mdatp

bash 'Extract Onbaording Json MDATP' do
  code <<-EOS
  unzip #{zip_path} -d #{mdatp}
  EOS
  not_if { ::File.exist?('/etc/opt/microsoft/mdatp/mdatp_onboard.json') }
end
```

تأكد من تحديث اسم المسار إلى موقع ملف الإلحاق.
لاختبار توزيعه على محطة عمل Chef، ما عليك سوى تشغيل ``sudo chef-client -z -o mdatp``.
بعد النشر الخاص بك يجب أن تفكر في إنشاء ونشر ملف تكوين إلى الخوادم استنادا إلى [تعيين تفضيلات Microsoft Defender لنقطة النهاية على Linux](/microsoft-365/security/defender-endpoint/linux-preferences).
بعد إنشاء ملف التكوين واختباره، يمكنك وضعه في مجلد كتاب التعليمات/mdatp/files حيث وضعت أيضا حزمة الإلحاق. ثم يمكنك إنشاء ملف settings_mdatp.rb في مجلد mdatp/recipies وإضافة هذا النص:

```powershell
#Copy the configuration file
cookbook_file '/etc/opt/microsoft/mdatp/managed/mdatp_managed.json' do
  source 'mdatp_managed.json'
  owner 'root'
  group 'root'
  mode '0755'
  action :create
end
```

لتضمين هذه الخطوة كجزء من الوصفة، ما عليك سوى إضافة include_recipe ':: settings_mdatp' إلى ملف default.rb داخل مجلد الوصفات.
يمكنك أيضا استخدام crontab لجدولة التحديثات التلقائية [جدولة تحديث Microsoft Defender لنقطة النهاية (Linux).](linux-update-MDE-Linux.md)

إلغاء تثبيت كتاب التعليمات MDATP:

```powershell
#Uninstall the Defender package
case node['platform_family']
when 'debian'
 apt_package "mdatp" do
   action :remove
 end
when 'rhel'
 if node['platform_version'] <= 8
then
    yum_package "mdatp" do
      action :remove
    end
 else
    dnf_package "mdatp" do
      action :remove
    end
 end
end
```
