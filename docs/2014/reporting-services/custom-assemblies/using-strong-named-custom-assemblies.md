---
title: Verwenden von benutzerdefinierten Assemblys mit starken Namen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- AllowPartiallyTrustedCallersAttribute attribute
- strong-named custom assemblies [Reporting Services]
- strong names [Reporting Services]
- assemblies [Reporting Services], strong names
- custom assemblies [Reporting Services], strong-named
ms.assetid: ca9f19d7-6e86-46f2-b9ad-9bf807eaa52e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5e685ecda39e0487eb4b469920820fa6e4a10daa
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "63264897"
---
# <a name="using-strong-named-custom-assemblies"></a>Verwenden von benutzerdefinierten Assemblys mit starken Namen
  Ein starker Name identifiziert eine Assembly und enthält den Textnamen der Assembly, die vierteilige Versionsnummer, Kulturinformationen (falls verfügbar), einen öffentlichen Schlüssel und eine digitale Signatur, die im Manifest der Assembly gespeichert werden. Ein starker Name identifiziert eine Assembly eindeutig für die Common Language Runtime (CLR) und stellt die binäre Integrität sicher.  
  
## <a name="using-allowpartiallytrustedcallersattribute"></a>Verwenden von AllowPartiallyTrustedCallersAttribute  
 Um Assemblys mit starken Namen in Berichten verwenden zu können, müssen Sie zulassen, dass die Assembly mit dem starken Namen von zum Teil vertrauenswürdigem Code über das **AllowPartiallyTrustedCallers**-Attribut der Assembly aufgerufen wird. Sie können mithilfe von **AllowPartiallyTrustedCallersAttribute** zulassen, dass Assemblys mit starkem Namen vom Berichts-Designer oder dem Berichtsserver in Berichtsausdrücken aufgerufen werden. Damit Assemblys mit starkem Namen von teilweise vertrauenswürdigem Code aufgerufen werden dürfen, müssen Sie folgendes Attribut auf Assemblyebene zu Ihrer Assemblyattributdatei hinzufügen.  
  
```vb  
<assembly:AllowPartiallyTrustedCallers>  
```  
  
```csharp  
[assembly:AllowPartiallyTrustedCallers]  
```  
  
 **Allowpartiallytreuhänder dcallersattribute** ist nur wirksam, wenn es von einer Assembly mit starkem Namen auf Assemblyebene angewendet wird. Weitere Informationen zum Anwenden von Attributen auf Assemblyebene finden Sie unter "Anwenden von Attributen [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] " in der SDK-Dokumentation.  
  
> [!CAUTION]  
>  Wenn **AllowPartiallyTrustedCallersAttribute** vorhanden ist, werden die Standardsicherheitsprüfungen von **FullTrustLinkDemand** verhindert. Dadurch kann die Assembly von einer anderen zum Teil vertrauenswürdigen Assembly aufgerufen werden. Alle Sicherheitsprüfungen, einschließlich der Attribute für die deklarative Sicherheit auf Klassen- oder Methodenebene, müssen explizit angegeben werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwenden benutzerdefinierter Assemblys mit Berichten](using-custom-assemblies-with-reports.md)  
  
  
