---
title: حاسبة مساحة العنوان لبوابة Azure الفرعية
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 01/07/2021
audience: ITPro
ms.topic: landing-page
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- PowerShell
- Ent_Office_Other
- seo-marvel-apr2020
description: 'ملخص: حساب مساحة العنوان في شبكة بوابة Azure الفرعية باستخدام C3 أو Python أو PowerShell.'
ms.openlocfilehash: 129c64e4484110517edf3640861636324e59de57
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/20/2022
ms.locfileid: "63681777"
---
# <a name="address-space-calculator-for-azure-gateway-subnets"></a>حاسبة مساحة العنوان لبوابة Azure الفرعية

يجب أن يكون للشبكة الظاهرية (VNet) في خدمات البنية الأساسية ل Azure المتصلة بالشبكات الأخرى شبكة بوابة فرعية. أفضل الممارسات لتعريف شبكة البوابة الفرعية هي:

- يمكن أن يكون أقصى طول للبادرة في شبكة البوابة الفرعية هو 29 (على سبيل المثال، 10.119.255.248/29)، ولكن التوصية الحالية هي استخدام طول البادرة 27 (على سبيل المثال، 10.119.255.224/27).
- عند تحديد مساحة العنوان في شبكة البوابة الفرعية، استخدم الجزء الأخير من مساحة عنوان VNet.

للحصول على التوصية الثانية، يمكنك تحديد مساحة عنوان الشبكة الفرعية للبوابة من خلال تعيين البتات المستخدمة للبوابة الفرعية إلى 0 والبت المتبقي في مساحة عنوان VNet إلى 1. لحساب مساحة عنوان الشبكة الفرعية للبوابة بسرعة دون الحاجة إلى التحويل إلى رقم ثنائي والخلف إلى رقم عشري، يمكنك استخدام تطبيق وحدة تحكم مكتوب باللغة C# أو Python أو مع كتلة أوامر PowerShell.

تحتوي هذه المقالة على كتل التعليمات البرمجية C# و Python و PowerShell التي تحسب مساحة عنوان الشبكة الفرعية للبوابة استنادا إلى قيم w.x.y.z/n لبادءة عنوان VNet وطولبادية الشبكة الفرعية للبوابة.

## <a name="c-code-block"></a>كتلة التعليمات البرمجية C#

استخدم كتلة التعليمات البرمجية هذه لإنشاء تطبيق وحدة تحكم في C#.

```c#
using System; 
using System.Collections.Generic; 
using System.Linq; 
using System.Text; 
using System.Threading.Tasks; 
 
namespace ConsoleApplication1 
{ 
    class Program 
    { 
        static void Main(string[] args) 
        { 
            // Declare variables. 
            const long wOctet = 16777216;  
            const long xOctet = 65536; 
            const long yOctet = 256; 
            double D; 
            int w, x, y, z, vnetPrefLen, gwPrefLen; 
            long d, w2, x2, y2, z2; 
             
 
            // Get the five values needed from the keyboard. 
            Console.WriteLine("**************************************************************************"); 
            Console.WriteLine("*** Gateway subnet address space calculator for Azure virtual networks ***");             
            Console.WriteLine("**************************************************************************");  
            Console.WriteLine(); 
            Console.WriteLine("Please supply your virtual network address space in the form of w.x.y.z/n."); 
            Console.WriteLine(); 
            Console.WriteLine("w="); 
            w = Convert.ToInt32(Console.ReadLine()); 
            Console.WriteLine("x="); 
            x = Convert.ToInt32(Console.ReadLine()); 
            Console.WriteLine("y="); 
            y = Convert.ToInt32(Console.ReadLine()); 
            Console.WriteLine("z="); 
            z = Convert.ToInt32(Console.ReadLine()); 
            Console.WriteLine("n="); 
            vnetPrefLen = Convert.ToInt32(Console.ReadLine()); 
            Console.WriteLine(); 
            Console.WriteLine("Now supply the prefix length of your gateway subnet:"); 
            gwPrefLen = Convert.ToInt32(Console.ReadLine()); 
            Console.WriteLine(); 
 
            // Perform the calculation. 
            D = w * wOctet + x * xOctet + y * yOctet + z; 
            for (int i = vnetPrefLen + 1; i < gwPrefLen + 1; i++) 
            { 
                D = D + Math.Pow(2, 32 - i); 
            } 
            d = Convert.ToInt64(D); 
            w2 = d / wOctet; 
            x2 = (d - w2 * wOctet) / xOctet;  
            y2 = (d - w2 * wOctet - x2 * xOctet) / yOctet; 
            z2 = d - w2 * wOctet - x2 * xOctet - y2 * yOctet; 
             
            // Display the result.             
            Console.WriteLine("**************************************************************************");  
            Console.WriteLine("For the Azure virtual address space {0}.{1}.{2}.{3}/{4}", w, x, y, z, vnetPrefLen); 
            Console.WriteLine("and gateway prefix length of {0}, the gateway subnet address space is:", gwPrefLen); 
            Console.WriteLine(); 
            Console.WriteLine("{0}.{1}.{2}.{3}/{4}", w2, x2, y2, z2, gwPrefLen); 
            Console.WriteLine(); 
            Console.WriteLine("Press ENTER to quit."); 
            Console.ReadLine(); 
        } 
    } 
} 
```

## <a name="python-code-block"></a>كتلة رمز Python

استخدم كتلة التعليمات البرمجية هذه لإنشاء تطبيق وحدة تحكم في Python.

```python
import math 
# Collect the values of w.x.y.z/n for your VNet address space and g, the prefix length of your gateway subnet 
print("**************************************************************************")  
print("*** Gateway subnet address space calculator for Azure virtual networks ***")  
print("**************************************************************************\n")   
print("Please supply your virtual network address space in the form of w.x.y.z/n.");  
w=int(input("w = ")) 
x=int(input("x = ")) 
y=int(input("y = ")) 
z=int(input("z = ")) 
n=int(input("n = ")) 
print("")  
g=int(input("Now supply the prefix length of your gateway subnet: ")) 
print("")  
 
# Calculate  
wOctet = 16777216  
xOctet = 65536  
yOctet = 256  
D = w * wOctet + x * xOctet + y * yOctet + z 
for index in range(n + 1,g + 1): 
    D += 2**(32 - index)  
 
w2 = math.floor(D / wOctet)  
x2 = math.floor((D - w2 * wOctet) / xOctet) 
y2 = math.floor((D - w2 * wOctet - x2 * xOctet) / yOctet) 
z2 = D - w2 * wOctet - x2 * xOctet - y2 * yOctet  
 
# Display the result  
gwAddrPref= "Your gateway address prefix is: " + str(w2) + "." + str(x2) + "." + str(y2) + "." + str(z2) + "/" + str(g)  
print(gwAddrPref) 
```


## <a name="powershell-command-block"></a>كتلة أوامر PowerShell

قم بتعبئة القيم وتشغيل كتلة الأوامر الناتجة في نافذة PowerShell أو في بيئة البرامج النصية المتكاملة في PowerShell (ISE).

```powershell
# Specify the values of w.x.y.z/n for your VNet address space and g, the prefix length of your gateway subnet: 
$w= 
$x= 
$y= 
$z= 
$n= 
$g= 
# Calculate 
$wOctet = 16777216 
$xOctet = 65536 
$yOctet = 256 
[long]$D = $w * $wOctet + $x * $xOctet + $y * $yOctet + $z; 
for ($i = $n + 1; $i -lt $g + 1; $i++) 
{ 
$D = $D + [math]::pow(2, 32 - $i) 
} 
$w2 = [math]::floor($D / $wOctet) 
$x2 = [math]::floor( ($D - $w2 * $wOctet) / $xOctet ) 
$y2 = [math]::floor( ($D - $w2 * $wOctet - $x2 * $xOctet) / $yOctet ) 
$z2 = $D - $w2 * $wOctet - $x2 * $xOctet - $y2 * $yOctet 
# Display the result 
$dx= [string]$w2 + "." + [string]$x2 + "." + [string]$y2 + "." + [string]$z2 + "/" + [string]$g 
Write-Host "Your gateway address prefix is: " $dx
```
    
## <a name="related-topics"></a>المواضيع ذات الصلة

[إدارة Microsoft 365 باستخدام PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)