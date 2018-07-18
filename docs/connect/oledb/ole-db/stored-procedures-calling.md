---
title: Aufrufen einer gespeicherten Prozedur (OLE DB) | Microsoft-Dokumentation
description: Aufrufen einer gespeicherten Prozedur (OLE DB)
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- calling stored procedures
- RPC escape sequence
- OLE DB, stored procedures
- parameters [OLE DB Driver for SQL Server], OLE DB
- ODBC CALL escape sequence
- stored procedures [OLE DB], calling
- OLE DB Driver for SQL Server, stored procedures
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: adf1023b7975e788fc460756c0eb6d16f40ba2ef
ms.sourcegitcommit: 5152caf8f4346f8b565742bc1df4e454551d63eb
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/27/2018
ms.locfileid: "37042630"
---
# <a name="stored-procedures---calling"></a>Aufrufen von gespeicherte Prozeduren
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-asdbmi-md](../../../includes/appliesto-ss-asdb-asdw-pdw-asdbmi-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Eine gespeicherte Prozedur kann 0 oder mehr Parameter haben. Sie kann auch einen Wert zurückgeben: Wenn der OLE DB-Treiber für SQL Server verwenden, können Parameter an eine gespeicherte Prozedur übergeben werden, indem:  
  
-   Durch Hartcodierung des Datenwerts  
  
-   Durch Verwendung einer Parametermarkierung (?) zum Angeben von Parametern, Binden einer Programmvariablen an die Parametermarkierung und Einfügen des Datenwerts in die Programmvariable  
  
> [!NOTE]  
>  Wenn gespeicherte [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Prozeduren mit benannten Parametern mit OLE DB aufgerufen werden, müssen die Parameternamen mit dem Zeichen „\@“ beginnen. Dies ist eine [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-spezifische Einschränkung. Der OLE DB-Treiber für SQL Server, erzwingt diese Einschränkung strenger als MDAC.  
  
 Damit Parameter unterstützt werden, wird die **ICommandWithParameters**-Schnittstelle auf dem Befehlsobjekt verfügbar gemacht. Wenn die Parameter verwendet werden sollen, beschreibt der Consumer die Parameter zunächst dem Anbieter, indem er die **ICommandWithParameters::SetParameterInfo**-Methode aufruft (oder optional eine Aufrufanweisung vorbereitet, die die **GetParameterInfo**-Methode aufruft). Der Consumer erstellt dann einen Accessor, der die Struktur eines Puffers angibt und Parameterwerte in diesen Puffer einfügt. Schließlich übergibt er das Handle des Accessors und einen Zeiger auf den Puffer an **Execute**. Bei späteren Aufrufen von **Execute** fügt der Consumer neue Parameterwerte in den Puffer ein und ruft **Execute** mit dem Accessorhandle und Pufferzeiger auf.  
  
 Ein Befehl, der eine temporär gespeicherte Prozedur mit Parametern aufruft, muss zunächst **ICommandWithParameters::SetParameterInfo** aufrufen, um die Parameterinformationen zu definieren, bevor der Befehl erfolgreich vorbereitet werden kann. Der Grund dafür ist, dass der interne Name für eine temporär gespeicherte Prozedur anders lautet als der externe Name, der von einem Client verwendet wird. Zudem kann MSOLEDBSQL die Systemtabellen nicht abfragen, um die Parameterinformationen für eine temporär gespeicherte Prozedur zu ermitteln.  
  
 Der Parameterbindungsprozess umfasst folgende Schritte:  
  
1.  Geben Sie die Parameterinformationen in ein Array aus DBPARAMBINDINFO-Strukturen ein, also den Parameternamen, den anbieterspezifischen Namen für den Datentyp des Parameters oder einen standardmäßigen Datentypennamen usw. Jede Struktur im Array beschreibt einen Parameter. Dieses Array wird dann an die **SetParameterInfo**-Methode übergeben.  
  
2.  Rufen Sie die **ICommandWithParameters::SetParameterInfo**-Methode auf, um dem Anbieter Parameter zu beschreiben. **SetParameterInfo** gibt den nativen Datentyp jedes Parameters an. **SetParameterInfo**-Argumente sind:  
  
    -   Die Anzahl von Parametern, für die Typinformationen festzulegen sind  
  
    -   Ein Array aus Ordnungszahlen von Parametern, für die Typinformationen festzulegen sind  
  
    -   Ein Array aus DBPARAMBINDINFO-Strukturen  
  
3.  Erstellen Sie mit dem Befehl **IAccessor::CreateAccessor** einen Parameteraccessor. Der Accessor gibt die Struktur eines Puffers an und fügt Parameterwerte in den Puffer ein. Der Befehl **CreateAccessor** erstellt aus mehreren Bindungen einen Accessor. Diese Bindungen werden vom Consumer mithilfe eines Arrays aus DBBINDING-Strukturen beschrieben. Jede Bindung ordnet dem Puffer des Consumers einen einzelnen Parameter zu und enthält Informationen wie z. B.:  
  
    -   Die Ordnungszahl des Parameters, auf den sich die Bindung bezieht  
  
    -   Die Angabe, was gebunden wird (der Datenwert, seine Länge und sein Status)  
  
    -   Den Offset im Puffer zu jedem dieser Teile  
  
    -   Die Länge und den Typ des Datenwerts, wie er im Puffer des Consumers vorhanden ist  
  
     Ein Accessor wird von seinem Handle identifiziert, das den Typ HACCESSOR aufweist. Dieses Handle wird von der **CreateAccessor**-Methode zurückgegeben. Sobald der Consumer einen Accessor nicht mehr benötigt, muss er die **ReleaseAccessor**-Methode aufrufen, um den belegten Arbeitsspeicher freizugeben.  
  
     Wenn der Consumer eine Methode wie z.B. **ICommand::Execute** aufruft, übergibt er das Handle an einen Accessor und einen Zeiger auf den Puffer selbst. Der Anbieter verwendet diesen Accessor, um zu bestimmen, wie die im Puffer enthaltenen Daten übertragen werden.  
  
4.  Geben Sie die DBPARAMS-Struktur ein. Die Consumervariablen, von denen Eingabeparameterwerte übernommen und in die Ausgabeparameterwerte geschrieben werden, werden zur Laufzeit an **ICommand::Execute** in der DBPARAMS-Struktur übergeben. Die DBPARAMS-Struktur beinhaltet drei Elemente:  
  
    -   Einen Zeiger auf den Puffer, aus dem der Anbieter Eingabeparameterdaten abruft und in den der Anbieter Ausgabeparameterdaten zurückgibt, gemäß den vom Accessorhandle angegebenen Bindungen  
  
    -   Die Anzahl von Parametersätzen im Puffer  
  
    -   Das in Schritt 3 erstellte Accessorhandle  
  
5.  Führen Sie den Befehl mit **ICommand::Execute** aus.  
  
## <a name="methods-of-calling-a-stored-procedure"></a>Methoden zum Aufrufen einer gespeicherten Prozedur  
 Beim Ausführen einer gespeicherten Prozedur in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], der OLE DB-Treiber für SQL Server unterstützt die:  
  
-   ODBC CALL-Escapesequenz  
  
-   RPC-Escapesequenz (Remote Procedure Call, Remoteprozeduraufruf)  
  
-   [!INCLUDE[tsql](../../../includes/tsql-md.md)]EXECUTE-Anweisung  
  
### <a name="odbc-call-escape-sequence"></a>ODBC CALL-Escapesequenz  
 Wenn Sie die Parameterinformationen kennen, rufen Sie die **ICommandWithParameters::SetParameterInfo**-Methode auf, um dem Anbieter die Parameter zu beschreiben. Wenn hingegen die ODBC CALL-Syntax zum Aufrufen einer gespeicherten Prozedur verwendet wird, ruft der Anbieter eine Hilfsfunktion auf, um die Parameterinformationen der gespeicherten Prozedur zu ermitteln.  
  
 Wenn Sie nicht sicher sind, was die Parameterinformationen (Parametermetadaten) betrifft, empfiehlt sich die Verwendung der ODBC CALL-Syntax.  
  
 Die allgemeine Syntax zum Aufrufen einer Prozedur mit der ODBC CALL-Escapesequenz lautet:  
  
 {[**? =**]**Aufruf ***Procedure_name*[**(**[*Parameter*] [**,**[*Parameter*]]...** )**]}  
  
 Zum Beispiel:  
  
```  
{call SalesByCategory('Produce', '1995')}  
```  
  
### <a name="rpc-escape-sequence"></a>RPC-Escapesequenz  
 Die RPC-Escapesequenz ist der ODBC CALL-Syntax für den Aufruf einer gespeicherten Prozedur ähnlich. Wenn Sie die Prozedur mehrmals aufrufen müssen, ist die RPC-Escapesequenz von den drei Methoden zum Aufrufen einer gespeicherten Prozedur die leistungsfähigste.  
  
 Wenn die RPC-Escapesequenz zur Ausführung einer gespeicherten Prozedur verwendet wird, ruft der Anbieter keine Hilfsfunktion auf, um die Parameterinformationen zu ermitteln (wie dies bei der ODBC CALL-Syntax der Fall ist). Die RPC-Syntax ist einfacher als die ODBC CALL-Syntax, weshalb der Befehl schneller verarbeitet und die Leistung gesteigert wird. In diesem Fall müssen Sie die Parameterinformationen durch Ausführen von **ICommandWithParameters::SetParameterInfo** bereitstellen.  
  
 Bei der RPC-Escapesequenz ist es erforderlich, einen Rückgabewert zu erhalten. Wenn die gespeicherte Prozedur keinen Wert zurückgibt, gibt der Server standardmäßig 0 (null) zurück. Außerdem können Sie keinen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Cursor für die gespeicherte Prozedur öffnen. Die gespeicherte Prozedur wird implizit vorbereitet, und beim Aufruf von **ICommandPrepare::Prepare** tritt ein Fehler auf. Aufgrund von nicht um ein RPC-Aufruf vorzubereiten können Sie keine Spaltenmetadaten Abfragen; IColumnsInfo:: GetColumnInfo und IColumnsRowset:: GetColumnsRowset geben db_e_notprepared zurück zurück.  
  
 Wenn Sie alle Parametermetadaten kennen, ist die RPC-Escapesequenz die empfohlene Methode für die Ausführung gespeicherter Prozeduren.  
  
 Es folgt ein Beispiel für eine RPC-Escapesequenz zum Aufrufen einer gespeicherten Prozedur:  
  
```  
{rpc SalesByCategory}  
```  
  
 Eine beispielanwendung, die eine RPC-Escapesequenz veranschaulicht, finden Sie unter [Ausführen einer gespeicherten Prozedur &#40;mithilfe der RPC-Syntax&#41; und Prozess-Rückgabecodes und Ausgabeparametern &#40;OLE DB&#41;](../../oledb/ole-db-how-to/results/execute-stored-procedure-with-rpc-and-process-output.md).  
  
### <a name="transact-sql-execute-statement"></a>'EXECUTE'-Anweisung (Transact-SQL)  
 Die ODBC CALL-Escapesequenz und die RPC-Escapesequenz stellen im Vergleich zur [EXECUTE](../../../t-sql/language-elements/execute-transact-sql.md)-Anweisung die bevorzugten Methoden zum Aufrufen einer gespeicherten Prozedur dar. Der OLE DB-Treiber für SQL Server verwendet den RPC-Mechanismus [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] befehlsverarbeitung zu optimieren. Dieses RPC-Protokoll erhöht die Leistung, indem es einen Großteil der Parameterverarbeitung und Anweisungsauswertung auf dem Server überflüssig macht.  
  
 Das folgende Beispiel zeigt die **EXECUTE**-Anweisung ([!INCLUDE[tsql](../../../includes/tsql-md.md)]):  
  
```  
EXECUTE SalesByCategory 'Produce', '1995'  
```  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Gespeicherte Prozeduren](../../oledb/ole-db/stored-procedures.md)  
  
  
