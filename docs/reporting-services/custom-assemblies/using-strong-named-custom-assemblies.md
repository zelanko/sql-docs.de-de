---
title: Verwenden von benutzerdefinierten Assemblys mit starken Namen | Microsoft-Dokumentation
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: custom-assemblies
ms.topic: reference
helpviewer_keywords:
- AllowPartiallyTrustedCallersAttribute attribute
- strong-named custom assemblies [Reporting Services]
- strong names [Reporting Services]
- assemblies [Reporting Services], strong names
- custom assemblies [Reporting Services], strong-named
ms.assetid: ca9f19d7-6e86-46f2-b9ad-9bf807eaa52e
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 0c315f5c76c13970d5f3555cb3393ca0877116b9
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47754333"
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
  
 **AllowPartiallyTrustedCallersAttribute** ist nur dann wirksam, wenn es von einer Assembly mit starkem Namen auf der Assemblyebene angewandt wird. Weitere Informationen über das Anwenden von Attributen auf der Assemblyebene finden Sie unter „Applying Attributes“ (Anwenden von Attributen) in der [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK-Dokumentation.  
  
> [!CAUTION]  
>  Wenn **AllowPartiallyTrustedCallersAttribute** vorhanden ist, werden die Standardsicherheitsprüfungen von **FullTrustLinkDemand** verhindert. Dadurch kann die Assembly von einer anderen zum Teil vertrauenswürdigen Assembly aufgerufen werden. Alle Sicherheitsprüfungen, einschließlich der Attribute für die deklarative Sicherheit auf Klassen- oder Methodenebene, müssen explizit angegeben werden.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Verwenden benutzerdefinierter Assemblys mit Berichten](../../reporting-services/custom-assemblies/using-custom-assemblies-with-reports.md)  
  
  
