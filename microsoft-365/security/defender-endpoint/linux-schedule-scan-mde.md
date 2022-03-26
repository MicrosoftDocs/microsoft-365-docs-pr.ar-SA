---
title: كيفية جدولة عمليات الفحص باستخدام Microsoft Defender ل Endpoint (Linux)
description: تعرف على كيفية جدولة وقت فحص تلقائي ل Microsoft Defender لنقطة النهاية (Linux) لحماية أصول مؤسستك بشكل أفضل.
keywords: microsoft، defender، Microsoft Defender ل Endpoint، linux، عمليات الفحص، الحماية من الفيروسات، microsoft defender لنقطة النهاية (linux)
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
ms.openlocfilehash: ddb02d67866e675febda59fac15e8e494188a47f
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/03/2021
ms.locfileid: "63574712"
---
# <a name="schedule-scans-with-microsoft-defender-for-endpoint-linux"></a>جدولة عمليات الفحص باستخدام Microsoft Defender ل Endpoint (Linux)

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)


لتشغيل فحص ل Linux، راجع [الأوامر المعتمدة](/microsoft-365/security/defender-endpoint/linux-resources#supported-commands).

لدى Linux (و Unix) أداة تسمى **crontab** (مماثلة لجدول المهام) لكي تتمكن من تشغيل المهام المجدولة.

## <a name="pre-requisite"></a>المتطلبات الأساسية

> [!NOTE]
> للحصول على قائمة بكل المناطق الزمنية، يمكنك تشغيل الأمر التالي: `timedatectl list-timezones`<br>
> أمثلة عن المنطقة الزمنية:
>
> - `America/Los_Angeles`
> - `America/New_York`
> - `America/Chicago`
> - `America/Denver`

## <a name="to-set-the-cron-job"></a>لتعيين مهمة Cron

استخدم الأوامر التالية:

### <a name="backup-crontab-entries"></a>إدخالات الكرونتاب الاحتياطية

```bash
sudo crontab -l > /var/tmp/cron_backup_200919.dat
```

> [!NOTE]
> أين 200919 == YRMMDD

> [!TIP]
> قم بذلك قبل التحرير أو الإزالة.

لتحرير الماكرونتاب، وإضافة مهمة جديدة كمستخدم جذر:

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
> في هذا المثال، قمنا بتعيينه إلى 00 دقيقة، 2 صباحا. (الساعة بتنسيق 24 ساعة)، أي يوم من الشهر، أي شهر، في أيام السبت. مما يعني أنه سيتم تشغيل أيام السبت الساعة 2:00 صباحا. Pacific (UTC -8).

اضغط على "Esc"

اكتب "`:wq`" بدون علامات الاقتباس المزدوجة.

> [!NOTE]
> w == write, q == quit

لعرض مهام cron، اكتب `sudo crontab -l`

:::image type="content" source="../../media/linux-mdatp-1.png" alt-text="linux mdatp.":::

#### <a name="to-inspect-cron-job-runs"></a>لفحص تشغيل وظيفة كرون

```bash
sudo grep mdatp /var/log/cron
```

#### <a name="to-inspect-the-mdatp_cron_joblog"></a>لفحص mdatp_cron_job.log*

```bash
sudo nano mdatp_cron_job.log
```

## <a name="for-those-who-use-ansible-chef-or-puppet"></a>بالنسبة لهؤلاء الذين يستخدمون Ansible أو Chef أو

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
راجع <https://docs.chef.io/resources/cron/> لمزيد من المعلومات.

### <a name="to-set-cron-jobs-in-puppet"></a>لتعيين مهام cron في "مهى"

```bash
Resource Type: cron
```

راجع <https://puppet.com/docs/puppet/5.5/types/cron.html> لمزيد من المعلومات.

الأتمتة مع "نظام التشغيل": مهام Cron والمهام المجدولة

راجع [https://puppet.com/blog/automating-puppet-cron-jobs-and-scheduled-tasks/](https://puppet.com/blog/automating-puppet-cron-jobs-and-scheduled-tasks/) لمزيد من المعلومات.

## <a name="additional-information"></a>معلومات إضافية

### <a name="to-get-help-with-crontab"></a>للحصول على تعليمات حول crontab

```bash
man crontab
```

### <a name="to-get-a-list-of-crontab-file-of-the-current-user"></a>للحصول على قائمة ملف crontab للمستخدم الحالي

```bash
crontab -l
```

### <a name="to-get-a-list-of-crontab-file-of-another-user"></a>للحصول على قائمة ملف crontab لمستخدم آخر

```bash
crontab -u username -l
```

### <a name="to-backup-crontab-entries"></a>لنسخ إدخالات crontab احتياطيا

```bash
crontab -l > /var/tmp/cron_backup.dat
```

> [!TIP]
> قم بذلك قبل التحرير أو الإزالة.

### <a name="to-restore-crontab-entries"></a>لاستعادة إدخالات الكرونتاب

```bash
crontab /var/tmp/cron_backup.dat
```

### <a name="to-edit-the-crontab-and-add-a-new-job-as-a-root-user"></a>لتحرير الكرونتاب وإضافة مهمة جديدة كمستخدم جذر

```bash
sudo crontab -e
```

### <a name="to-edit-the-crontab-and-add-a-new-job"></a>لتحرير الكرونتاب وإضافة مهمة جديدة

```bash
crontab -e
```

### <a name="to-edit-other-users-crontab-entries"></a>لتحرير إدخالات crontab الخاصة ب مستخدم آخر

```bash
crontab -u username -e
```

### <a name="to-remove-all-crontab-entries"></a>لإزالة كل إدخالات crontab

```bash
crontab -r
```

### <a name="to-remove-other-users-crontab-entries"></a>لإزالة إدخالات crontab الخاصة ب مستخدم آخر

```bash
crontab -u username -r
```

### <a name="explanation"></a>شرح

+—————- دقيقة (قيم: 0 - 59) (أحرف خاصة: ، - * /)  <br>
| +————- (قيم: 0 - 23) (أحرف خاصة: ، - * /) <br>
| | +———- من الشهر (قيم: 1 - 31) (أحرف خاصة: ، - * / L W C)  <br>
| | | +——- شهر (قيم: 1 - 12) (أحرف خاصة: ,- * / )  <br>
| | | | +—- يوم من الأسبوع (القيم: 0 - 6) (الأحد=0 أو 7) (أحرف خاصة: ، - * / L W C) <br>
| | | | | الأمر *****لتنفيذه
