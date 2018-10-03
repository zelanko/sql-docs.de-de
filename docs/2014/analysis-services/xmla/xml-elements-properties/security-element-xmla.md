---
title: Security-Element (XMLA) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Security Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.security
- urn:schemas-microsoft-com:xml-analysis#Security
- http://schemas.microsoft.com/analysisservices/2003/engine#Security
helpviewer_keywords:
- Security element
ms.assetid: 0b601f69-d16d-4d10-9361-b8afaa6ed357
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 784a3f6b56c0372897b984c5fac4e8915cb53ebc
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48111949"
---
# <a name="security-element-xmla"></a>Security-Element (XMLA)
  Gibt an, wie sichern oder Wiederherstellen von sicherheitsdefinitionen wie Rollen und Berechtigungen, während eine [Sicherung](../xml-elements-commands/backup-element-xmla.md) oder [wiederherstellen](../xml-elements-commands/restore-element-xmla.md) Befehl.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Backup> <!-- or Restore -->  
   ...  
   <Security>...</Security>  
   ...  
</Backup>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Zeichenfolge (Enumeration)|  
|Standardwert|*skipMembership*|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Sicherung](../xml-elements-commands/backup-element-xmla.md), [wiederherstellen](../xml-elements-commands/restore-element-xmla.md)|  
|Untergeordnete Elemente|None|  
  
## <a name="remarks"></a>Hinweise  
 Das `Security`-Element bestimmt, ob die Sicherheitsdefinitionen wie Rollen und Berechtigungen, die in einer [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]-Datenbank definiert sind, während eines `Backup`- oder eines `Restore`-Befehls gesichert bzw. wiederhergestellt werden. Dieses Element bestimmt außerdem, ob Windows-Benutzerkonten und Gruppen, die als Mitglieder der Sicherheitsdefinitionen definiert sind, als Teil des `Backup`- oder `Restore`-Befehls einbezogen werden.  
  
 Der Wert dieses Elements ist auf eine der in der folgenden Tabelle aufgelisteten Zeichenfolgen beschränkt.  
  
|value|Description|  
|-----------|-----------------|  
|*skipMembership*|Einbeziehen von Sicherheitsdefinitionen und Ausschließen von Informationen zur Mitgliedschaft während `Backup`- oder `Restore`-Befehlen.|  
|*CopyAll*|Einbeziehen von sicherheitsdefinitionen und Informationen zur Mitgliedschaft während `Backup` oder `Restore` Befehle.|  
|*IgnoreSecurity*|Ausschließen von sicherheitsdefinitionen während `Backup` oder `Restore` Befehle.|  
  
## <a name="see-also"></a>Siehe auch  
 [SynchronizeSecurity-Element &#40;XMLA&#41;](security-element-xmla.md)   
 [Eigenschaften &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
