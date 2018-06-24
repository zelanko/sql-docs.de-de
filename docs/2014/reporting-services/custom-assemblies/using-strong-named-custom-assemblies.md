---
title: Verwenden von benutzerdefinierten Assemblys mit starken Namen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- AllowPartiallyTrustedCallersAttribute attribute
- strong-named custom assemblies [Reporting Services]
- strong names [Reporting Services]
- assemblies [Reporting Services], strong names
- custom assemblies [Reporting Services], strong-named
ms.assetid: ca9f19d7-6e86-46f2-b9ad-9bf807eaa52e
caps.latest.revision: 34
author: douglaslM
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 002445779b68832a9ff68eb35e5dfb4237f854c5
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36049396"
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
  
## <a name="see-also"></a>Siehe auch  
 [Verwenden benutzerdefinierter Assemblys mit Berichten](using-custom-assemblies-with-reports.md)  
  
  