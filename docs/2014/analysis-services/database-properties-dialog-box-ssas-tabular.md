---
title: Daten Bank Eigenschaften (Dialog Feld) (SSAS-tabellarisch) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.ssmsimbi.DatabaseProperties.f1
ms.assetid: 0f0ec02f-7b55-40ea-8a04-ed0deb1efd7a
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 8361508d678e407be9bed6eb18e8c221364daf61
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66082363"
---
# <a name="database-properties-dialog-box-ssas---tabular"></a>Datenbankeigenschaften (Dialogfeld, SSAS – tabellarisch)
  In diesem Dialogfeld werden Zeitstempel und andere beschreibende Informationen bereitgestellt. Außerdem sind anpassbare Eigenschaften vorhanden, die bestimmen, ob die Datenbank zwischengespeicherte Daten verwendet. Andere vom Benutzer anpassbare Eigenschaften sind z. B. das Ändern des Datenbanknamens und das Angeben der Identitätswechseloptionen.  
  
## <a name="options"></a>Tastatur  
  
|Begriff|Definition|  
|----------|----------------|  
|**Name**|**Name** ist der Datenbankname, der die Datenbank auf dem Server eindeutig identifiziert. Wenn Sie den Datenbanknamen ändern, sollten Sie die Auswirkungen auf Berichte und Clientanwendungen beachten, in denen der aktuelle Name in vorhandenen Verbindungszeichenfolgen verwendet wird. Sie müssen Verbindungszeichenfolgen in vorhandenen Berichten aktualisieren, um Zugriffsverweigerungsfehler zu vermeiden. Außerdem verwendet das tabellarische Modell, das als Quelle dieser Datenbank dient, in den meisten Fällen den ursprünglichen Namen. Erwägen Sie, die Eigenschaften für die Datenbankbereitstellung im Modell zu aktualisieren, um sicherzustellen, dass zukünftige Updates dieses Modells in der gewünschten Datenbank veröffentlicht werden.|  
|**id**|Zeigt den Bezeichner der Datenbank an.|  
|**Beschreibung**|Hier können Sie eine neue Beschreibung für die Datenbank eingeben.|  
|**Timestamp erstellen**|Zeigt das Datum und die Uhrzeit der Erstellung der Datenbank an.|  
|**Letzte Schema Aktualisierung**|Zeigt das Datum und die Uhrzeit des letzten Updates der Metadaten für die Datenbank an.|  
|**Letztes Update**|Zeigt das Datum und den Uhrzeit des letzten Updates der Daten für die Datenbank an.|  
|**Lese-/Schreibmodus**|Dies ist eine schreibgeschützte Eigenschaft, die Sie jedoch mit einer Sequenz von **Trennen**- und **Anfügen**-Befehlen ändern können, wobei die Eigenschaft ein Parameter des Befehls **Anfügen** ist. Weitere Informationen finden Sie unter [Datenbank-ReadWriteModes](multidimensional-models/database-readwritemodes.md).|  
|**DirectQueryMode**|Gibt an, ob die Datenbank nur arbeitsspeicherinterne Speicherung (keine Speicherung auf der Festplatte), nur datenträgerbasierte Speicherung oder eine Kombination beider Verfahren verwendet. Gültige Werte sind InMemory, DirectQuery, InMemoryWithDirectQuery (hauptsächlich speicherbasiert mit Teilauslagerung auf Datenträger) oder DirectQueryWithInMemory (hauptsächlich datenträgerbasiert mit Teilspeicherung im Arbeitsspeicher). Weitere Informationen finden Sie unter [directquery-Bereitstellungs Szenarien &#40;tabellarischen SSAS-&#41;](directquery-deployment-scenarios-ssas-tabular.md).|  
|**Identitätswechselinformationen der Datenquelle**|Gibt das für Datenbankverbindungen verwendete Identitätswechselkonto an, wenn Daten auf lokalen Partitionen oder Remotepartitionen aktualisiert werden, sowie Abfragen, die für einen relationalen Datenspeicher ausgeführt werden (über DirectQuery), Out-of-Line-Bindungen und die Datenbanksynchronisierung vom Ziel zur Quelle.<br /><br /> Gültige Werte enthalten das Analysis Services-Dienstkonto oder einen bestimmten Satz von Windows-Anmeldeinformationen. Aktivieren Sie nicht die Option **Anmeldeinformationen des aktuellen Benutzers verwenden**. Diese Option für Anmeldeinformationen wird für eine tabellarische Modelldatenbank nicht unterstützt.|  
|**Zuletzt verarbeitet**|Zeigt das Datum und die Uhrzeit an, zu der die Datenbank zuletzt verarbeitet wurde.|  
|**Geschätzte Größe**|Zeigt die geschätzte Größe der Datenbank an.|  
|**Speicherort**|Gibt den Ort der Datenbank an. Wenn sich die Datenbank im Standarddatenverzeichnis befindet, ist dieser Wert leer.|  
  
  
