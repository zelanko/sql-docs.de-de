---
title: 'Issasynchstatus:: Abort (OLE DB) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- ISSAsynchStatus::Abort (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- Abort method
ms.assetid: 2a4bd312-839a-45a8-a299-fc8609be9a2a
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3d161786019750aae9740ce42ab0a15464b0dfc2
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48160870"
---
# <a name="issasynchstatusabort-ole-db"></a>ISSAsynchStatus::Abort (OLE DB)
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
 Der Vorgang, der abgebrochen werden soll. Dieser sollte den folgenden Wert haben:  
  
 DBASYNCHOP_OPEN – Die Anforderung zum Abbruch gilt für das asynchrone Öffnen oder Auffüllen eines Rowsets oder für die asynchrone Initialisierung eines Datenquellobjekts.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 S_OK  
 Die Anforderung zum Abbrechen des asynchronen Vorgangs wurde verarbeitet. Dies ist keine Garantie, dass der Vorgang selbst abgebrochen wurde. Um festzustellen, ob der Vorgang abgebrochen wurde, sollte der Consumer [ISSAsynchStatus::GetStatus](issasynchstatus-getstatus-ole-db.md) aufrufen und auf den Wert DB_E_CANCELED prüfen. Dieser Wert wird unter Umständen jedoch nicht gleich im nächsten Aufruf zurückgegeben.  
  
 DB_E_CANTCANCEL  
 Der asynchrone Vorgang kann nicht abgebrochen werden.  
  
 DB_E_CANCELED  
 Die Anforderung zum Abbrechen des asynchronen Vorgangs wurde während der Benachrichtigungen abgebrochen. Der Vorgang wird immer noch asynchron ausgeführt.  
  
 E_FAIL  
 Es ist ein anbieterspezifischer Fehler aufgetreten.  
  
 E_INVALIDARG  
 Der *hChapter* -Parameter ist nicht DB_NULL_HCHAPTER, oder *eOperation* ist nicht DBASYNCH_OPEN.  
  
 E_UNEXPECTED  
 **ISSAsynchStatus::Abort** wurde für ein Datenquellobjekt aufgerufen, für das **IDBInitialize::Initialize** nicht aufgerufen oder nicht abgeschlossen wurde.  
  
 **ISSAsynchStatus::Abort** wurde für ein Datenquellobjekt aufgerufen, für das **IDBInitialize::Initialize** aufgerufen wurde, das jedoch vor der Initialisierung abgebrochen wurde oder für das ein Timeout eingetreten ist. Das Datenquellobjekt wurde noch nicht initialisiert.  
  
 **ISSAsynchStatus::Abort** wurde für ein Rowset aufgerufen, für das zuvor **ITransaction::Commit** oder **ITransaction::Abort** aufgerufen wurde, und das Rowset blieb nach dem Commit oder Abbruch nicht bestehen und befindet sich in einem Zombiezustand.  
  
 **ISSAsynchStatus::Abort** wurde für ein Rowset aufgerufen, das in seiner Initialisierungsphase asynchron abgebrochen wurde. Das Rowset befindet sich in einem Zombiezustand.  
  
## <a name="remarks"></a>Hinweise  
 Durch Abbrechen der Initialisierung eines Rowsets oder eines Datenquellobjekts wird das Rowset bzw. das Datenquellobjekt möglicherweise in einen Zombiezustand versetzt, sodass für alle Methoden außer **IUnknown** -Methoden E_UNEXPECTED zurückgegeben wird. In diesem Fall hat der Consumer nur die Möglichkeit, das Rowset oder das Datenquellobjekt freizugeben.  
  
 Durch Aufrufen von **ISSAsynchStatus::Abort** und Übergeben eines anderen Werts für *eOperation* als DBASYNCHOP_OPEN wird S_OK zurückgegeben. Dies bedeutet nicht, dass der Vorgang abgeschlossen oder abgebrochen wurde.  
  
## <a name="see-also"></a>Siehe auch  
 [Ausführen asynchroner Vorgänge](../native-client/features/performing-asynchronous-operations.md)  
  
  
