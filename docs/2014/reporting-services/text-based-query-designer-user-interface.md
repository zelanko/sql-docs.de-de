---
title: Benutzeroberfläche des textbasierten Abfrage-Designers | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- "10010"
- sql12.rtp.rptdesigner.dataview.genericquerydesigner.f1
helpviewer_keywords:
- text-based query designer [Reporting Services]
- query designers [Reporting Services], text-based
ms.assetid: 44b7c664-03aa-494e-a484-052b318e810c
caps.latest.revision: 25
author: maggiesmsft
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 4e24396a7b851bf3e210bd31318f52b757f15a46
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37177087"
---
# <a name="text-based-query-designer-user-interface"></a>Benutzeroberfläche des textbasierten Abfrage-Designers
  Verwenden Sie den textbasierten Abfrage-Designer, um eine Abfrage mithilfe der Abfragesprache zu verwenden, die von der Datenquelle unterstützt wird, führen Sie die Abfrage aus, und zeigen Sie die Ergebnisse zur Entwurfszeit an. Sie können mehrere [!INCLUDE[tsql](../includes/tsql-md.md)] -Anweisungen, Abfrage- oder Befehlssyntaxen für benutzerdefinierte Datenverarbeitungserweiterungen und Abfragen angeben, die als Ausdrücke angegeben sind. Da der textbasierte Abfrage-Designer die Abfrage nicht zuvor verarbeitet und eine beliebige Abfragesyntax aufnehmen kann, handelt es sich hierbei um das standardmäßige Abfrage-Designer-Tool für viele Datenquellentypen.  
  
 Der textbasierte Abfrage-Designer zeigt eine Symbolleiste und die folgenden zwei Bereiche an:  
  
-   **Abfrage** zeigt den Abfragetext, den Tabellennamen oder den Name der gespeicherten Prozedur.  
  
-   **Ergebnis** Zeigt die Ergebnisse einer Ausführung der Abfrage zur Entwurfszeit an.  
  
## <a name="text-based-query-designer-toolbar"></a>Symbolleiste für den textbasierten Abfrage-Designer  
 Der textbasierte Abfrage-Designer stellt eine einzige Symbolleiste für alle Befehlstypen bereit. In der folgenden Tabelle werden jede Schaltfläche auf der Symbolleiste und ihre Funktion aufgelistet.  
  
|Schaltfläche|Description|  
|------------|-----------------|  
|**Als Text bearbeiten**|Wechseln zwischen dem textbasierten Abfrage-Designer und dem grafischen Abfrage-Designer. Nicht alle Datenquellentypen unterstützen grafische Abfrage-Designer.|  
|**Importieren**|Importiert eine vorhandene Abfrage aus einer Datei oder einem Bericht. Nur die Dateitypen SQL und RDL werden unterstützt. Weitere Informationen finden Sie unter [Erstellen von Berichten zu eingebetteten und freigegebenen Datasets &#40;Berichts-Generator und SSRS&#41;](report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md).|  
|![Führen Sie die Abfrage aus](../analysis-services/media/rsqdicon-run.gif "Run the query")|Führen Sie die Abfrage aus, und zeigen Sie das Resultset im Ergebnisbereich an.|  
|**Befehlstyp**|Wählen Sie **Text**, **StoredProcedure**oder **TableDirect**. Weist eine gespeicherte Prozedur Parameter auf, wird das Dialogfeld **Abfrageparameter definieren** angezeigt, wenn Sie auf der Symbolleiste auf **Ausführen** klicken. Sie können nach Bedarf Werte eingeben. Beachten Sie, wenn eine gespeicherte Prozedur mehrere Resultsets zurückgibt, nur das erste Resultset verwenden, um das Dataset zu füllen.<br /><br /> Unterstützung für den Befehlstyp ändert sich jeweils nach dem Datenquellentyp. Nur OLE DB und ODBC unterstützen z.B. **TableDirect**.|  
  
### <a name="command-type-text"></a>Befehlstyp "Text"  
 Wenn Sie ein [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Dataset erstellen, wird vom Berichts-Designer standardmäßig der grafische Abfrage-Designer angezeigt. Wenn Sie zum textbasierten Abfrage-Designer wechseln möchten, klicken Sie auf der Symbolleiste auf die Umschaltfläche **Als Text bearbeiten** . Der textbasierte Abfrage-Designer hat zwei Bereiche: den Abfragebereich und den Ergebnisbereich. In der folgenden Abbildung werden die einzelnen Bereiche bezeichnet.  
  
 ![Generischer Abfrage-Designer für relationale Datenabfragen](../analysis-services/media/rsqd-dsaw-sql-generic.gif "Generic query designer, for relational data query")  
  
 Die folgende Tabelle beschreibt die Funktion jedes Bereichs.  
  
|Bereich|Funktion|  
|----------|--------------|  
|Dataseteigenschaften|Zeigt den [!INCLUDE[tsql](../includes/tsql-md.md)] -Abfragetext an. In diesem Bereich schreiben oder bearbeiten Sie eine [!INCLUDE[tsql](../includes/tsql-md.md)] -Abfrage.|  
|Ergebnis|Zeigt die Ergebnisse der Abfrage an. Klicken Sie zum Ausführen der Abfrage mit der rechten Maustaste in einen beliebigen Bereich, und klicken Sie auf **Ausführen**, oder klicken Sie auf der Symbolleiste auf **Ausführen** .|  
  
#### <a name="example"></a>Beispiel  
 Die folgende Abfrage gibt die Liste der Nachnamen aus der `Contact`-Tabelle der [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)]-Datenbank zurück.  
  
```  
SELECT LastName FROM Person.Person;  
```  
  
 Sie können eine beliebige [!INCLUDE[tsql](../includes/tsql-md.md)]-Anweisung als Befehlstyp Text verwenden, einschließlich `EXEC`-Anweisungen. Die folgende Abfrage ruft die gespeicherte Prozedur `uspGetEmployeeManagers` von [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] auf und gibt die Befehlskette für den Mitarbeiter mit der ID 1 zurück.  
  
```  
EXEC uspGetEmployeeManagers 1;  
```  
  
 Wenn Sie auf der Symbolleiste auf **Ausführen** klicken, wird der Befehl im **Abfragebereich** ausgeführt, und die Ergebnisse werden im **Ergebnisbereich** angezeigt.  
  
### <a name="command-type-storedprocedure"></a>StoredProcedure-Befehlstyp  
 Wenn Sie den **Befehlstyp StoredProcedure**auswählen, zeigt der textbasierte Abfrage-Designer zwei Bereiche an: den Abfragebereich und den Ergebnisbereich. Geben Sie den Namen der gespeicherten Prozedur im Bereich **Abfrage** ein, und klicken Sie auf der Symbolleiste auf Ausführen. Das Dialogfeld Abfrageparameter definieren wird geöffnet. Geben Sie die Parameterwerte für die gespeicherte Prozedur ein. Für jeden Parameter einer gespeicherten Prozedur wird ein Berichtsparameter erstellt.  
  
#### <a name="example"></a>Beispiel  
 Die folgende Abfrage ruft die gespeicherte [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)]-Prozedur `uspGetEmployeeManagers` auf. Sie müssen einen Wert für den Mitarbeiter-ID-Parameter eingeben, wenn Sie die Abfrage ausführen.  
  
```  
uspGetEmployeeManagers;  
```  
  
### <a name="command-type-tabledirect"></a>TableDirect-Befehlstyp  
 Wenn Sie den **Befehlstyp TableDirect**auswählen, zeigt der textbasierte Abfrage-Designer zwei Bereiche an: den Abfragebereich und den Ergebnisbereich. Wenn Sie eine Tabelle auswählen und auf die Schaltfläche **Ausführen** klicken, werden alle Spalten für diese Tabelle zurückgegeben.  
  
#### <a name="example"></a>Beispiel  
 Die folgende Abfrage gibt ein Resultset für alle Kunden in der [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)]-Datenbank zurück.  
  
 `Sales.Customer`  
  
 Wenn Sie den Namen der Tabelle Sales.Customer eingeben, entspricht der Erstellung der [!INCLUDE[tsql](../includes/tsql-md.md)] Anweisung `SELECT * FROM Sales.Customer;`.  
  
## <a name="see-also"></a>Siehe auch  
 [Abfrageentwurfstools im Berichts-Designer SQL-Server-Datatools &#40;SSRS&#41;](report-data/query-design-tools-ssrs.md)   
 [Erstellen von Berichten zu eingebetteten und freigegebenen Datasets &#40;Berichts-Generator und SSRS&#41;](report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)   
 [SQL Server-Verbindungstyp &#40;SSRS&#41;](report-data/sql-server-connection-type-ssrs.md)   
 [OLE DB-Verbindungstyp (SSRS)](report-data/ole-db-connection-type-ssrs.md)   
 [ODBC-Verbindungstyp &#40;SSRS&#41;](report-data/odbc-connection-type-ssrs.md)   
 [Erstellen von Berichten zu eingebetteten und freigegebenen Datasets &#40;Berichts-Generator und SSRS&#41;](report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)   
 [RSReportDesigner Configuration File (RSReportDesigner-Konfigurationsdatei)](report-server/rsreportdesigner-configuration-file.md)  
  
  
