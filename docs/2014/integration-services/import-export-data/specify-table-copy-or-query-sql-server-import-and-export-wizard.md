---
title: Tabelle kopieren oder Datenbank abfragen (SQL Server-Import/Export-Assistent) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.impexpwizard.specifytablecopyorquery.f1
ms.assetid: 08aa7158-40e6-4ef3-84d3-1265a8ba194c
caps.latest.revision: 43
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 413dd857be0ab913f43bd07f9c2f82d536137dad
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36058743"
---
# <a name="specify-table-copy-or-query-sql-server-import-and-export-wizard"></a>Tabelle kopieren oder Datenbank abfragen (SQL Server-Import/Export-Assistent)
  Verwenden der **geben Tabelle kopieren oder Datenbank Abfragen** Seite, um anzugeben, wie Daten zu kopieren. Sie können eine grafische Oberfläche zum Auswählen zu kopierender vorhandener Datenbankobjekte verwenden, oder Sie erstellen mithilfe von Transact-SQL eine komplexere Abfrage.  
  
 Weitere Informationen zu diesem Assistenten finden Sie unter [SQL Server-Import / Export-Assistenten](import-and-export-data-with-the-sql-server-import-and-export-wizard.md). Weitere Informationen zu den Optionen zum Starten des Assistenten als auch die Berechtigungen erforderlich, um den Assistenten erfolgreich ausführen finden Sie unter [führen Sie die SQL Server-Import / Export-Assistenten](start-the-sql-server-import-and-export-wizard.md).  
  
 Mit dem SQL Server-Import/Export-Assistenten werden Daten aus einer Quelle in ein Ziel kopiert. Mit dem Assistenten können auch eine Zieldatenbank und Zieltabellen erstellt werden. Wenn Sie jedoch mehrere Datenbanken, Tabellen oder andere Datenbankobjekte kopieren müssen, verwenden Sie stattdessen den Assistenten zum Kopieren von Datenbanken. Weitere Informationen finden Sie unter [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).  
  
## <a name="options"></a>Tastatur  
 **Daten aus mindestens einer Tabelle oder Sicht kopieren**  
 Kopieren Sie Felder aus ausgewählten Quelltabellen und-Sichten an das angegebene Ziel oder die Ziele mithilfe der **wählen Quelltabellen und-Sichten** (Dialogfeld). Verwenden Sie diese Option, wenn Sie alle Quelldaten ohne Filtern oder Ordnen der Datensätze kopieren möchten.  
  
 Bei Verwendung einer [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] -Datenanbieter für die Verbindung mit Ihrer Datenquelle den **Kopieren von Daten aus Tabellen oder Sichten** Option möglicherweise nicht zur Verfügung. Diese Option ist nur für Anbieter verfügbar, die über einen ProviderDescription-Abschnitt in der Datei ProviderDescriptors.xml verfügen. Jeder ProviderDescription-Abschnitt enthält die Informationen, die erforderlich sind, um Metadaten von dem entsprechenden Anbieter abzurufen. Standardmäßig enthält die Datei ProviderDescriptors.xml nur für die folgenden Anbieter einen ProviderDescription-Abschnitt:  
  
-   System.Data.SqlClient  
  
-   System.Data.OracleClient  
  
-   System.Data.OleDb  
  
-   System.Data.Odbc  
  
 Vornehmen der **Kopieren von Daten aus Tabellen oder Sichten** option für weitere Anbieter verfügbar, die dritte können eigene ProviderDescriptor-Abschnitte der Datei "ProviderDescriptors.xml" hinzufügen. Standardmäßig ist diese Datei \< *Laufwerk*>: \Programme\Microsoft SQL Server\100\DTS\ProviderDescriptors. Um die Anforderungen für den ProviderDescriptor-Abschnitt zu prüfen, öffnen Sie die Schemadatei ProviderDescriptors.xsd, die sich standardmäßig im selben Ordner befindet wie die Datei ProviderDescriptors.xml.  
  
 **Abfrage zum Angeben der zu übertragenden Daten schreiben**  
 Erstellen von SQL-Anweisungen zum Abrufen von Zeilen mithilfe der **Quellabfrage angeben** (Dialogfeld). Mit dieser Option können Sie die Quelldaten während des Kopiervorgangs ändern oder einschränken. Nur die Zeilen, die den Auswahlkriterien entsprechen, stehen dann zum Kopieren zur Verfügung.  
  
  