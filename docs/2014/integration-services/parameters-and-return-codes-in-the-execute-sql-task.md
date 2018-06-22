---
title: Parameter und Rückgabecodes dem Task SQL ausführen | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- return codes [Integration Services]
- parameters [Integration Services]
- parameterized SQL statements [Integration Services]
- Execute SQL task [Integration Services]
ms.assetid: a3ca65e8-65cf-4272-9a81-765a706b8663
caps.latest.revision: 28
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 949fefc6beb432eaee882b3a842279a9531f3fbf
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36059659"
---
# <a name="parameters-and-return-codes-in-the-execute-sql-task"></a>Parameter und Rückgabecodes im Task 'SQL ausführen'
  SQL-Anweisungen und gespeicherte Prozeduren verwenden häufig `input` Parameter `output` Parametern und Rückgabecodes. In [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] unterstützt der Task „SQL ausführen“ die Parametertypen `Input`, `Output` und `ReturnValue`. Verwenden Sie die `Input` Typ für Eingabeparameter, `Output` für Ausgabeparameter und `ReturnValue` Rückgabecodes.  
  
> [!NOTE]  
>  Parameter können in einem Task SQL ausführen nur verwendet werden, wenn dies vom Datenanbieter unterstützt wird.  
  
 Parameter in SQL-Befehlen, einschließlich Abfragen und gespeicherte Prozeduren, werden benutzerdefinierten Variablen zugeordnet, die im Bereich des Tasks "SQL ausführen", eines übergeordneten Containers oder im Bereich des Pakets erstellt werden. Die Werte für Variablen können zur Entwurfszeit festgelegt oder zur Laufzeit dynamisch aufgefüllt werden. Sie können Parameter auch Systemvariablen zuordnen. Weitere Informationen finden Sie unter [Integration Services-Variablen &#40;SSIS&#41;](integration-services-ssis-variables.md) und [Systemvariablen](system-variables.md).  
  
 Das Arbeiten mit Parametern und Rückgabecodes in einem Task „SQL ausführen“ bedeutet jedoch mehr, als nur zu wissen, welche Parametertypen der Task unterstützt und wie diese Parameter zugeordnet werden. Es müssen weitere Benutzungsanforderungen und Richtlinien beachtet werden, um Parameter und Rückgabecodes erfolgreich in einem Task „SQL ausführen“ zu verwenden. Diese Benutzungsanforderungen und Richtlinien werden am Ende dieses Themas behandelt:  
  
-   [Verwenden von Parametern, Namen und Markern](#Parameter_names_and_markers)  
  
-   [Verwenden von Parametern mit Datums- und Zeitdatentypen](#Date_and_time_data_types)  
  
-   [Verwenden von Parametern in WHERE-Klauseln](#WHERE_clauses)  
  
-   [Verwenden von Parametern mit gespeicherten Prozeduren](#Stored_procedures)  
  
-   [Abrufen von Rückgabecodewerten](#Return_codes)  
  
-   [Konfigurieren von Parametern und Rückgabecodes in SQL Task Editor für den Task](#Configure_parameters_and_return_codes)  
  
##  <a name="Parameter_names_and_markers"></a> Verwenden von Parameternamen und Markern  
 Die Syntax des SQL-Befehls verwendet verschiedene Parametermarkierungen, je nach verwendetem Verbindungstyp im Task SQL ausführen. Beispielsweise erfordert der [!INCLUDE[vstecado](../includes/vstecado-md.md)]-Verbindungs-Manager-Typ, dass der SQL-Befehl eine Parametermarkierung im Format **@varParameter** verwendet, während für den OLEDB-Verbindungstyp das Fragezeichen („?“) als Parametermarkierung erforderlich ist.  
  
 Die Namen, die in den Zuordnungen zwischen Variablen und Parametern als Parameternamen verwendet werden können, variieren ebenfalls je nach Managertyp. Beispielsweise verwendet der [!INCLUDE[vstecado](../includes/vstecado-md.md)]-Verbindungs-Managertyp einen benutzerdefinierten Namen mit einem @-Präfix, während der OLE DB-Verbindungs-Managertyp die Verwendung des numerischen Wertes einer 0-basierten Ordnungszahl als Parameternamen erfordert.  
  
 In der folgenden Tabelle finden Sie eine Auflistung der Anforderungen für SQL-Befehle für Verbindungs-Managertypen, die der Task SQL ausführen verwenden kann.  
  
|Verbindungstyp|Parametermarkierung|Parametername|Beispiel SQL-Befehl|  
|---------------------|----------------------|--------------------|-------------------------|  
|ADO|?|Param1, Param2, …|SELECT FirstName, LastName, Title FROM Person.Contact WHERE ContactID = ?|  
|[!INCLUDE[vstecado](../includes/vstecado-md.md)]|@\<Parametername>|@\<Parametername>|SELECT FirstName, LastName, Title FROM Person.Contact WHERE ContactID = @parmContactID|  
|ODBC|?|1, 2, 3, …|SELECT FirstName, LastName, Title FROM Person.Contact WHERE ContactID = ?|  
|EXCEL und OLE DB|?|0, 1, 2, 3, …|SELECT FirstName, LastName, Title FROM Person.Contact WHERE ContactID = ?|  
  
### <a name="using-parameters-with-adonet-and-ado-connection-managers"></a>Verwenden von Parametern mit ADO.NET- und ADO-Verbindungs-Managern  
 [!INCLUDE[vstecado](../includes/vstecado-md.md)]- und ADO-Verbindungs-Manager besitzen besondere Anforderungen für SQL-Befehle, die Parameter verwenden:  
  
-   [!INCLUDE[vstecado](../includes/vstecado-md.md)]-Verbindungs-Manager erfordern die Verwendung von Parameternamen als Parametermarker in SQL-Befehlen. Das bedeutet, dass Variablen Parametern direkt zugeordnet werden können. Beispielsweise wird die `@varName` -Variable dem Parameter mit der Bezeichnung `@parName` zugeordnet. Auf diese Weise wird dem `@parName`-Parameter ein Wert bereitgestellt.  
  
-   ADO-Verbindungs-Manager erfordern die Verwendung von Fragezeichen ("?") als Parametermarker in SQL-Befehlen. Sie können jedoch einen beliebigen benutzerdefinierten Namen, mit Ausnahme von ganzzahligen Werten, als Parameternamen verwenden.  
  
 Variablen werden Parameternamen zugeordnet, um Parametern Werte bereitzustellen. Anschließend verwendet der Task „SQL ausführen“ den Ordinalwert des Parameternamens in der Parameterliste, um die Variablenwerte in Parametern zu laden.  
  
### <a name="using-parameters-with-excel-odbc-and-ole-db-connection-managers"></a>Verwenden von Parametern mit EXCEL-, ODBC- und OLE DB-Verbindungs-Managern  
 EXCEL-, ODBC- und OLE DB-Verbindungs-Manager erfordern die Verwendung von Fragezeichen ("?") als Parametermarkierungen in SQL-Befehlen sowie die Verwendung 0-basierter bzw. 1-basierter numerischer Werte als Parameternamen. Wenn der Task „SQL ausführen“ den ODBC-Verbindungs-Manager verwendet, wird der Parametername, der dem ersten Parameter in der Abfrage zugeordnet wird, mit 1 bezeichnet, andernfalls wird er mit 0 bezeichnet. Für nachfolgende Parameter gibt der numerische Wert des Parameternamens den Parameter in dem SQL-Befehl an, dem der Parametername zugeordnet wird. Beispielsweise wird der Parametername mit der Bezeichnung "3" dem dritten Parameter zugeordnet, der im SQL-Befehl durch das dritte Fragezeichen ("?") dargestellt wird.  
  
 Um Werte für Parameter bereitzustellen, werden den Parameternamen Variablen zugeordnet. Der Task SQL ausführen verwendet dann den Ordinalwert des Parameternamens, um die Variablenwerte in Parametern zu laden.  
  
 Einige OLE DB-Datentypen werden, abhängig vom Anbieter, den der Verbindungs-Manager verwendet, nicht unterstützt. Beispielsweise erkennt der Excel-Treiber nur einen begrenzten Satz von Datentypen. Weitere Informationen zum Verhalten des Jet-Anbieters mit dem Excel-Treiber finden Sie unter [Excel Source](data-flow/excel-source.md).  
  
#### <a name="using-parameters-with-ole-db-connection-managers"></a>Verwenden von Parametern mit OLE DB-Verbindungs-Managern  
 Wenn der Task „SQL ausführen“ den OLE DB-Verbindungs-Manager verwendet, ist die BypassPrepare-Eigenschaft des Tasks verfügbar. Legen Sie diese Eigenschaft auf `true` , wenn der Task SQL ausführen SQL-Anweisungen mit Parametern verwendet.  
  
 Bei Verwendung eines OLE DB-Verbindungs-Managers können Sie keine parametrisierten Unterabfragen verwenden, da der Task „SQL ausführen“ keine Parameterinformationen über den OLE DB-Anbieter ableiten kann. Sie können jedoch einen Ausdruck verwenden, um die Parameterwerte in der Abfragezeichenfolge zu verketten und die SqlStatementSource-Eigenschaft des Tasks festzulegen.  
  
##  <a name="Date_and_time_data_types"></a> Verwenden von Parametern mit Datums- und Zeitdatentypen  
  
### <a name="using-date-and-time-parameters-with-adonet-and-ado-connection-managers"></a>Verwenden von Datums- und Zeitparametern mit ADO.NET- und ADO-Verbindungs-Managern  
 Beim Lesen von Daten von der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Typen `time` und `datetimeoffset`, einen Task SQL ausführen, die entweder verwendet ein [!INCLUDE[vstecado](../includes/vstecado-md.md)] oder ADO-Verbindungs-Manager hat die folgenden zusätzlichen Anforderungen:  
  
-   Für `time` Daten, ein [!INCLUDE[vstecado](../includes/vstecado-md.md)] Verbindungs-Manager erfordert diese Daten in einem Parameter gespeichert werden, dessen Parametertyp `Input` oder `Output`, und mit dem Datentyp `string`.  
  
-   Für `datetimeoffset` Daten, eine [!INCLUDE[vstecado](../includes/vstecado-md.md)] Verbindungs-Manager erfordert diese Daten in einem der folgenden Parameter gespeichert werden:  
  
    -   Ein Parameter mit dem Parametertyp `Input` und dem Datentyp `string`.  
  
    -   Ein Parameter mit dem Parametertyp `Output` oder `ReturnValue`, und mit dem Datentyp `datetimeoffset`, `string`, oder `datetime2`. Wenn Sie einen Parameter auswählen, deren Datentyp entweder ist `string` oder `datetime2`, [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] in String bzw. datetime2 konvertiert.  
  
-   Für einen ADO-Verbindungs-Manager ist es erforderlich, dass `time`-Daten oder `datetimeoffset`-Daten in einem Parameter mit dem Parametertyp `Input` oder `Output` und dem Datentyp `adVarWchar` gespeichert werden.  
  
 Weitere Informationen zu [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Datentypen sowie deren Zuordnung zu [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]-Datentypen finden Sie unter [Datentypen &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql) und [SQL Server Integration Services-Datentypen](data-flow/integration-services-data-types.md).  
  
### <a name="using-date-and-time-parameters-with-ole-db-connection-managers"></a>Verwenden von Datums- und Zeitparametern mit dem OLE DB-Verbindungs-Manager  
 Wenn Sie einen OLE DB-Verbindungs-Manager verwenden, besitzt ein Task SQL ausführen bestimmte speicheranforderungen für Daten aus der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Datentypen `date`, `time`, `datetime`, `datetime2`, und `datetimeoffset`. Sie müssen diese Daten in einem der folgenden Parametertypen speichern:  
  
-   In einem Eingabeparameter mit dem Datentyp NVARCHAR  
  
-   In einem Ausgabeparameter mit dem entsprechenden Datentyp, wie in der folgenden Tabelle aufgeführt  
  
    |Parametertyp `Output`|Date-Datumstyp|  
    |-------------------------------|--------------------|  
    |DBDATE|`date`|  
    |DBTIME2|`time`|  
    |DBTIMESTAMP|`datetime`, `datetime2`|  
    |DBTIMESTAMPOFFSET|`datetimeoffset`|  
  
 Wenn die Daten nicht im entsprechenden Eingabe- oder Ausgabeparameter gespeichert werden, erzeugt das Paket einen Fehler.  
  
### <a name="using-date-and-time-parameters-with-odbc-connection-managers"></a>Verwenden von Datums- und Zeitparametern mit dem ODBC-Verbindungs-Manager  
 Wenn Sie einen ODBC-Verbindungs-Manager verwenden, hat ein Task SQL ausführen bestimmte speicheranforderungen für Daten mit der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Datentypen `date`, `time`, `datetime`, `datetime2`, oder `datetimeoffset`. Sie müssen diese Daten in einem der folgenden Parametertypen speichern:  
  
-   Ein `input`-Parameter mit dem Datentyp SQL_WVARCHAR  
  
-   Ein `output` Parameter mit dem entsprechenden Datentyp, wie in der folgenden Tabelle aufgeführt.  
  
    |Parametertyp `Output`|Date-Datumstyp|  
    |-------------------------------|--------------------|  
    |SQL_DATE|`date`|  
    |SQL_SS_TIME2|`time`|  
    |SQL_TYPE_TIMESTAMP<br /><br /> -oder-<br /><br /> SQL_TIMESTAMP|`datetime`, `datetime2`|  
    |SQL_SS_TIMESTAMPOFFSET|`datetimeoffset`|  
  
 Wenn die Daten nicht im entsprechenden Eingabe- oder Ausgabeparameter gespeichert werden, erzeugt das Paket einen Fehler.  
  
##  <a name="WHERE_clauses"></a> Verwenden von Parametern in WHERE Klauseln  
 In SELECT-, INSERT-, UPDATE- und DELETE-Befehlen sind häufig WHERE-Klauseln enthalten, um Filter anzugeben, die die Bedingungen definieren, die die Zeilen in den Quelltabellen für einen SQL-Befehl erfüllen müssen. Parameter stellen die Filterwerte in den WHERE-Klauseln bereit.  
  
 Sie können Parametermarkierungen verwenden, um Parameterwerte dynamisch bereitzustellen. Die Regeln für die in der SQL-Anweisung zu verwendenden Parametermarkierungen und Parameternamen hängen vom Typ des Verbindungs-Managers ab, den der Task SQL ausführen verwendet.  
  
 In der folgenden Tabelle finden Sie eine Auflistung von Beispielen des SELECT-Befehls nach verschiedenen Verbindungs-Managertypen. Die INSERT-, UPDATE- und DELETE-Anweisungen ähneln sich. In den Beispielen wird die SELECT-Anweisung verwendet, um Produkte aus der **Product** -Tabelle in [!INCLUDE[ssSampleDBUserInputNonLocal](../includes/sssampledbuserinputnonlocal-md.md)] zurückzugeben, die eine **ProductID** aufweisen, die größer oder kleiner als die angegebenen Werte von zwei Parametern ist.  
  
|Verbindungstyp|SELECT-Syntax|  
|---------------------|-------------------|  
|EXCEL, ODBC und OLEDB|`SELECT* FROM Production.Product WHERE ProductId > ? AND ProductID < ?`|  
|ADO|`SELECT* FROM Production.Product WHERE ProductId > ? AND ProductID < ?`|  
|[!INCLUDE[vstecado](../includes/vstecado-md.md)]|`SELECT* FROM Production.Product WHERE ProductId > @parmMinProductID AND ProductID < @parmMaxProductID`|  
  
 In den Beispielen werden Parameter mit den folgenden Namen benötigt:  
  
-   Die EXCEL- und OLED DB-Verbindungs-Manager verwenden die Parameternamen 0 und 1. Der ODBC-Verbindungstyp verwendet die Namen 1 und 2.  
  
-   Der ADO-Verbindungstyp kann zwei beliebige Parameternamen verwenden, wie z. B. Param1 und Param2, deren Zuordnung muss aber nach ihrer Ordnungsposition in der Parameterliste erfolgen.  
  
-   Der [!INCLUDE[vstecado](../includes/vstecado-md.md)]-Verbindungstyp verwendet die Parameternamen @parmMinProductID und @parmMaxProductID.  
  
##  <a name="Stored_procedures"></a> Verwenden von Parametern mit gespeicherten Prozeduren  
 Für SQL-Befehle, die gespeicherte Prozeduren ausführen, kann die Parameterzuordnung ebenfalls verwendet werden. Die Regeln für die zu verwendenden Parametermarkierungen und Parameternamen hängen, wie die Regeln für parametrisierte Abfragen, vom Typ des Verbindungs-Managers ab, den der Task SQL ausführen verwendet.  
  
 In der folgenden Tabelle finden Sie eine Auflistung von Beispielen des EXEC-Befehls nach verschiedenen Verbindungs-Managertypen. Die Beispiele führen die gespeicherte Prozedur **uspGetBillOfMaterials** in [!INCLUDE[ssSampleDBUserInputNonLocal](../includes/sssampledbuserinputnonlocal-md.md)]aus. Die gespeicherte Prozedur verwendet die `@StartProductID` sowie den `@CheckDate`-Parameter und den `input`-Eingabeparameter.  
  
|Verbindungstyp|EXEC-Syntax|  
|---------------------|-----------------|  
|EXCEL und OLEDB|`EXEC uspGetBillOfMaterials ?, ?`|  
|ODBC|`{call uspGetBillOfMaterials(?, ?)}`<br /><br /> Weitere Informationen über die ODBC-Aufrufsyntax finden Sie im Thema [Prozedurparameter](http://go.microsoft.com/fwlink/?LinkId=89462)in der ODBC Programmer's Reference in der MSDN Library.|  
|ADO|Wenn IsQueryStoredProcedure, um festgelegt ist `False`, `EXEC uspGetBillOfMaterials ?, ?`<br /><br /> Wenn IsQueryStoredProcedure, um festgelegt ist `True`, `uspGetBillOfMaterials`|  
|[!INCLUDE[vstecado](../includes/vstecado-md.md)]|Wenn IsQueryStoredProcedure, um festgelegt ist `False`, `EXEC uspGetBillOfMaterials @StartProductID, @CheckDate`<br /><br /> Wenn IsQueryStoredProcedure, um festgelegt ist `True`, `uspGetBillOfMaterials`|  
  
 Um Ausgabeparameter verwenden zu können, erfordert die Syntax die Verwendung des OUTPUT-Schlüsselworts am Ende jeder Parametermarkierung. Zum Beispiel ist die folgende Ausgabeparametersyntax richtig: `EXEC myStoredProcedure ? OUTPUT`.  
  
 Weitere Informationen zum Verwenden von Eingabe- und Ausgabeparametern mit gespeicherten Prozeduren von Transact-SQL finden Sie unter [EXECUTE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/execute-transact-sql).  
  
##  <a name="Return_codes"></a> Abrufen von Werten von Rückgabecodes  
 Eine gespeicherte Prozedur kann einen ganzzahligen Wert zurückgeben, der als Rückgabecode bezeichnet wird, um den Ausführungsstatus einer Prozedur anzuzeigen. Um Rückgabecodes im Task SQL ausführen zu implementieren, verwenden Sie die Parameter des der `ReturnValue` Typ.  
  
 In der folgenden Tabelle finden Sie eine Auflistung einiger Beispiele des EXEC-Befehls nach verschiedenen Verbindungstypen, die Rückgabecodes implementieren. In alle Beispiele wird ein `input`-Parameter verwendet. Die Regeln für die Verwendung von parametermarkierungen und Parameternamen sind für alle Parametertypen identisch –`Input`, `Output`, und `ReturnValue`.  
  
 Ein Teil der Syntax unterstützt keine Parameterliterale. In diesem Fall müssen Sie die Parameterwerte mithilfe einer Variablen bereitstellen.  
  
|Verbindungstyp|EXEC-Syntax|  
|---------------------|-----------------|  
|EXCEL und OLEDB|`EXEC ? = myStoredProcedure 1`|  
|ODBC|`{? = call myStoredProcedure(1)}`<br /><br /> Weitere Informationen über die ODBC-Aufrufsyntax finden Sie im Thema [Prozedurparameter](http://go.microsoft.com/fwlink/?LinkId=89462)in der ODBC Programmer's Reference in der MSDN Library.|  
|ADO|Wenn IsQueryStoreProcedure, um festgelegt ist `False`, `EXEC ? = myStoredProcedure 1`<br /><br /> Wenn IsQueryStoreProcedure, um festgelegt ist `True`, `myStoredProcedure`|  
|[!INCLUDE[vstecado](../includes/vstecado-md.md)]|Set IsQueryStoreProcedure festgelegt ist, um `True`.<br /><br /> `myStoredProcedure`|  
  
 In der in der obigen Tabelle gezeigten Syntax verwendet der Task "SQL ausführen" zum Ausführen der gespeicherten Prozedur den Quelltyp **Direkteingabe** . Der Task "SQL ausführen" kann auch den Quelltyp **Dateiverbindung** verwenden, um eine gespeicherte Prozedur auszuführen. Unabhängig davon, ob der Task SQL ausführen verwendet die **Direkteingabe** oder **Dateiverbindung** Datenquellentyp, mit einem Parameter des der `ReturnValue` Typ implementieren den Rückgabecode. Weitere Informationen zum Konfigurieren des Quelltyps für die vom Task „SQL ausführen“ ausgeführte SQL-Anweisung finden Sie unter [Editor für den Task „SQL ausführen“ &#40;Seite „Allgemein“&#41;](general-page-of-integration-services-designers-options.md).  
  
 Weitere Informationen zum Verwenden von Rückgabecodes mit gespeicherten Prozeduren von Transact-SQL finden Sie unter [RETURN &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/return-transact-sql).  
  
##  <a name="Configure_parameters_and_return_codes"></a> Konfigurieren von Parametern und Rückgabecodes in den Tasks "SQL ausführen"  
 Klicken Sie auf das folgende Thema, um weitere Informationen zu den Eigenschaften von Parametern und Rückgabecodes zu erhalten, die Sie im [!INCLUDE[ssIS](../includes/ssis-md.md)] -Designer festlegen können:  
  
-   [Editor für den Task SQL ausführen &#40;Seite Parameterzuordnung&#41;](../../2014/integration-services/execute-sql-task-editor-parameter-mapping-page.md)  
  
 Klicken Sie auf das folgende Thema, um weitere Informationen zum Festlegen dieser Eigenschaften im [!INCLUDE[ssIS](../includes/ssis-md.md)] -Designer zu erhalten:  
  
-   [Festlegen der Eigenschaften eines Tasks oder Containers](../../2014/integration-services/set-the-properties-of-a-task-or-container.md)  
  
## <a name="related-tasks"></a>Related Tasks  
 [Festlegen der Eigenschaften eines Tasks oder Containers](../../2014/integration-services/set-the-properties-of-a-task-or-container.md)  
  
## <a name="related-content"></a>Verwandte Inhalte  
  
-   Blog-Artikel [Stored procedures with output parameters](http://go.microsoft.com/fwlink/?LinkId=157786)(Gespeicherte Prozeduren mit Ausgabeparametern) unter blogs.msdn.com  
  
-   CodePlex-Beispiel [Execute SQL Parameters and Result Sets](http://go.microsoft.com/fwlink/?LinkId=157863)(Ausführen von SQL-Parametern und Resultsets) auf msftisprodsamples.codeplex.com  
  
## <a name="see-also"></a>Siehe auch  
 [SQL ausführen (Task)](control-flow/execute-sql-task.md)   
 [Resultsets im Task „SQL ausführen“](../../2014/integration-services/result-sets-in-the-execute-sql-task.md)  
  
  
