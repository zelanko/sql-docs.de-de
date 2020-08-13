---
title: Befehlsparameter (OLE DB-Treiber) | Microsoft-Dokumentation
description: Befehlsparameter
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- parameters [OLE DB Driver for SQL Server]
- OLE DB Driver for SQL Server, parameters
- OLE DB Driver for SQL Server, commands
- parameters [OLE DB Driver for SQL Server], OLE DB
- commands [OLE DB]
author: pmasl
ms.author: pelopes
ms.openlocfilehash: d5538e11a121a61b4e5c93175bdecbf31be27127
ms.sourcegitcommit: 591bbf4c7e4e2092f8abda6a2ffed263cb61c585
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/22/2020
ms.locfileid: "86942772"
---
# <a name="command-parameters"></a>Befehlsparameter
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Parameter werden im Befehlstext durch ein Fragezeichen markiert. Zum Beispiel wurde die folgende SQL-Anweisung für einen einzelnen Eingabeparameter markiert:  
  
```  
{call SalesByCategory('Produce', ?)}  
```  
  
 Um die Leistung durch eine Reduzierung des Netzwerkverkehrs zu verbessern, leitet der OLE DB-Treiber für SQL Server nicht automatisch Parameterinformationen ab, sondern nur dann, wenn vor der Befehlsausführung **ICommandWithParameters::GetParameterInfo** oder **ICommandPrepare::Prepare** aufgerufen wird. Dies bedeutet, dass der OLE DB Treiber für SQL Server folgende Vorgänge nicht automatisch ausführt:  
  
-   Überprüfen der Korrektheit des mit **ICommandWithParameters::SetParameterInfo** angegebenen Datentyps.  
  
-   Zuordnen des in den Accessor-Bindungsinformationen angegebenen DBTYPE zum korrekten [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Datentyp für den Parameter  
  
 Bei Einsatz dieser beiden Methoden können in Anwendungen möglicherweise Fehler oder Genauigkeitsverluste auftreten, wenn Datentypen angegeben werden, die nicht mit dem [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Datentyp des Parameters kompatibel sind.  
  
 Um dies zu vermeiden, sollte die Anwendung Folgendes tun:  
  
-   Sicherstellen, dass *pwszDataSourceType* dem [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Datentyp für den Parameter entspricht, wenn **ICommandWithParameters::SetParameterInfo** fest codiert wird.  
  
-   Sicherstellen, dass der DBTYPE–Wert, der an den Parameter gebunden wird, vom gleichen Typ wie der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Datentyp des Parameters ist, wenn ein Accessor fest codiert wird.  
  
-   Aufrufen von **ICommandWithParameters::GetParameterInfo**, damit der Anbieter die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Datentypen der Parameter während der Laufzeit ermitteln kann. Beachten Sie, dass dies einen zusätzlichen Netzwerkroundtrip zum Server bedingt.  
  
> [!NOTE]  
>  Der Anbieter unterstützt den Aufruf von **ICommandWithParameters::GetParameterInfo** nicht in Verbindung mit [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] UPDATE- oder DELETE-Anweisungen, die eine FROM-Klausel enthalten; SQL-Anweisungen, die von einer Unterabfrage mit Parametern abhängen; SQL-Anweisungen, die Parametermarkierungen in beiden Ausdrücken eines Vergleichs oder quantifizierten Prädikats enthalten; oder Abfragen, in denen ein Parameter ein Funktionsparameter ist. Bei der Verarbeitung von Batches von SQL-Anweisungen unterstützt der Anbieter überdies keine Aufrufe von **ICommandWithParameters::GetParameterInfo** für Parametermarkierungen in Anweisungen, die der ersten Anweisung im Batch folgen. Kommentare (/* \*/) sind im Befehl [!INCLUDE[tsql](../../../includes/tsql-md.md)] nicht zulässig.  
  
 Der OLE DB-Treiber für SQL Server unterstützt Eingabeparameter in SQL-Anweisungsbefehlen. In Prozeduraufrufbefehlen unterstützt der OLE DB-Treiber für SQL Server Eingabe-, Ausgabe- und Eingabe/Ausgabe-Parameter. Ausgabeparameterwerte werden entweder nach der Ausführung (nur wenn keine Rowsets zurückgegeben werden) oder nach Abschluss der Rowsetverarbeitung durch die Anwendung an die Anwendung zurückgegeben. Um sicherzustellen, dass zurückgegebene Werte gültig sind, verwenden Sie **IMultipleResults**, um den Einsatz von Rowsets zu erzwingen.  
  
 Die Namen der Parameter von gespeicherten Prozeduren müssen nicht in einer DBPARAMBINDINFO-Struktur angegeben werden. Geben Sie durch die Angabe von NULL als Wert für das Element *pwszName* an, dass der OLE DB-Treiber für SQL Server den Parameternamen ignorieren und nur die Ordinalzahl verwenden soll, die im Element *rgParamOrdinals* von **ICommandWithParameters::SetParameterInfo** angegeben wurde. Wenn der Befehlstext sowohl benannte als auch unbenannte Parameter enthält, dann müssen alle unbenannten Parameter vor den benannten Parametern angegeben werden.  
  
 Wenn der Name eines Parameters einer gespeicherten Prozedur angegeben wird, dann überprüft der OLE DB-Treiber für SQL Server den Namen, um seine Gültigkeit sicherzustellen. Der OLE DB-Treiber für SQL Server gibt einen Fehler zurück, wenn er vom Consumer einen fehlerhaften Parameternamen erhält.  
  
> [!NOTE]  
>  Um Unterstützung für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] XML-Typen und benutzerdefinierte Typen (UDT) verfügbar zu machen, implementiert der OLE DB-Treiber für SQL Server eine neue [ISSCommandWithParameters](../../oledb/ole-db-interfaces/isscommandwithparameters-ole-db.md)-Schnittstelle.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Befehle](../../oledb/ole-db-commands/commands.md)  
  
  
