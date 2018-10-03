---
title: Massenimport und -export von Daten (SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- exporting data
- bulk importing [SQL Server], about bulk importing
- data [SQL Server], bulk export and import
- transferring data
- importing data, (See also bulk importing [SQL Server])
- copying data [SQL Server]
- bulk exporting [SQL Server]
- importing data, bulk import
- copying data [SQL Server], bulk export and import
- exporting data,(See also bulk exporting [SQL Server])
- bulk exporting [SQL Server], about bulk exporting
- bulk importing [SQL Server]
- importing data
ms.assetid: 19049021-c048-44a2-b38d-186d9f9e4a65
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 36065984f03980f54cbc6a75162bb007f8b5f772
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48124440"
---
# <a name="bulk-import-and-export-of-data-sql-server"></a>Massenimport und -export von Daten (SQL Server)
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützt den Massenexport von Daten (*Massendaten*) aus einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Tabelle und den Massenimport in eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Tabelle oder eine nicht partitionierte Sicht. Das Massenimportieren und -exportieren ist für die effiziente Datenübertragung zwischen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und Quellen heterogener Daten wichtig. Der*Massenexport* bezieht sich auf das Kopieren von Daten aus einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Tabelle in eine Datendatei. Beim*Massenimport* werden Daten aus einer Datendatei in eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Tabelle geladen. Sie können beispielsweise Daten von einer [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel-Anwendung in eine Datendatei exportieren und dann einen Massenimport der Daten in eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Tabelle ausführen.  
  
 **In diesem Thema:**  
  
-   [Einführung zu Massenimport- und Massenexportvorgängen](#Intro)  
  
-   [Verwandte Aufgaben](#RelatedTasks)  
  
##  <a name="Intro"></a> Massenimport und Übersicht über Massen-Export  
 Dieser Abschnitt enthält eine Auflistung und einen kurzen Vergleich der verschiedenen Methoden, die für den Massenimport und -export von Daten verfügbar sind. Der Abschnitt bietet darüber hinaus eine Einführung in Formatdateien.  
  
 **In diesem Thema:**  
  
-   [Methoden für den Massenimport importieren und Exportieren von Daten](#MethodsForBuliIE)  
  
-   [Formatdateien](#FFs)  
  
###  <a name="MethodsForBuliIE"></a> Methoden für den Massenimport importieren und Exportieren von Daten  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wird der Massenexport von Daten aus einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Tabelle und der Massenimport in eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Tabelle oder eine nicht partitionierte Sicht unterstützt. Dazu stehen die folgenden grundlegenden Methoden zur Verfügung.  
  
|Methode|Description|Importiert Daten|Exportiert Daten|  
|------------|-----------------|------------------|------------------|  
|[bcp (Hilfsprogramm)](import-and-export-bulk-data-by-using-the-bcp-utility-sql-server.md)|Ein Befehlszeilenprogramm (Bcp.exe), mit dem Massenexporte und -importe von Daten ausgeführt und Formatdateien generiert werden können.|Benutzerkontensteuerung|Benutzerkontensteuerung|  
|[BULK INSERT-Anweisung](import-bulk-data-by-using-bulk-insert-or-openrowset-bulk-sql-server.md)|Eine [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisung, mit der Daten direkt aus einer Datendatei in eine Datenbanktabelle oder nicht partitionierte Sicht importiert werden.|Benutzerkontensteuerung|nein|  
|[INSERT ... SELECT * FROM OPENROWSET(BULK...)-Anweisung](import-bulk-data-by-using-bulk-insert-or-openrowset-bulk-sql-server.md)|Eine [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisung, bei der mit dem OPENROWSET-Massenrowsetanbieter ein Massenimport von Daten in eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Tabelle ausgeführt wird. Dabei wird die OPENROWSET(BULK…)-Funktion angegeben, um Daten in einer INSERT-Anweisung auszuwählen.|Benutzerkontensteuerung|nein|  
  
> [!IMPORTANT]  
>  CSV (Comma-Separated Value)-Dateien werden von SQL Server-Massenimportvorgängen nicht unterstützt. In manchen Fällen kann jedoch eine CSV-Datei als Datendatei für einen Massenimport von Daten in SQL Server verwendet werden. Das Feldabschlusszeichen einer CSV-Datei muss kein Komma sein. Weitere Informationen finden Sie unter [Vorbereiten von Daten für den Massenexport oder -import &#40;SQL Server&#41;](prepare-data-for-bulk-export-or-import-sql-server.md).  
  
###  <a name="FFs"></a> Formatdateien  
 Das Hilfsprogramm **bcp** sowie die Anweisungen BULK INSERT und INSERT... SELECT \* FROM OPENROWSET(BULK...) unterstützen alle die Verwendung einer als *Formatdatei* bezeichneten speziellen Datei zum Speichern von Formatinformationen für jedes Feld in einer Datendatei. In einer Formatdatei können auch Informationen zu der korrespondierenden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Tabelle enthalten sein. Über die Formatdatei können alle Formatinformationen bereitgestellt werden, die für den Massenexport von Daten aus einer Instanz und für den Massenimport von Daten in eine Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]erforderlich sind.  
  
 Formatdateien bieten eine flexible Möglichkeit zum Interpretieren von Daten, wie diese in der Datendatei während des Imports vorhanden sind, und zum Formatieren von Daten in der Datendatei während des Exports. Durch diese Flexibilität besteht nicht mehr die Notwendigkeit, einen speziellen Code für das Interpretieren der Daten zu schreiben oder die Daten für die speziellen Anforderungen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder der externen Anwendung umzuformatieren. Wenn Sie beispielsweise einen Massenexport von Daten ausführen, die in eine Anwendung geladen werden sollen, für die durch Trennzeichen getrennte Werte erforderlich sind, können Sie eine Formatdatei verwenden, um Kommas als Feldabschlusszeichen in den exportierten Daten einzufügen.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützt zwei Arten von Formatdateien: XML-Formatdateien und Nicht-XML-Formatdateien.  
  
 Formatdateien können nur mithilfe des Hilfsprogramms **bcp** generiert werden. Weitere Informationen finden Sie unter [Erstellen einer Formatdatei &#40;SQL Server&#41;](create-a-format-file-sql-server.md). Weitere Informationen zu Formatdateien finden Sie unter [Formatdateien zum Importieren oder Exportieren von Daten &#40;SQL Server&#41;](format-files-for-importing-or-exporting-data-sql-server.md).  
  
> [!NOTE]  
>  Wenn keine Formatdatei während eines Massenexport- oder Massenimportvorgangs zur Verfügung steht, können Sie die Standardformatierung mithilfe der Befehlszeile überschreiben.  
  
##  <a name="RelatedTasks"></a> Verwandte Aufgaben  
  
-   [Importieren und Exportieren von Massendaten mithilfe des Hilfsprogramms Bcp &#40;SQL Server&#41;](import-and-export-bulk-data-by-using-the-bcp-utility-sql-server.md)  
  
-   [Importieren von Massendaten mithilfe von BULK INSERT oder OPENROWSET(Bulk...)&#40;BULK... &#41; &#40;SQLServer&#41;](import-bulk-data-by-using-bulk-insert-or-openrowset-bulk-sql-server.md)  
  
-   [Beibehalten von Identitätswerten beim Massenimport von Daten &#40;SQL Server&#41;](keep-identity-values-when-bulk-importing-data-sql-server.md)  
  
-   [Beibehalten von NULL-Werten oder Verwenden von Standardwerten während des Massenimports &#40;SQL Server&#41;](keep-nulls-or-use-default-values-during-bulk-import-sql-server.md)  
  
-   [Vorbereiten von Daten für den Massenexport oder -import &#40;SQL Server&#41;](prepare-data-for-bulk-export-or-import-sql-server.md)  
  
 **So verwenden Sie eine Formatdatei**  
  
-   [Erstellen einer Formatdatei &#40;SQL Server&#41;](create-a-format-file-sql-server.md)  
  
-   [Massenimport von Daten mithilfe einer Formatdatei &#40;SQL Server&#41;](use-a-format-file-to-bulk-import-data-sql-server.md)  
  
-   [Verwenden einer Formatdatei zum Zuordnen von Tabellenspalten zu Datendateifeldern &#40;SQL Server&#41;](use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server.md)  
  
-   [Auslassen eines Datenfelds mithilfe einer Formatdatei &#40;SQL Server&#41;](use-a-format-file-to-skip-a-data-field-sql-server.md)  
  
-   [Überspringen einer Tabellenspalte mithilfe einer Formatdatei &#40;SQL Server&#41;](use-a-format-file-to-skip-a-table-column-sql-server.md)  
  
 **So verwenden Sie Datenformate für Massenimport oder Massenexport**  
  
-   [Importieren von Daten aus früheren SQL Server-Versionen im systemeigenen Format oder im Zeichenformat](import-native-and-character-format-data-from-earlier-versions-of-sql-server.md)  
  
-   [Verwenden des Zeichenformats zum Importieren und Exportieren von Daten &#40;SQL Server&#41;](use-character-format-to-import-or-export-data-sql-server.md)  
  
-   [Verwenden des nativen Formats zum Importieren oder Exportieren von Daten &#40;SQL Server&#41;](use-native-format-to-import-or-export-data-sql-server.md)  
  
-   [Verwenden des Unicode-Zeichenformats zum Importieren und Exportieren von Daten &#40;SQL Server&#41;](use-unicode-character-format-to-import-or-export-data-sql-server.md)  
  
-   [Verwenden des nativen Unicode-Formats zum Importieren oder Exportieren von Daten &#40;SQL Server&#41;](use-unicode-native-format-to-import-or-export-data-sql-server.md)  
  
 **So geben Sie Datenformate für die Kompatibilität bei Verwendung von bcp an**  
  
1.  [Angeben von Feld- und Zeilenabschlusszeichen &#40;SQL Server&#41;](specify-field-and-row-terminators-sql-server.md)  
  
2.  [Angeben der Präfixlänge in Datendateien mittels bcp &#40;SQL Server&#41;](specify-prefix-length-in-data-files-by-using-bcp-sql-server.md)  
  
3.  [Angeben des Dateispeichertyps mithilfe von bcp &#40;SQL Server&#41;](specify-file-storage-type-by-using-bcp-sql-server.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Voraussetzungen für die minimale Protokollierung beim Massenimport](prerequisites-for-minimal-logging-in-bulk-import.md)   
 [Formatdateien zum Importieren oder Exportieren von Daten &#40;SQL Server&#41;](format-files-for-importing-or-exporting-data-sql-server.md)   
 [Beispiele für den Massenimport und -export von XML-Dokumenten &#40;SQL Server&#41;](examples-of-bulk-import-and-export-of-xml-documents-sql-server.md)   
 [SQL Server Integration Services](../../integration-services/sql-server-integration-services.md)   
 [Kopieren von Datenbanken auf andere Server](../databases/copy-databases-to-other-servers.md)   
 [Ausführen von Massenladen von XML-Daten &#40;SQLXML 4.0&#41;](../sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/performing-bulk-load-of-xml-data-sqlxml-4-0.md)   
 [Durchführen von Massenkopiervorgängen](../native-client/features/performing-bulk-copy-operations.md)   
 [bcp (Hilfsprogramm)](../../tools/bcp-utility.md)   
 [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql)   
 [Formatdateien zum Importieren oder Exportieren von Daten &#40;SQL Server&#41;](format-files-for-importing-or-exporting-data-sql-server.md)   
 [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql)  
  
  
