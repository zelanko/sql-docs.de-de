---
title: Flatfileziel konfigurieren (SQL Server-Import/Export-Assistent) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.impexpwizard.configureflatfiledest.f1
ms.assetid: 318e8da0-37d3-46cd-943a-fc5d66aad93a
caps.latest.revision: 30
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 033b602d712d4ec6e0caf136b1228cd82b552e08
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36060747"
---
# <a name="configure-flat-file-destination-sql-server-import-and-export-wizard"></a>Flatfileziel konfigurieren (SQL Server-Import/Export-Assistent)
  Verwenden der **Flatfileziel konfigurieren** Seite Formatierungsoptionen für die Zielflatfile angeben und eine Vorschau der Ergebnisse zuerst anzeigen.  
  
 Weitere Informationen zu diesem Assistenten finden Sie unter [SQL Server-Import / Export-Assistenten](import-and-export-data-with-the-sql-server-import-and-export-wizard.md). Weitere Informationen zu den Optionen zum Starten des Assistenten als auch die Berechtigungen erforderlich, um den Assistenten erfolgreich ausführen finden Sie unter [führen Sie die SQL Server-Import / Export-Assistenten](start-the-sql-server-import-and-export-wizard.md).  
  
 Mit dem SQL Server-Import/Export-Assistenten werden Daten aus einer Quelle in ein Ziel kopiert. Mit dem Assistenten können auch eine Zieldatenbank und Zieltabellen erstellt werden. Wenn Sie jedoch mehrere Datenbanken, Tabellen oder andere Datenbankobjekte kopieren müssen, verwenden Sie stattdessen den Assistenten zum Kopieren von Datenbanken. Weitere Informationen finden Sie unter [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).  
  
## <a name="options"></a>Tastatur  
 **Quellflatfile**  
 Der Name der Zieldatei.  
  
 **Zeilentrennzeichen**  
 Wählen Sie ein Trennzeichen für Zeilen aus der Liste aus.  
  
|value|Description|  
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
  
|value|Description|  
|-----------|-----------------|  
|**{CR}{LF}**|Als Trennzeichen für Spalten dient ein Wagenrücklauf-Zeilenvorschub Kombination.|  
|**{CR}**|Als Trennzeichen für Spalten dient ein Wagenrücklauf.|  
|**{LF}**|Als Trennzeichen für Spalten dient ein Zeilenvorschub.|  
|**Semikolon {;}**|Als Trennzeichen für Spalten dient ein Semikolon.|  
|**Doppelpunkt {:}**|Als Trennzeichen für Spalten dient ein Doppelpunkt.|  
|**Komma {,}**|Als Trennzeichen für Spalten dient ein Komma.|  
|**Tabulator {t}**|Als Trennzeichen für Spalten dient ein Tabulator.|  
|**Senkrechter Strich {&#124;}**|Als Trennzeichen für Spalten dient ein senkrechter Strich.|  
  
 **Vorschau**  
 Zeigen Sie in der **Vorschaudaten** (Dialogfeld), die die Ergebnisse der ausgewählten Formatierungsoptionen für die Zielflatfile Optionen.  
  
 **Transformation bearbeiten**  
 Löschen von Zeilen, Anfügen von Zeilen und Spalten in der Zieldatei konfigurieren, mit der **Spaltenzuordnungen** (Dialogfeld).  
  
  