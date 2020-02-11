---
title: Aufrufen einer gespeicherten Prozedur (OLE DB) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- calling stored procedures
- RPC escape sequence
- OLE DB, stored procedures
- parameters [SQL Server Native Client], OLE DB
- ODBC CALL escape sequence
- stored procedures [OLE DB], calling
- SQL Server Native Client OLE DB provider, stored procedures
ms.assetid: 8e5738e5-4bbe-4f34-bd69-0c0633290bdd
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: c30e6ca03f1d1d4c794d01bd594efd88306410e3
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "73759043"
---
# <a name="stored-procedures---calling"></a>Aufrufen von gespeicherte Prozeduren
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Eine gespeicherte Prozedur kann 0 oder mehr Parameter haben. Sie kann auch einen Wert zurückgeben: Wenn Sie den [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client-OLE DB-Anbieter verwenden, können die Parameter für eine gespeicherte Prozedur wie folgt übermittelt werden:  
  
-   Durch Hartcodierung des Datenwerts  
  
-   Durch Verwendung einer Parametermarkierung (?) zum Angeben von Parametern, Binden einer Programmvariablen an die Parametermarkierung und Einfügen des Datenwerts in die Programmvariable  
  
> [!NOTE]  
>  Wenn gespeicherte [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Prozeduren mit benannten Parametern mit OLE DB aufgerufen werden, müssen die Parameternamen mit dem Zeichen „\@“ beginnen. Dies ist eine [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-spezifische Einschränkung. Der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter erzwingt diese Einschränkung strenger als MDAC.  
  
 Damit Parameter unterstützt werden, wird die **ICommandWithParameters**-Schnittstelle auf dem Befehlsobjekt verfügbar gemacht. Wenn die Parameter verwendet werden sollen, beschreibt der Consumer die Parameter zunächst dem Anbieter, indem er die **ICommandWithParameters::SetParameterInfo**-Methode aufruft (oder optional eine Aufrufanweisung vorbereitet, die die **GetParameterInfo**-Methode aufruft). Der Consumer erstellt dann einen Accessor, der die Struktur eines Puffers angibt und Parameterwerte in diesen Puffer einfügt. Schließlich übergibt er das Handle des Accessors und einen Zeiger auf den Puffer an **Execute**. Bei späteren Aufrufen von **Execute** fügt der Consumer neue Parameterwerte in den Puffer ein und ruft **Execute** mit dem Accessorhandle und Pufferzeiger auf.  
  
 Ein Befehl, der eine temporär gespeicherte Prozedur mit Parametern aufruft, muss zunächst **ICommandWithParameters::SetParameterInfo** aufrufen, um die Parameterinformationen zu definieren, bevor der Befehl erfolgreich vorbereitet werden kann. Der Grund dafür ist, dass der interne Name für eine temporär gespeicherte Prozedur anders lautet als der externe Name, der von einem Client verwendet wird. Zudem kann SQLOLEDB die Systemtabellen nicht abfragen, um die Parameterinformationen für eine temporär gespeicherte Prozedur zu ermitteln.  
  
 Der Parameterbindungsprozess umfasst folgende Schritte:  
  
1.  Geben Sie die Parameterinformationen in ein Array aus DBPARAMBINDINFO-Strukturen ein, also den Parameternamen, den anbieterspezifischen Namen für den Datentyp des Parameters oder einen standardmäßigen Datentypennamen usw. Jede Struktur im Array beschreibt einen Parameter. Dieses Array wird dann an die **SetParameterInfo**-Methode übergeben.  
  
2.  Rufen Sie die **ICommandWithParameters::SetParameterInfo**-Methode auf, um dem Anbieter Parameter zu beschreiben. **SetParameterInfo** gibt den systemeigenen Datentyp der einzelnen Parameter an. **SetParameterInfo** -Argumente:  
  
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
 Beim Ausführen einer gespeicherten Prozedur in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]unterstützt [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] der Native Client OLE DB-Anbieter Folgendes:  
  
-   ODBC CALL-Escapesequenz  
  
-   RPC-Escapesequenz (Remote Procedure Call, Remoteprozeduraufruf)  
  
-   
  [!INCLUDE[tsql](../../../includes/tsql-md.md)]EXECUTE-Anweisung  
  
### <a name="odbc-call-escape-sequence"></a>ODBC CALL-Escapesequenz  
 Wenn Sie die Parameterinformationen kennen, rufen Sie die **ICommandWithParameters::SetParameterInfo**-Methode auf, um dem Anbieter die Parameter zu beschreiben. Wenn hingegen die ODBC CALL-Syntax zum Aufrufen einer gespeicherten Prozedur verwendet wird, ruft der Anbieter eine Hilfsfunktion auf, um die Parameterinformationen der gespeicherten Prozedur zu ermitteln.  
  
 Wenn Sie nicht sicher sind, was die Parameterinformationen (Parametermetadaten) betrifft, empfiehlt sich die Verwendung der ODBC CALL-Syntax.  
  
 Die allgemeine Syntax zum Aufrufen einer Prozedur mit der ODBC CALL-Escapesequenz lautet:  
  
 {[**? =**]**aufrufen**_procedure_name_[**(**[*Parameter*] [**,**[*Parameter*]]... **)**]}  
  
 Beispiel:  
  
```  
{call SalesByCategory('Produce', '1995')}  
```  
  
### <a name="rpc-escape-sequence"></a>RPC-Escapesequenz  
 Die RPC-Escapesequenz ist der ODBC CALL-Syntax für den Aufruf einer gespeicherten Prozedur ähnlich. Wenn Sie die Prozedur mehrmals aufrufen müssen, ist die RPC-Escapesequenz von den drei Methoden zum Aufrufen einer gespeicherten Prozedur die leistungsfähigste.  
  
 Wenn die RPC-Escapesequenz zur Ausführung einer gespeicherten Prozedur verwendet wird, ruft der Anbieter keine Hilfsfunktion auf, um die Parameterinformationen zu ermitteln (wie dies bei der ODBC CALL-Syntax der Fall ist). Die RPC-Syntax ist einfacher als die ODBC CALL-Syntax, weshalb der Befehl schneller verarbeitet und die Leistung gesteigert wird. In diesem Fall müssen Sie die Parameterinformationen durch Ausführen von **ICommandWithParameters::SetParameterInfo** bereitstellen.  
  
 Bei der RPC-Escapesequenz ist es erforderlich, einen Rückgabewert zu erhalten. Wenn die gespeicherte Prozedur keinen Wert zurückgibt, gibt der Server standardmäßig 0 (null) zurück. Außerdem können Sie keinen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Cursor für die gespeicherte Prozedur öffnen. Die gespeicherte Prozedur wird implizit vorbereitet, und beim Aufruf von **ICommandPrepare::Prepare** tritt ein Fehler auf. Da es nicht möglich ist, einen RPC-Aufruf vorzubereiten, können keine Spaltenmetadaten abgefragt werden. IColumnsInfo::GetColumnInfo und IColumnsRowset::GetColumnsRowset geben DB_E_NOTPREPARED zurück.  
  
 Wenn Sie alle Parametermetadaten kennen, ist die RPC-Escapesequenz die empfohlene Methode für die Ausführung gespeicherter Prozeduren.  
  
 Es folgt ein Beispiel für eine RPC-Escapesequenz zum Aufrufen einer gespeicherten Prozedur:  
  
```  
{rpc SalesByCategory}  
```  
  
 Eine Beispielanwendung, die eine RPC-Escapesequenz veranschaulicht, finden [Sie unter Ausführen einer gespeicherten Prozedur &#40;mithilfe der RPC-Syntax&#41; und Verarbeiten von Rückgabe Codes und Ausgabeparametern &#40;OLE DB&#41;](../../../relational-databases/native-client-ole-db-how-to/results/execute-stored-procedure-with-rpc-and-process-output.md).  
  
### <a name="transact-sql-execute-statement"></a>'EXECUTE'-Anweisung (Transact-SQL)  
 Die ODBC CALL-Escapesequenz und die RPC-Escapesequenz stellen im Vergleich zur [EXECUTE](../../../t-sql/language-elements/execute-transact-sql.md)-Anweisung die bevorzugten Methoden zum Aufrufen einer gespeicherten Prozedur dar. Der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter verwendet den RPC- [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Mechanismus von, um die Befehls Verarbeitung zu optimieren. Dieses RPC-Protokoll erhöht die Leistung, indem es einen Großteil der Parameterverarbeitung und Anweisungsauswertung auf dem Server überflüssig macht.  
  
 Das folgende Beispiel zeigt die EXECUTE[!INCLUDE[tsql](../../../includes/tsql-md.md)] **-Anweisung (**):  
  
```  
EXECUTE SalesByCategory 'Produce', '1995'  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte Prozeduren](../../../relational-databases/native-client/ole-db/stored-procedures.md)  
  
  
