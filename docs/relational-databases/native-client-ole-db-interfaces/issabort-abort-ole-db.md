---
description: 'ISSAbort:: Abort (Native Client OLE DB-Anbieter)'
title: 'ISSAbort:: Abort (Native Client OLE DB-Anbieter) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apiname:
- ISSAbort::Abort (OLE DB)
apitype: COM
helpviewer_keywords:
- Abort method
ms.assetid: a5bca169-694b-4895-84ac-e8fba491e479
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 16e72e33c4ddd618ab9753cb13e1073d9defe365
ms.sourcegitcommit: 7eb80038c86acfef1d8e7bfd5f4e30e94aed3a75
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2020
ms.locfileid: "92081579"
---
# <a name="issabortabort-native-client-ole-db-provider"></a>ISSAbort:: Abort (Native Client OLE DB-Anbieter)
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Bricht das aktuelle Rowset sowie eventuell mit dem aktuellen Befehl verknüpfte Batchbefehle ab.  
  
Die **ISSAbort** -Schnittstelle, die im [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter verfügbar gemacht wird, stellt die **ISSAbort::Abort** -Methode bereit. Sie dient dazu, das aktuelle Rowset sowie Befehle abzubrechen, die mit dem Befehl, der das Rowset ursprünglich generierte, verknüpft sind und noch nicht ausgeführt wurden.  
  
 **ISSAbort** ist eine für den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-Anbieter spezifische Schnittstelle, die bei Verwendung von **QueryInterface** für das **IMultipleResults** -Objekt, das von **ICommand::Execute** oder **IOpenRowset::OpenRowset**zurückgegeben wird, verfügbar ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
HRESULT Abort(void);  
```  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn der abgebrochene Befehl eine gespeicherte Prozedur ist, wird die Ausführung der gespeicherten Prozedur (und aller Prozeduren, die diese Prozedur aufgerufen haben) sowie der Befehls Batch, der den Aufruf der gespeicherten Prozedur enthält, ebenfalls beendet. Falls der Server gerade ein Resultset an den Client überträgt, wird dieses gestoppt. Wenn der Client ein Resultset nicht verarbeitet, wird durch Aufrufen von **ISSAbort::Abort** vor dem Freigeben des Rowsets die Rowsetfreigabe beschleunigt, aber wenn eine offene Transaktion vorhanden ist und XACT_ABORT auf ON gestellt ist, wird beim Aufrufen von **ISSAbort::Abort** ein Rollback für die Transaktion ausgeführt.  
  
 Sobald **ISSAbort::Abort** „S_OK“ zurückgibt, kann die zugehörige **IMultipleResults**-Schnittstelle nicht mehr verwendet werden und gibt bei allen Methodenaufrufen „DB_E_CANCELED“ zurück (außer bei Methoden, die durch die **IUnknown**-Schnittstelle definiert sind), bis sie wieder freigegeben wird. Falls vor dem **Abort** -Aufruf ein **IRowset** von **IMultipleResults**empfangen wurde, ist dieses ebenfalls nicht mehr verwendbar und gibt bei allen Methodenaufrufen DB_E_CANCELED zurück (außer bei Methoden, die durch die **IUnknown** -Schnittstelle und **IRowset::ReleaseRows**definiert sind), bis es nach einem erfolgreichen Aufruf von **ISSAbort::Abort**wieder freigegeben wird.  
  
> [!NOTE]  
>  Wenn der Serverstatus „XACT_ABORT“ab [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] auf ON festgelegt ist, werden bei Ausführung von **ISSAbort::Abort** alle aktuellen impliziten oder expliziten Transaktionen beendet und ein Rollback ausgeführt, wenn eine Verbindung zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]besteht. Frühere Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] brechen die aktuelle Transaktion nicht ab.  
  
## <a name="arguments"></a>Argumente  
 Keine.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 S_OK  
 Die **ISSAbort::Abort** -Methode gibt S_OK zurück, wenn der Batch abgebrochen wurde, andernfalls DB_E_CANTCANCEL. Wenn der Batch bereits abgebrochen wurde, wird DB_E_CANCELED zurückgegeben.  
  
 DB_E_CANCELED  
 Der Batch wurde bereits abgebrochen.  
  
 DB_E_CANTCANCEL  
 Der Batch wurde nicht abgebrochen.  
  
 E_FAIL  
 Ein anbieterspezifischer Fehler ist aufgetreten. Ausführliche Informationen erhalten Sie über die [ISQLServerErrorInfo](isqlservererrorinfo-geterrorinfo-ole-db.md)-Schnittstelle.  
  
 E_UNEXPECTED  
 Die Methode wurde unerwartet aufgerufen. Zum Beispiel ist das Objekt in einem Zombiezustand, da **ISSAbort::Abort** bereits aufgerufen wurde.  
  
 E_OUTOFMEMORY  
 Fehler aufgrund von nicht genügend Arbeitsspeicher.  
  
## <a name="see-also"></a>Weitere Informationen  
 [ISSAbort &#40;OLE DB&#41;]()  
  
