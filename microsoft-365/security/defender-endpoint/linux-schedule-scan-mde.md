---
title: كيفية جدولة عمليات الفحص باستخدام Microsoft Defender لنقطة النهاية (Linux)
description: تعرف على كيفية جدولة وقت فحص تلقائي Microsoft Defender لنقطة النهاية (Linux) لحماية أصول مؤسستك بشكل أفضل.
keywords: microsoft، defender، Microsoft Defender لنقطة النهاية، linux، عمليات الفحص، مكافحة الفيروسات، microsoft Defender لنقطة النهاية (linux)
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 706284ed0adf49c4da6357b6bb8217d5a14268e1
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/06/2022
ms.locfileid: "64663479"
---
# <a name="schedule-scans-with-microsoft-defender-for-endpoint-linux"></a>جدولة عمليات الفحص باستخدام Microsoft Defender لنقطة النهاية (Linux)

**ينطبق على:**
- [Microsoft Defender لنقطة النهاية الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)


لتشغيل فحص لنظام Linux، راجع [الأوامر المدعومة](/microsoft-365/security/defender-endpoint/linux-resources#supported-commands).

لدى Linux (و Unix) أداة تسمى **crontab** (مشابهة لمجدول المهام) لتكون قادرة على تشغيل المهام المجدولة.

## <a name="pre-requisite"></a>المتطلبات الأساسية

> [!NOTE]
> للحصول على قائمة بجميع المناطق الزمنية، قم بتشغيل الأمر التالي: `timedatectl list-timezones`<br>
> أمثلة على المناطق الزمنية:
>
> - `America/Los_Angeles`
> - `America/New_York`
> - `America/Chicago`
> - `America/Denver`

## <a name="to-set-the-cron-job"></a>لتعيين مهمة Cron

استخدم الأوامر التالية:

### <a name="backup-crontab-entries"></a>إدخالات crontab احتياطية

```bash
sudo crontab -l > /var/tmp/cron_backup_200919.dat
```

> [!NOTE]
> حيث 200919 == YRMMDD

> [!TIP]
> قم بذلك قبل التحرير أو الإزالة.

لتحرير الجدول، وإضافة مهمة جديدة كمستخدم جذر:

```bash
sudo crontab -e
```

> [!NOTE]
> المحرر الافتراضي هو VIM.

قد ترى:

```outbou
0 * * * * /etc/opt/microsoft/mdatp/logrorate.sh
```

اضغط على "إدراج"

أضف الإدخالات التالية:

```bash
CRON_TZ=America/Los_Angeles

0 2 * * sat /bin/mdatp scan quick > ~/mdatp_cron_job.log
```

> [!NOTE]
> في هذا المثال، قمنا بتعيينه إلى 00 دقيقة، 2 ص. (الساعة بتنسيق 24 ساعة)، أي يوم من الشهر، أي شهر، في أيام السبت. مما يعني أنه سيتم تشغيله يوم السبت في الساعة 2:00 ص. المحيط الهادئ (UTC -8).

اضغط على "Esc"

اكتب "`:wq`" بدون علامات الاقتباس المزدوجة.

> [!NOTE]
> w == write, q == quit

لعرض مهام cron، اكتب `sudo crontab -l`

:::image type="content" source="../../media/linux-mdatp-1.png" alt-text="صفحة linux mdatp" lightbox="../../media/linux-mdatp-1.png":::

#### <a name="to-inspect-cron-job-runs"></a>لفحص تشغيل مهمة cron

```bash
sudo grep mdatp /var/log/cron
```

#### <a name="to-inspect-the-mdatp_cron_joblog"></a>لفحص mdatp_cron_job.log*

```bash
sudo nano mdatp_cron_job.log
```

## <a name="for-those-who-use-ansible-chef-or-puppet"></a>لأولئك الذين يستخدمون Ansible أو Chef أو Puppet

استخدم الأوامر التالية:

### <a name="to-set-cron-jobs-in-ansible"></a>لتعيين مهام cron في Ansible

```bash
cron - Manage cron.d and crontab entries

See [https://docs.ansible.com/ansible/latest/modules/cron_module.html](https://docs.ansible.com/ansible/latest/modules/cron_module.html) for more information.

### To set crontabs in Chef

```bash
cron resource
```bash

```
لمزيد <https://docs.chef.io/resources/cron/> من المعلومات.

### <a name="to-set-cron-jobs-in-puppet"></a>لتعيين مهام cron في Puppet

```bash
Resource Type: cron
```

لمزيد <https://puppet.com/docs/puppet/5.5/types/cron.html> من المعلومات.

الأتمتة باستخدام Puppet: مهام Cron والمهام المجدولة

لمزيد [https://puppet.com/blog/automating-puppet-cron-jobs-and-scheduled-tasks/](https://puppet.com/blog/automating-puppet-cron-jobs-and-scheduled-tasks/) من المعلومات.

## <a name="additional-information"></a>معلومات إضافية

### <a name="to-get-help-with-crontab"></a>للحصول على تعليمات حول crontab

```bash
man crontab
```

### <a name="to-get-a-list-of-crontab-file-of-the-current-user"></a>للحصول على قائمة بالملف الجدولي للمستخدم الحالي

```bash
crontab -l
```

### <a name="to-get-a-list-of-crontab-file-of-another-user"></a>للحصول على قائمة بملف جدولي لمستخدم آخر

```bash
crontab -u username -l
```

### <a name="to-backup-crontab-entries"></a>للنسخ الاحتياطي للإدخالات الجدولية

```bash
crontab -l > /var/tmp/cron_backup.dat
```

> [!TIP]
> قم بذلك قبل التحرير أو الإزالة.

### <a name="to-restore-crontab-entries"></a>لاستعادة الإدخالات الجدولية

```bash
crontab /var/tmp/cron_backup.dat
```

### <a name="to-edit-the-crontab-and-add-a-new-job-as-a-root-user"></a>لتحرير crontab وإضافة مهمة جديدة كمستخدم جذر

```bash
sudo crontab -e
```

### <a name="to-edit-the-crontab-and-add-a-new-job"></a>لتحرير crontab وإضافة مهمة جديدة

```bash
crontab -e
```

### <a name="to-edit-other-users-crontab-entries"></a>لتحرير إدخالات crontab الخاصة بالمستخدم الآخر

```bash
crontab -u username -e
```

### <a name="to-remove-all-crontab-entries"></a>لإزالة كافة الإدخالات الجدولية

```bash
crontab -r
```

### <a name="to-remove-other-users-crontab-entries"></a>لإزالة إدخالات crontab الخاصة بالمستخدم الآخر

```bash
crontab -u username -r
```

### <a name="explanation"></a>تفسير

+—————- دقيقة (القيم: 0 - 59) (الأحرف الخاصة: ، \- \* /)  <br>
| +————- ساعة (القيم: 0 - 23) (الأحرف الخاصة: ، \- \* /) <br>
| | +———- يوم من الشهر (القيم: 1 - 31) (الأحرف الخاصة: ، \- \* / L W C)  <br>
| | | +——- شهر (القيم: 1 - 12) (الأحرف الخاصة: ، \- \* / )  <br>
| | | | +—- يوم من الأسبوع (القيم: 0 - 6) (الأحد=0 أو 7) (الأحرف الخاصة: ، \- \* / L W C) <br>
| | | | |****الأمر المطلوب تنفيذه
