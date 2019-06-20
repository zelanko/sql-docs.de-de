---
title: Transformations-Editor für die Überwachung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.audittransformation.f1
helpviewer_keywords:
- Audit Transformation Editor
ms.assetid: 32786a34-5870-4fde-83c7-ec74d62404b8
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 9d31f297b9544c75e416fe798facd6a1c328ff0d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66061420"
---
# <a name="audit-transformation-editor"></a>Transformations-Editor für Überwachung
  Mithilfe der Überwachungstransformation werden in den Datenfluss eines Pakets Daten zur Umgebung, in der das Paket ausgeführt wird, eingeschlossen. Dem Datenfluss kann z. B. der Name des Pakets, Computers und Operators hinzugefügt werden. [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] enthält Systemvariablen, die diese Informationen bereitstellen.  
  
 Weitere Informationen zur Überwachungstransformation finden Sie unter [Audit Transformation](data-flow/transformations/audit-transformation.md).  
  
## <a name="options"></a>Optionen  
 **Name der Ausgabespalte**  
 Geben Sie den Namen der neuen Ausgabespalte an, die die Überwachungsinformationen enthalten soll.  
  
 **Überwachungstyp**  
 Wählen Sie eine verfügbare Systemvariable zum Bereitstellen der Überwachungsinformationen aus.  
  
|Wert|Description|  
|-----------|-----------------|  
|**GUID der Ausführungsinstanz**|Fügen Sie die GUID ein, die die Ausführungsinstanz des Pakets eindeutig identifiziert.|  
|**Paket-ID**|Fügen Sie die GUID ein, die das Paket eindeutig identifiziert.|  
|**Paketname**|Fügen Sie den Paketnamen ein.|  
|**Versions-ID**|Fügen Sie die GUID ein, die die Paketversion eindeutig identifiziert.|  
|**Startzeit der Ausführung**|Fügen Sie den Zeitpunkt ein, zu dem mit der Ausführung des Pakets begonnen wird.|  
|**Computername**|Fügen Sie den Namen des Computers ein, auf dem das Paket gestartet wurde.|  
|**Benutzername**|Fügen Sie den Anmeldenamen des Benutzers ein, der das Paket gestartet hat.|  
|**Taskname**|Fügen Sie den Namen von dem Datenflusstask ein, mit dem die Überwachungstransformation verknüpft ist.|  
|**Task-ID**|Fügen Sie die GUID ein, die den mit der Überwachungstransformation verknüpften Datenflusstask eindeutig identifiziert.|  
  
## <a name="see-also"></a>Siehe auch  
 [Fehler- und Meldungsreferenz von Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)  
  
  
