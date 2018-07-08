---
title: Dialogfeld "Eigenschaften" (SSAS – mehrdimensional)-Datenbank | Microsoft-Dokumentation
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
- sql12.asvs.sqlserverstudio.databaseproperties.f1
ms.assetid: 70f000b7-917f-4699-b142-7a0d13ff767c
caps.latest.revision: 22
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 2c138f61c17f79ed264dda4c28be766a7b41c9b2
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37157371"
---
# <a name="database-properties-dialog-box-ssas---multidimensional"></a>Datenbankeigenschaften (Dialogfeld, SSAS – mehrdimensional)
  Mithilfe des Dialogfelds **Datenbankeigenschaften** in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] können Sie die Eigenschaften einer Datenbank in einer [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Datenbank festlegen. Klicken Sie zum Anzeigen des Dialogfelds **Datenbankeigenschaften** im Objekt-Explorer mit der rechten Maustaste auf eine Datenbank, und wählen Sie **Eigenschaften**aus.  
  
## <a name="options"></a>Tastatur  
  
|Begriff|Definition|  
|----------|----------------|  
|**Name**|Hier können Sie einen Namen für die Datenbank eingeben.|  
|**ID**|Zeigt den Bezeichner der Datenbank an.|  
|**Beschreibung**|Hier können Sie eine neue Beschreibung für die Datenbank eingeben.|  
|**Timestamp erstellen**|Zeigt das Datum und die Uhrzeit der Erstellung der Datenbank an.|  
|**Letztes Schemaupdate**|Zeigt das Datum und die Uhrzeit des letzten Updates der Metadaten für die Datenbank an.|  
|**Letztes Update**|Zeigt das Datum und den Uhrzeit des letzten Updates der Daten für die Datenbank an.|  
|**Identitätswechselinformationen der Datenquelle**|Wählen Sie die Identitätswechselinformationen aus, die von der Datenbank bei der Verbindung und der Interaktion mit Datenquellen verwendet werden, die in der Datenbank enthalten sind. Folgende Werte sind gültig:<br /><br /> **ImpersonateAccount** (verwenden Sie einen bestimmten Windows-Benutzernamen und ein entsprechendes Kennwort)<br /><br /> **ImpersonateService** (verwenden Sie das Dienstkonto)<br /><br /> **ImpersonateCurrentUser** (verwenden Sie die Anmeldeinformationen des aktuellen Benutzers)<br /><br /> **Standard** (verwenden Sie das Dienstkonto für MOLAP-Vorgänge und den aktuellen Benutzer für Data Mining)<br /><br /> Obwohl Sie die Einstellungen für den Datenquellenidentitätswechsel auf Datenbankebene festlegen können, beeinflusst dieser Vorgang nur die Datenquellen, bei denen **Erben** für zugehörige Identitätswechseleinstellungen festgelegt ist. Direkt auf Datenquellenebene angegebene Identitätswechseleinstellungen setzen stets die Einstellungen außer Kraft, die auf Datenbankebene angegeben wurden.<br /><br /> Wenn Sie eine Identitätswechseloption auswählen, berücksichtigen Sie die Vorgangstypen, die unterstützt werden müssen. Einige Vorgänge wie die Verarbeitung können nicht ausgeführt werden.|  
|**Zuletzt verarbeitet**|Zeigt das Datum und die Uhrzeit an, zu der die Datenbank zuletzt verarbeitet wurde.|  
|**Geschätzte Größe**|Zeigt die geschätzte Größe der Datenbank an.|  
|**Speicherort**|Gibt den Ort der Datenbank an. Wenn sich die Datenbank im Standarddatenverzeichnis befindet, ist dieser Wert leer.|  
  
## <a name="see-also"></a>Siehe auch  
 [Analysis Services-Designer und-Dialogfelder &#40;mehrdimensionale Daten&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)   
 [Mehrdimensionale Modelldatenbanken &#40;SSAS&#41;](multidimensional-models/multidimensional-model-databases-ssas.md)  
  
  
