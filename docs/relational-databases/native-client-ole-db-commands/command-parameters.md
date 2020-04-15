---
title: Befehlsparameter | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- parameters [SQL Server Native Client]
- SQL Server Native Client OLE DB provider, parameters
- SQL Server Native Client OLE DB provider, commands
- parameters [SQL Server Native Client], OLE DB
- commands [OLE DB]
ms.assetid: 072ead49-ebaf-41eb-9a0f-613e9d990f26
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 5db24ee3b68d1a8989200479a3ce4018e63a5177
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304513"
---
# <a name="command-parameters"></a>Befehlsparameter
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Parameter werden im Befehlstext durch ein Fragezeichen markiert. Zum Beispiel wurde die folgende SQL-Anweisung für einen einzelnen Eingabeparameter markiert:  
  
```  
{call SalesByCategory('Produce', ?)}  
```  
  
 Um die Leistung durch Verringern [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] des Netzwerkverkehrs zu verbessern, leitet der native Client-OLE-DB-Anbieter parameterinformationen nicht automatisch ab, es sei **denn, ICommandWithParameters::GetParameterInfo** oder **ICommandPrepare::Prepare** wird aufgerufen, bevor ein Befehl ausgeführt wird. Dies bedeutet, dass der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter nicht automatisch:  
  
-   Überprüfen der Korrektheit des mit **ICommandWithParameters::SetParameterInfo** angegebenen Datentyps.  
  
-   Zuordnen des in den Accessor-Bindungsinformationen angegebenen DBTYPE zum korrekten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentyp für den Parameter  
  
 Bei Einsatz dieser beiden Methoden können in Anwendungen möglicherweise Fehler oder Genauigkeitsverluste auftreten, wenn Datentypen angegeben werden, die nicht mit dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentyp des Parameters kompatibel sind.  
  
 Um dies zu vermeiden, sollte die Anwendung Folgendes tun:  
  
-   Sicherstellen, dass *pwszDataSourceType* dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentyp für den Parameter entspricht, wenn **ICommandWithParameters::SetParameterInfo** fest codiert wird.  
  
-   Sicherstellen, dass der DBTYPE–Wert, der an den Parameter gebunden wird, vom gleichen Typ wie der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentyp des Parameters ist, wenn ein Accessor fest codiert wird.  
  
-   Aufrufen von **ICommandWithParameters::GetParameterInfo**, damit der Anbieter die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentypen der Parameter während der Laufzeit ermitteln kann. Beachten Sie, dass dies einen zusätzlichen Netzwerkroundtrip zum Server bedingt.  
  
> [!NOTE]  
>  Der Anbieter unterstützt den Aufruf von **ICommandWithParameters::GetParameterInfo** nicht in Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] UPDATE- oder DELETE-Anweisungen, die eine FROM-Klausel enthalten; SQL-Anweisungen, die von einer Unterabfrage mit Parametern abhängen; SQL-Anweisungen, die Parametermarkierungen in beiden Ausdrücken eines Vergleichs oder quantifizierten Prädikats enthalten; oder Abfragen, in denen ein Parameter ein Funktionsparameter ist. Bei der Verarbeitung von Batches von SQL-Anweisungen unterstützt der Anbieter überdies keine Aufrufe von **ICommandWithParameters::GetParameterInfo** für Parametermarkierungen in Anweisungen, die der ersten Anweisung im Batch folgen. Kommentare (/* \*/) sind im Befehl [!INCLUDE[tsql](../../includes/tsql-md.md)] nicht zulässig.  
  
 Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native Client-OLE-DB-Anbieter unterstützt Eingabeparameter in SQL-Anweisungsbefehlen. Bei Prozeduraufrufbefehlen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützt der native Client-OLE-DB-Anbieter Eingabe-, Ausgabe- und Eingabe-/Ausgabeparameter. Ausgabeparameterwerte werden entweder nach der Ausführung (nur wenn keine Rowsets zurückgegeben werden) oder nach Abschluss der Rowsetverarbeitung durch die Anwendung an die Anwendung zurückgegeben. Um sicherzustellen, dass zurückgegebene Werte gültig sind, verwenden Sie **IMultipleResults**, um den Einsatz von Rowsets zu erzwingen.  
  
 Die Namen der Parameter von gespeicherten Prozeduren müssen nicht in einer DBPARAMBINDINFO-Struktur angegeben werden. Verwenden Sie NULL für den Wert des *pwszName-Members,* um anzugeben, dass der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native Client-OLE-DB-Anbieter den Parameternamen ignorieren und nur den Ordinal verwenden soll, der im *rgParamOrdinals-Member* von **ICommandWithParameters::SetParameterInfo**angegeben ist. Wenn der Befehlstext sowohl benannte als auch unbenannte Parameter enthält, dann müssen alle unbenannten Parameter vor den benannten Parametern angegeben werden.  
  
 Wenn der Name eines gespeicherten Prozedurparameters angegeben wird, überprüft der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter den Namen, um sicherzustellen, dass er gültig ist. Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native Client-OLE-DB-Anbieter gibt einen Fehler zurück, wenn er einen fehlerhaften Parameternamen vom Consumer empfängt.  
  
> [!NOTE]  
>  Um die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Unterstützung für XML und benutzerdefinierte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Typen (UDT) verfügbar zu machen, implementiert der native Client-OLE-DB-Anbieter eine neue [ISSCommandWithParameters-Schnittstelle.](../../relational-databases/native-client-ole-db-interfaces/isscommandwithparameters-ole-db.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Befehle](../../relational-databases/native-client-ole-db-commands/commands.md)  
  
  
