---
title: Befehlsparameter | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
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
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 544809bfdf8ba6b979c9277668adfbe519246b06
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "43072552"
---
# <a name="command-parameters"></a>Befehlsparameter
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Parameter werden im Befehlstext durch ein Fragezeichen markiert. Zum Beispiel wurde die folgende SQL-Anweisung für einen einzelnen Eingabeparameter markiert:  
  
```  
{call SalesByCategory('Produce', ?)}  
```  
  
 Zur Verbesserung der Leistung durch Verringern des Netzwerkverkehrs, der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter wird nicht automatisch Parameterinformationen, wenn **ICommandWithParameters:: GetParameterInfo** oder  **ICommandPrepare:: Prepare** wird aufgerufen, bevor die Ausführung eines Befehls. Dies bedeutet, dass die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter nicht automatisch unterstützt:  
  
-   Überprüfen der Korrektheit des mit **ICommandWithParameters::SetParameterInfo** angegebenen Datentyps.  
  
-   Zuordnen des in den Accessor-Bindungsinformationen angegebenen DBTYPE zum korrekten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentyp für den Parameter  
  
 Bei Einsatz dieser beiden Methoden können in Anwendungen möglicherweise Fehler oder Genauigkeitsverluste auftreten, wenn Datentypen angegeben werden, die nicht mit dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentyp des Parameters kompatibel sind.  
  
 Um dies zu vermeiden, sollte die Anwendung Folgendes tun:  
  
-   Sicherstellen, dass *pwszDataSourceType* dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentyp für den Parameter entspricht, wenn **ICommandWithParameters::SetParameterInfo** fest codiert wird.  
  
-   Sicherstellen, dass der DBTYPE–Wert, der an den Parameter gebunden wird, vom gleichen Typ wie der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentyp des Parameters ist, wenn ein Accessor fest codiert wird.  
  
-   Aufrufen von **ICommandWithParameters::GetParameterInfo**, damit der Anbieter die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentypen der Parameter während der Laufzeit ermitteln kann. Beachten Sie, dass dies einen zusätzlichen Netzwerkroundtrip zum Server bedingt.  
  
> [!NOTE]  
>  Der Anbieter unterstützt den Aufruf von **ICommandWithParameters::GetParameterInfo** nicht in Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] UPDATE- oder DELETE-Anweisungen, die eine FROM-Klausel enthalten; SQL-Anweisungen, die von einer Unterabfrage mit Parametern abhängen; SQL-Anweisungen, die Parametermarkierungen in beiden Ausdrücken eines Vergleichs oder quantifizierten Prädikats enthalten; oder Abfragen, in denen ein Parameter ein Funktionsparameter ist. Bei der Verarbeitung von Batches von SQL-Anweisungen unterstützt der Anbieter überdies keine Aufrufe von **ICommandWithParameters::GetParameterInfo** für Parametermarkierungen in Anweisungen, die der ersten Anweisung im Batch folgen. Kommentare (/* \*/) sind im Befehl [!INCLUDE[tsql](../../includes/tsql-md.md)] nicht zulässig.  
  
 Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter unterstützt Eingabeparameter in SQL-Anweisungsbefehlen. In prozeduraufrufbefehlen die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter unterstützt die Eingabe-, Ausgabe- und Eingabe-/Ausgabeparameter. Ausgabeparameterwerte werden entweder nach der Ausführung (nur wenn keine Rowsets zurückgegeben werden) oder nach Abschluss der Rowsetverarbeitung durch die Anwendung an die Anwendung zurückgegeben. Um sicherzustellen, dass zurückgegebene Werte gültig sind, verwenden Sie **IMultipleResults**, um den Einsatz von Rowsets zu erzwingen.  
  
 Die Namen der Parameter von gespeicherten Prozeduren müssen nicht in einer DBPARAMBINDINFO-Struktur angegeben werden. Verwenden Sie NULL als Wert für die *PwszName* Member an, dass die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter sollten den Parameternamen ignorieren und nur die Ordinalzahl, die im angegebenen verwenden die *RgParamOrdinals*Mitglied **ICommandWithParameters:: SetParameterInfo**. Wenn der Befehlstext sowohl benannte als auch unbenannte Parameter enthält, dann müssen alle unbenannten Parameter vor den benannten Parametern angegeben werden.  
  
 Wenn Sie der Namen der Parameter einer gespeicherten Prozedur angegeben wird, die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter überprüft den Namen aus, um sicherzustellen, dass er gültig ist. Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter gibt einen Fehler zurück, wenn er vom Consumer einen fehlerhaften Parameternamen erhält.  
  
> [!NOTE]  
>  Unterstützung für verfügbar machen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] XML und benutzerdefinierte Typen (UDT), die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter implementiert eine neue [ISSCommandWithParameters](../../relational-databases/native-client-ole-db-interfaces/isscommandwithparameters-ole-db.md) Schnittstelle.  
  
## <a name="see-also"></a>Siehe auch  
 [Befehle](../../relational-databases/native-client-ole-db-commands/commands.md)  
  
  
