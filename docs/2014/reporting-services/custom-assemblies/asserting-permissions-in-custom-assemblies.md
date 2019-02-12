---
title: Berechtigungserteilung in benutzerdefinierten Assemblys | Microsoft-Dokumentationen
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.topic: reference
helpviewer_keywords:
- secure calls [Reporting Services]
- custom assemblies [Reporting Services], permissions
- permission sets [Reporting Services]
- asserting permissions
- permissions [Reporting Services], custom assemblies
- limited permission sets
- security configuration files [Reporting Services]
ms.assetid: 3afb9631-f15e-405e-990b-ee102828f298
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 2f2ac7bfb08aa5812b8db90d3c1a6049665ce1b0
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/11/2019
ms.locfileid: "56025998"
---
# <a name="asserting-permissions-in-custom-assemblies"></a>Berechtigungserteilung in benutzerdefinierten Assemblys
  Standardmäßig wird Code von benutzerdefinierten Assemblys mit dem eingeschränkten Berechtigungssatz **Execution** ausgeführt. In einigen Fällen möchten Sie vielleicht eine benutzerdefinierte Assembly implementieren, die gesicherte Aufrufe an geschützte Ressourcen innerhalb Ihres Sicherheitssystems durchführt (z. B. an Dateien oder die Registrierung). Hierzu müssen Sie folgende Schritte durchführen:  
  
1.  Identifizieren Sie die genauen Berechtigungen, die der Code benötigt, um den gesicherten Aufruf zu machen. Wenn diese Methode Teil einer [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]-Bibliothek ist, sollten diese Informationen in der Dokumentation der Methode enthalten sein.  
  
2.  Ändern Sie die Dateien für die Berichtsserver-Richtlinienkonfiguration, um der benutzerdefinierten Assembly die erforderlichen Berechtigungen zu erteilen. Weitere Informationen zu den Konfigurationsdateien der Sicherheitsrichtlinie finden Sie unter [Using Reporting Services Security Policy Files (Verwenden von Reporting Services-Sicherheitsrichtliniendateien)](../extensions/secure-development/using-reporting-services-security-policy-files.md).  
  
3.  Erteilen Sie die erforderlichen Berechtigungen als ein Teil der Methode, in der der gesicherte Aufruf gemacht wird. Dies ist notwendig, da der vom Berichtsserver aufgerufene Code für die benutzerdefinierte Assembly ein Teil der Berichtsausdrucks-Hostassembly ist, die standardmäßig mit der Berechtigung **Execution** ausgeführt wird. Der Berechtigungssatz **Execution** besagt, dass Code ausgeführt werden kann, aber keine geschützten Ressourcen verwendet werden können.  
  
4.  Markieren Sie die benutzerdefinierte Assembly mit **AllowPartiallyTrustedCallersAttribute**, wenn sie mit einem sicheren Namen signiert wird. Dies ist notwendig, da benutzerdefinierte Assemblys von einem Berichtsausdruck aufgerufen werden, der Teil der Berichtsausdrucks-Hostassembly ist, die standardmäßig nicht **FullTrust** erhält und die somit nur „teilweise vertrauenswürdig“ ist. Weitere Informationen finden Sie unter [Using Strong-Named Custom Assemblies (Verwenden von benutzerdefinierten Assemblys mit starken Namen)](using-strong-named-custom-assemblies.md).  
  
## <a name="implementing-a-secure-call"></a>Implementieren sicherer Aufrufe  
 Sie können die Dateien für die Richtlinienkonfiguration ändern, um der Assembly bestimmte Berechtigungen zu erteilen. Wenn Sie beispielsweise eine benutzerdefinierte Assembly für die Währungsumrechnung schreiben, kann es nötig sein, dass die aktuellen Wechselkurse aus einer Datei gelesen werden müssen. Sie müssen ein weiteres Sicherheitsrecht, **FileIOPermission**, zum Berechtigungssatz der Assembly hinzufügen, um die Kursdaten abzurufen. Sie können folgenden zusätzlichen Eintrag in der Datei für die Richtlinienkonfiguration vornehmen:  
  
```  
<PermissionSet class="NamedPermissionSet"  
   version="1"  
   Name="CurrencyRatesFilePermissionSet"  
   Description="A special permission set that grants read access to my currency rates file.">  
      <IPermission class="FileIOPermission"  
         version="1"  
         Read="C:\CurrencyRates.xml"/>  
      <IPermission class="SecurityPermission"  
         version="1"  
         Flags="Execution, Assertion"/>  
</PermissionSet>  
```  
  
 Sie fügen dann eine Codegruppe hinzu, die auf diesen Berechtigungssatz verweist:  
  
```  
<CodeGroup class="UnionCodeGroup"  
   version="1"  
   PermissionSetName="CurrencyRatesFilePermissionSet"  
   Name="MyNewCodeGroup"  
   Description="A special code group for my custom assembly.">  
   <IMembershipCondition class="UrlMembershipCondition"  
      version="1"  
      Url="C:\Program Files\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\MSSQL\Reporting Services\ReportServer\bin\CurrencyConversion.dll"/>  
</CodeGroup>  
```  
  
 Damit Ihr Code die entsprechende Berechtigung erhält, müssen Sie diese Berechtigung im Code der benutzerdefinierten Assembly erteilen. Wenn Sie beispielsweise Lesezugriff zur XML-Datei, C:\CurrencyRates.xml, hinzufügen möchten, müssen Sie folgenden Code zu Ihrer Methode hinzufügen:  
  
```  
// C#  
FileIOPermission permission = new FileIOPermission(FileIOPermissionAccess.Read, @"C:\CurrencyRates.xml");  
try  
{  
   permission.Assert();  
   // Load the XML currency rates file  
   XmlDocument doc = new XmlDocument();  
   doc.Load(@"C:\CurrencyRates.xml");  
...  
```  
  
 Sie können diese Erteilung auch als Methodenattribut hinzufügen:  
  
```  
[FileIOPermissionAttribute(SecurityAction.Assert, Read=@"C:\CurrencyRates.xml")]  
```  
  
 Weitere Informationen finden Sie in der .NET Framework-Sicherheit im .NET Framework Developer's Guide.  
  
## <a name="see-also"></a>Siehe auch  
 [Verwenden benutzerdefinierter Assemblys mit Berichten](using-custom-assemblies-with-reports.md)  
  
  
