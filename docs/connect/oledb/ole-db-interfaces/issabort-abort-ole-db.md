---
title: ISSAbort::Abort (OLE DB-Treiber) | Microsoft-Dokumentation
description: Erfahren Sie, wie die ISSAbort::Abort-Methode das aktuelle Rowset und alle mit dem aktuellen Befehl im OLE DB-Treiber für SQL Server verknüpften Stapelbefehle aufhebt.
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
apiname:
- ISSAbort::Abort (OLE DB)
apitype: COM
helpviewer_keywords:
- Abort method
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 18e8c8544c557292bd5a7cc813d809ea0f9cf061
ms.sourcegitcommit: c95f3ef5734dec753de09e07752a5d15884125e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88860077"
---
# <a name="issabortabort-ole-db"></a>ISSAbort::Abort (OLE DB)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Bricht das aktuelle Rowset sowie eventuell mit dem aktuellen Befehl verknüpfte Batchbefehle ab.  
  
Die `ISSAbort`-Schnittstelle, die im OLE DB-Treiber für SQL Server verfügbar gemacht wird, stellt die `ISSAbort::Abort`-Methode bereit. Sie dient dazu, das aktuelle Rowset sowie Befehle abzubrechen, die mit dem Befehl, der das Rowset ursprünglich generiert hat, verknüpft sind und noch nicht ausgeführt wurden.  
  
 `ISSAbort` ist ein OLE DB-Treiber für SQL Server-spezifische Schnittstellen, die bei Verwendung von `QueryInterface` für das `IMultipleResults`-Objekt, das von `ICommand::Execute` oder `IOpenRowset::OpenRowset` zurückgegeben wird, verfügbar sind.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
HRESULT Abort(void);  
```  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn der abgebrochene Befehl eine gespeicherte Prozedur ist, wird die Ausführung der gespeicherten Prozedur (und aller Prozeduren, die diese Prozedur aufgerufen haben) sowie des Befehlsbatches, der den gespeicherten Prozeduraufruf enthielt, ebenfalls beendet. Falls der Server gerade ein Resultset an den Client überträgt, wird die Übertragung beendet. Wenn der Client ein Resultset nicht nutzen möchte, wird `**`ISSAbort::Abort` before releasing the rowset will speed up the rowset release, but if there is an open transaction and XACT_ABORT is ON, the transaction will be rolled back when `ISSAbort::Abort` aufgerufen.  
  
 Sobald `ISSAbort::Abort` „S_OK“ zurückgibt, kann die zugehörige `IMultipleResults`-Schnittstelle nicht mehr verwendet werden und gibt bei allen Methodenaufrufen „DB_E_CANCELED“ zurück (außer bei Methoden, die durch die `IUnknown`-Schnittstelle definiert sind), bis sie wieder freigegeben wird. Falls vor dem `IRowset` -Aufruf ein `IMultipleResults` von `Abort`empfangen wurde, ist dieses ebenfalls nicht mehr verwendbar und gibt bei allen Methodenaufrufen DB_E_CANCELED zurück (außer bei Methoden, die durch die `IUnknown` -Schnittstelle und `IRowset::ReleaseRows`definiert sind), bis es nach einem erfolgreichen Aufruf von `ISSAbort::Abort`wieder freigegeben wird.  
  
> [!NOTE]  
>  Wenn der Serverstatus „XACT_ABORT“ab [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] auf ON festgelegt ist, werden bei Ausführung von `ISSAbort::Abort` alle aktuellen impliziten oder expliziten Transaktionen beendet und ein Rollback ausgeführt, wenn eine Verbindung zu [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]besteht. Frühere Versionen von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] brechen die aktuelle Transaktion nicht ab.  
  
## <a name="arguments"></a>Argumente  
 Keine.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 S_OK  
 Die `ISSAbort::Abort` -Methode gibt S_OK zurück, wenn der Batch abgebrochen wurde, andernfalls DB_E_CANTCANCEL. Wenn der Batch bereits abgebrochen wurde, wird DB_E_CANCELED zurückgegeben.  
  
 DB_E_CANCELED  
 Der Batch wurde bereits abgebrochen.  
  
 DB_E_CANTCANCEL  
 Der Batch wurde nicht abgebrochen.  
  
 E_FAIL  
 Ein anbieterspezifischer Fehler ist aufgetreten. Ausführliche Informationen erhalten Sie über die [ISQLServerErrorInfo](https://docs.microsoft.com/sql/connect/oledb/ole-db-interfaces/isqlservererrorinfo-geterrorinfo-ole-db?view=sql-server-ver15)-Schnittstelle.  
  
 E_UNEXPECTED  
 Die Methode wurde unerwartet aufgerufen. Zum Beispiel ist das Objekt in einem Zombiezustand, da `ISSAbort::Abort` bereits aufgerufen wurde.  
  
 E_OUTOFMEMORY  
 Fehler aufgrund von nicht genügend Arbeitsspeicher.  
  
  
