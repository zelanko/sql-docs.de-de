---
title: ISSAsynchStatus::Abort (OLE DB-Treiber) | Microsoft-Dokumentation
description: Erfahren Sie, wie die ISSAsynchStatus::Abort-Methode einen asynchron ausgeführten Vorgang im OLE DB-Treiber für SQL Server abbricht.
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
apiname:
- ISSAsynchStatus::Abort (OLE DB)
apitype: COM
helpviewer_keywords:
- Abort method
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: cbbef11ae17029500a6910e5b28c121f6312dce2
ms.sourcegitcommit: c95f3ef5734dec753de09e07752a5d15884125e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88862206"
---
# <a name="issasynchstatusabort-ole-db"></a>ISSAsynchStatus::Abort (OLE DB)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Bricht einen asynchron ausgeführten Vorgang ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
HRESULT Abort(  
        HCHAPTER hChapter,  
        DBASYNCHOP eOperation);  
```  
  
## <a name="arguments"></a>Argumente  
 *hChapter*[in]  
 Das Handle des Kapitels, für das der Vorgang abgebrochen werden soll. Wenn das aufgerufene Objekt kein Rowsetobjekt ist oder der Vorgang nicht für ein Kapitel gilt, muss der Aufrufer *hChapter* auf DB_NULL_HCHAPTER festlegen.  
  
 *eOperation*[in]  
 Der Vorgang, der abgebrochen werden soll. Der folgende Wert sollte verwendet werden:  
  
 DBASYNCHOP_OPEN – Die Anforderung zum Abbruch gilt für das asynchrone Öffnen oder Auffüllen eines Rowsets oder für die asynchrone Initialisierung eines Datenquellobjekts.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 S_OK  
 Die Anforderung zum Abbrechen des asynchronen Vorgangs wurde verarbeitet. Dies ist keine Garantie, dass der Vorgang selbst abgebrochen wurde. Um festzustellen, ob der Vorgang abgebrochen wurde, muss der Consumer [ISSAsynchStatus::GetStatus](../../oledb/ole-db-interfaces/issasynchstatus-getstatus-ole-db.md) aufrufen und auf den Wert DB_E_CANCELED prüfen. Dieser Wert wird ggf. jedoch nicht im nächsten Aufruf zurückgegeben.  
  
 DB_E_CANTCANCEL  
 Der asynchrone Vorgang kann nicht abgebrochen werden.  
  
 DB_E_CANCELED  
 Die Anforderung zum Abbrechen des asynchronen Vorgangs wurde während der Benachrichtigungen abgebrochen. Der Vorgang wird immer noch asynchron ausgeführt.  
  
 E_FAIL  
 Es ist ein anbieterspezifischer Fehler aufgetreten.  
  
 E_INVALIDARG  
 Der *hChapter*-Parameter ist nicht DB_NULL_HCHAPTER, oder *eOperation* ist nicht DBASYNCH_OPEN.  
  
 E_UNEXPECTED  
 `ISSAsynchStatus::Abort` wurde für ein Datenquellobjekt aufgerufen, für das `IDBInitialize::Initialize` nicht aufgerufen oder nicht abgeschlossen wurde.  
  
 `ISSAsynchStatus::Abort` wurde für ein Datenquellenobjekt aufgerufen, für das `IDBInitialize::Initialize` aufgerufen wurde, das dann aber vor der Initialisierung abgebrochen wurde oder das Zeitlimit überschritten hat. Das Datenquellobjekt wurde noch nicht initialisiert.  
  
 `ISSAsynchStatus::Abort` wurde für ein Rowset aufgerufen, für das zuvor `ITransaction::Commit` oder `ITransaction::Abort` aufgerufen wurde, und das Rowset blieb nach dem Commit oder Abbruch nicht bestehen und befindet sich in einem Zombiezustand.  
  
 `ISSAsynchStatus::Abort` wurde für ein Rowset aufgerufen, das in seiner Initialisierungsphase asynchron abgebrochen wurde. Das Rowset befindet sich in einem Zombiezustand.  
  
## <a name="remarks"></a>Bemerkungen  
 Durch Abbrechen der Initialisierung eines Rowsets oder eines Datenquellobjekts wird das Rowset bzw. das Datenquellobjekt möglicherweise in einen Zombiezustand versetzt, sodass für alle Methoden außer `IUnknown` -Methoden E_UNEXPECTED zurückgegeben wird. In diesem Fall hat der Consumer nur die Möglichkeit, das Rowset oder das Datenquellobjekt freizugeben.  
  
 Durch Aufrufen von `ISSAsynchStatus::Abort` und Übergeben eines anderen Werts für *eOperation* als DBASYNCHOP_OPEN wird S_OK zurückgegeben. Dieser Wert bedeutet nicht, dass der Vorgang abgeschlossen oder abgebrochen wurde.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Ausführen asynchroner Vorgänge](../../oledb/features/performing-asynchronous-operations.md)  
  
  
