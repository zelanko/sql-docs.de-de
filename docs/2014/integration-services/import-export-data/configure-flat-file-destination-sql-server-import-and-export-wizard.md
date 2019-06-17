---
title: Flatfileziel konfigurieren (SQL Server-Import/Export-Assistent) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.impexpwizard.configureflatfiledest.f1
ms.assetid: 318e8da0-37d3-46cd-943a-fc5d66aad93a
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 6504e4f5eee83d670b4843fb8d956b23a84d4aad
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62893031"
---
# <a name="configure-flat-file-destination-sql-server-import-and-export-wizard"></a>Flatfileziel konfigurieren (SQL Server-Import/Export-Assistent)
  Verwenden der **Flatfileziel konfigurieren** Seite Formatierungsoptionen für die Zielflatfile angeben und eine Vorschau der Ergebnisse vor dem Fortfahren anzeigen.  
  
 Weitere Informationen zu diesem Assistenten finden Sie unter [SQL Server-Import / Export-Assistenten](import-and-export-data-with-the-sql-server-import-and-export-wizard.md). Weitere Informationen zu den Optionen zum Starten des Assistenten als auch die Berechtigungen erforderlich, um den Assistenten erfolgreich ausführen, finden Sie unter [führen Sie die SQL Server-Import / Export-Assistenten](start-the-sql-server-import-and-export-wizard.md).  
  
 Mit dem SQL Server-Import/Export-Assistenten werden Daten aus einer Quelle in ein Ziel kopiert. Mit dem Assistenten können auch eine Zieldatenbank und Zieltabellen erstellt werden. Wenn Sie jedoch mehrere Datenbanken, Tabellen oder andere Datenbankobjekte kopieren müssen, verwenden Sie stattdessen den Assistenten zum Kopieren von Datenbanken. Weitere Informationen finden Sie unter [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).  
  
## <a name="options"></a>Optionen  
 **Quellflatfile**  
 Der Name der Zieldatei.  
  
 **Zeilentrennzeichen**  
 Wählen Sie ein Trennzeichen für Zeilen aus der Liste aus.  
  
|Wert|Description|  
|-----------|-----------------|  
|**{CR}{LF}**|Als Trennzeichen für Zeilen dient ein Wagenrücklauf in Kombination mit einem Zeilenvorschub.|  
|**{CR}**|Als Trennzeichen für Zeilen dient ein Wagenrücklauf.|  
|**{LF}**|Als Trennzeichen für Zeilen dient ein Zeilenvorschub.|  
|**Semikolon {;}**|Als Trennzeichen für Zeilen dient ein Semikolon.|  
|**Doppelpunkt {:}**|Als Trennzeichen für Zeilen dient ein Doppelpunkt.|  
|**Komma {,}**|Als Trennzeichen für Zeilen dient ein Komma.|  
|**Tabulator {t}**|Als Trennzeichen für Zeilen dient ein Tabulator.|  
|**Senkrechter Strich {&#124;}**|Als Trennzeichen für Zeilen dient ein senkrechter Strich.|  
  
 **Spaltentrennzeichen**  
 Wählen Sie ein Trennzeichen für Spalten aus der Liste aus.  
  
|Wert|Description|  
|-----------|-----------------|  
|**{CR}{LF}**|Die Spalten dient ein Wagenrücklauf-Zeilenvorschub-Kombination.|  
|**{CR}**|Als Trennzeichen für Spalten dient ein Wagenrücklauf.|  
|**{LF}**|Als Trennzeichen für Spalten dient ein Zeilenvorschub.|  
|**Semikolon {;}**|Als Trennzeichen für Spalten dient ein Semikolon.|  
|**Doppelpunkt {:}**|Als Trennzeichen für Spalten dient ein Doppelpunkt.|  
|**Komma {,}**|Als Trennzeichen für Spalten dient ein Komma.|  
|**Tabulator {t}**|Als Trennzeichen für Spalten dient ein Tabulator.|  
|**Senkrechter Strich {&#124;}**|Als Trennzeichen für Spalten dient ein senkrechter Strich.|  
  
 **Vorschau**  
 Zeigen Sie in der **Vorschaudaten** Dialogfeld "Optionen" die Ergebnisse der ausgewählten Formatierungsoptionen für die Zielflatfile.  
  
 **Transformation bearbeiten**  
 Zeilen löschen, Anfügen von Zeilen und Spalten in der Zieldatei konfigurieren, mit der **Spaltenzuordnungen** Dialogfeld.  
  
  
