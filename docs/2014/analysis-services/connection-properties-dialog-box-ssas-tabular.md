---
title: Im Dialogfeld Verbindungseigenschaften (SSAS – tabellarisch) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.asvs.ssmsimbi.ConnectionProperties.F1
ms.assetid: 17bae8ae-2ba0-4978-be70-61c687f59d54
caps.latest.revision: 6
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 29871222a68b9babfb2abd5b2d477316c1d6ac34
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37157241"
---
# <a name="connection-properties-dialog-box-ssas---tabular"></a>Verbindungseigenschaften (Dialogfeld, SSAS – tabellarisch)
  Verwenden Sie diese Seite zum Anzeigen oder Ändern der Verbindungseigenschaften einer Datenquelle, die von einem tabellarischen Modell verwendet wird, in SQL Server Management Studio.  
  
 In diesem Dialogfeld werden Zeitstempel und andere beschreibende Informationen sowie vom Benutzer anpassbare Eigenschaften bereitgestellt, die die Merkmale der Verbindung bestimmen.  
  
## <a name="options"></a>Tastatur  
  
|Begriff|Definition|  
|----------|----------------|  
|**Name**|Gibt den Namen der Datenquelle an.|  
|**ID**|Zeigt den Bezeichner des Datenquellenobjekts an.|  
|**Beschreibung**|Zeigt eine Beschreibung des Datenquellenobjekts an.|  
|**Timestamp erstellen**|Zeigt das Datum und die Uhrzeit der Erstellung der Datenbank an.|  
|**Letztes Schemaupdate**|Zeigt das Datum und die Uhrzeit des letzten Updates der Metadaten für die Datenbank an.|  
|**Verbindungszeichenfolge**|Zeigt die Verbindungszeichenfolge an, die verwendet wurde, um eine Verbindung mit der Datenquelle herzustellen, die dem Modell Daten bereitstellt.|  
|**Maximale Anzahl von Verbindungen**|Gibt die maximale Anzahl von Clientverbindungen zu dieser Datenbank an.|  
|**Isolation**|Gültige Werte sind ReadCommitted oder Snapshot. Weitere Informationen finden Sie unter [Isolation-Element &#40;ASSL&#41;](scripting/properties/isolation-element-assl.md).|  
|**Abfragetimeout**|Gibt die Zeit in Sekunden an, nach der bei einem Datenabfrageversuch ein Timeout eintritt.|  
|**Verwalteter Anbieter**|Bestimmt den Namen des verwalteten Anbieters. Wenn die Datenquellenverbindung einen systemeigenen OLE DB-Anbieter verwendet, ist dieser Wert leer.|  
|**Identitätswechselinformationen**|Gibt das für Datenbankverbindungen verwendete Identitätswechselkonto an, wenn Daten verarbeitet oder aktualisiert werden, sowie Abfragen, die für einen relationalen Datenspeicher ausgeführt werden (über DirectQuery), Out-of-Line-Bindungen, Remotepartitionen und die Datenbanksynchronisierung vom Ziel zur Quelle.<br /><br /> Gültige Werte enthalten das Analysis Services-Dienstkonto oder einen bestimmten Satz von Windows-Anmeldeinformationen. Lassen Sie die Optionen **Anmeldeinformationen des aktuellen Benutzers** oder **Erben**deaktiviert. Diese Optionen für Anmeldeinformationen werden für eine tabellarische Modelldatenbank nicht unterstützt.|  
  
  
