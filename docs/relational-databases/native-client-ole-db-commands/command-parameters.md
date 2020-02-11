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
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 6a0fe1fa812f42ad29b6cc9780acd896ff44bc8a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "73758292"
---
# <a name="command-parameters"></a>Befehlsparameter
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Parameter werden im Befehlstext durch ein Fragezeichen markiert. Zum Beispiel wurde die folgende SQL-Anweisung für einen einzelnen Eingabeparameter markiert:  
  
```  
{call SalesByCategory('Produce', ?)}  
```  
  
 Um die Leistung durch das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] reduzieren des Netzwerk Datenverkehrs zu verbessern, werden Parameterinformationen vom Native Client OLE DB-Anbieter nicht automatisch abgeleitet, es sei denn, dass **ICommandWithParameters:: GetParameterInfo** oder **ICommandPrepare::P repare** vor dem Ausführen eines Befehls aufgerufen wird. Dies bedeutet, dass [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] der Native Client OLE DB-Anbieter nicht automatisch folgende Aktionen durchführt:  
  
-   Überprüfen der Korrektheit des mit **ICommandWithParameters::SetParameterInfo** angegebenen Datentyps.  
  
-   Zuordnen des in den Accessor-Bindungsinformationen angegebenen DBTYPE zum korrekten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentyp für den Parameter  
  
 Bei Einsatz dieser beiden Methoden können in Anwendungen möglicherweise Fehler oder Genauigkeitsverluste auftreten, wenn Datentypen angegeben werden, die nicht mit dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentyp des Parameters kompatibel sind.  
  
 Um dies zu vermeiden, sollte die Anwendung Folgendes tun:  
  
-   Sicherstellen, dass *pwszDataSourceType* dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentyp für den Parameter entspricht, wenn **ICommandWithParameters::SetParameterInfo** fest codiert wird.  
  
-   Sicherstellen, dass der DBTYPE–Wert, der an den Parameter gebunden wird, vom gleichen Typ wie der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentyp des Parameters ist, wenn ein Accessor fest codiert wird.  
  
-   Aufrufen von **ICommandWithParameters::GetParameterInfo**, damit der Anbieter die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentypen der Parameter während der Laufzeit ermitteln kann. Beachten Sie, dass dies einen zusätzlichen Netzwerkroundtrip zum Server bedingt.  
  
> [!NOTE]  
>  Der Anbieter unterstützt den Aufruf von **ICommandWithParameters::GetParameterInfo** nicht in Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] UPDATE- oder DELETE-Anweisungen, die eine FROM-Klausel enthalten; SQL-Anweisungen, die von einer Unterabfrage mit Parametern abhängen; SQL-Anweisungen, die Parametermarkierungen in beiden Ausdrücken eines Vergleichs oder quantifizierten Prädikats enthalten; oder Abfragen, in denen ein Parameter ein Funktionsparameter ist. Bei der Verarbeitung von Batches von SQL-Anweisungen unterstützt der Anbieter überdies keine Aufrufe von **ICommandWithParameters::GetParameterInfo** für Parametermarkierungen in Anweisungen, die der ersten Anweisung im Batch folgen. Kommentare (/* \*/) sind im Befehl [!INCLUDE[tsql](../../includes/tsql-md.md)] nicht zulässig.  
  
 Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter unterstützt Eingabeparameter in SQL-Anweisungs Befehlen. Bei Prozedur aufrufbefehlen unterstützt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] der Native Client OLE DB-Anbieter Eingabe-, Ausgabe-und Eingabe-/Ausgabeparameter. Ausgabeparameterwerte werden entweder nach der Ausführung (nur wenn keine Rowsets zurückgegeben werden) oder nach Abschluss der Rowsetverarbeitung durch die Anwendung an die Anwendung zurückgegeben. Um sicherzustellen, dass zurückgegebene Werte gültig sind, verwenden Sie **IMultipleResults**, um den Einsatz von Rowsets zu erzwingen.  
  
 Die Namen der Parameter von gespeicherten Prozeduren müssen nicht in einer DBPARAMBINDINFO-Struktur angegeben werden. Verwenden Sie für den Wert des *pwszName* -Members NULL, um anzugeben [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , dass der Native Client OLE DB-Anbieter den Parameternamen ignorieren und nur die Ordinalzahl verwenden soll, die im *rgParamOrdinals* -Member von **ICommandWithParameters:: SetParameterInfo**angegeben ist. Wenn der Befehlstext sowohl benannte als auch unbenannte Parameter enthält, dann müssen alle unbenannten Parameter vor den benannten Parametern angegeben werden.  
  
 Wenn der Name eines Parameters für eine gespeicherte Prozedur angegeben wird [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , überprüft der Native Client OLE DB-Anbieter den Namen, um sicherzustellen, dass er gültig ist. Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter gibt einen Fehler zurück, wenn er vom Consumer einen fehlerhaften Parameternamen empfängt.  
  
> [!NOTE]  
>  Um Unterstützung für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] XML und benutzerdefinierte Typen (User-Defined Types, UDT) verfügbar zu machen, implementiert der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter eine neue [ISSCommandWithParameters](../../relational-databases/native-client-ole-db-interfaces/isscommandwithparameters-ole-db.md) -Schnittstelle.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Befehle](../../relational-databases/native-client-ole-db-commands/commands.md)  
  
  
