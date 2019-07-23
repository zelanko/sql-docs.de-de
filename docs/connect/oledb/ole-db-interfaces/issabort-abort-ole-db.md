---
title: 'ISSAbort:: Abort (OLE DB) | Microsoft-Dokumentation'
description: ISSAbort::Abort (OLE DB)
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
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 72ce7fa29adfb349fab8c9e60872740c94484108
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67994385"
---
# <a name="issabortabort-ole-db"></a>ISSAbort::Abort (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Bricht das aktuelle Rowset sowie eventuell mit dem aktuellen Befehl verknüpfte Batchbefehle ab.  
  
Die **ISSAbort**-Schnittstelle, die im OLE DB-Treiber für SQL Server verfügbar gemacht wird, stellt die **ISSAbort::Abort**-Methode bereit. Sie dient dazu, das aktuelle Rowset sowie Befehle abzubrechen, die mit dem Befehl, der das Rowset ursprünglich generiert hat, verknüpft sind und noch nicht ausgeführt wurden.  
  
 **ISSAbort** ist ein OLE DB-Treiber für SQL Server-spezifische Schnittstellen, die bei Verwendung von **QueryInterface** für das **IMultipleResults**-Objekt, das von **ICommand::Execute** oder **IOpenRowset::OpenRowset** zurückgegeben wird, verfügbar sind.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
HRESULT Abort(void);  
```  
  
## <a name="remarks"></a>Remarks  
 Wenn der abgebrochene Befehl eine gespeicherte Prozedur ist, wird die Ausführung der gespeicherten Prozedur (und aller Prozeduren, die diese Prozedur aufgerufen haben) sowie des Befehlsbatches, der den gespeicherten Prozeduraufruf enthielt, ebenfalls beendet. Falls der Server gerade ein Resultset an den Client überträgt, wird die Übertragung beendet. Wenn der Client ein Resultset nicht verarbeitet, wird durch Aufrufen von **ISSAbort::Abort** vor dem Freigeben des Rowsets die Rowsetfreigabe beschleunigt, aber wenn eine offene Transaktion vorhanden ist und XACT_ABORT auf ON gestellt ist, wird beim Aufrufen von **ISSAbort::Abort** ein Rollback für die Transaktion ausgeführt.  
  
 Sobald **ISSAbort::Abort** „S_OK“ zurückgibt, kann die zugehörige **IMultipleResults**-Schnittstelle nicht mehr verwendet werden und gibt bei allen Methodenaufrufen „DB_E_CANCELED“ zurück (außer bei Methoden, die durch die **IUnknown**-Schnittstelle definiert sind), bis sie wieder freigegeben wird. Falls vor dem **Abort** -Aufruf ein **IRowset** von **IMultipleResults**empfangen wurde, ist dieses ebenfalls nicht mehr verwendbar und gibt bei allen Methodenaufrufen DB_E_CANCELED zurück (außer bei Methoden, die durch die **IUnknown** -Schnittstelle und **IRowset::ReleaseRows**definiert sind), bis es nach einem erfolgreichen Aufruf von **ISSAbort::Abort**wieder freigegeben wird.  
  
> [!NOTE]  
>  Ab [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]gilt: Wenn der Serverstatus XACT_ABORT ON ist, werden bei Ausführung von **ISSAbort::Abort** alle aktuellen impliziten oder expliziten Transaktionen beendet und ein Rollback ausgeführt, wenn eine Verbindung zu [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]besteht. Frühere Versionen von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] brechen die aktuelle Transaktion nicht ab.  
  
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
 Ein anwenderspezifischer Fehler ist aufgetreten. Ausführlichere Informationen erhalten Sie über die [ISQLServerErrorInfo](https://msdn.microsoft.com/library/a8323b5c-686a-4235-a8d2-bda43617b3a1) -Schnittstelle.  
  
 E_UNEXPECTED  
 Die Methode wurde unerwartet aufgerufen. Zum Beispiel ist das Objekt in einem Zombiezustand, da **ISSAbort::Abort** bereits aufgerufen wurde.  
  
 E_OUTOFMEMORY  
 Fehler aufgrund von nicht genügend Arbeitsspeicher.  
  
  
