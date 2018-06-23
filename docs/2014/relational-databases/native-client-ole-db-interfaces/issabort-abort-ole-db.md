---
title: 'Issabort:: Abort (OLE DB) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- ISSAbort::Abort (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- Abort method
ms.assetid: a5bca169-694b-4895-84ac-e8fba491e479
caps.latest.revision: 15
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 0729183a2e5be91d3cdb30eae3ae5990f8398103
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36147888"
---
# <a name="issabortabort-ole-db"></a>ISSAbort::Abort (OLE DB)
  Bricht das aktuelle Rowset sowie eventuell mit dem aktuellen Befehl verknüpfte Batchbefehle ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
HRESULT Abort(void);  
```  
  
## <a name="remarks"></a>Hinweise  
 Wenn der abgebrochene Befehl eine gespeicherte Prozedur ist, wird die Ausführung der gespeicherten Prozedur (und aller Prozeduren, die diese Prozedur aufgerufen haben) sowie des Befehlsbatch, der den gespeicherten Prozeduraufruf enthielt, ebenfalls beendet. Falls der Server gerade ein Resultset an den Client überträgt, wird dieses gestoppt. Wenn der Client ein Resultset nicht verarbeitet, wird durch Aufrufen von **ISSAbort::Abort** vor dem Freigeben des Rowsets die Rowsetfreigabe beschleunigt, aber wenn eine offene Transaktion vorhanden ist und XACT_ABORT auf ON gestellt ist, wird beim Aufrufen von **ISSAbort::Abort** ein Rollback für die Transaktion ausgeführt.  
  
 Sobald **ISSAbort::Abort** S_OK zurückgibt, kann die zugehörige **IMultipleResults** -Schnittstelle nicht mehr verwendet werden und gibt bei allen Methodenaufrufen DB_E_CANCELED zurück (außer bei Methoden, die durch die **IUnknown** -Schnittstelle definiert sind), bis sie wieder freigegeben wird. Falls vor dem **Abort** -Aufruf ein **IRowset** von **IMultipleResults**empfangen wurde, ist dieses ebenfalls nicht mehr verwendbar und gibt bei allen Methodenaufrufen DB_E_CANCELED zurück (außer bei Methoden, die durch die **IUnknown** -Schnittstelle und **IRowset::ReleaseRows**definiert sind), bis es nach einem erfolgreichen Aufruf von **ISSAbort::Abort**wieder freigegeben wird.  
  
> [!NOTE]  
>  Beginnend mit [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], wenn der Serverstatus XACT_ABORT ON ist, Ausführen von **issabort:: Abort** beendet und führt einen Rollback für alle aktuellen impliziten oder expliziten Transaktionen beim Verbinden mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Frühere Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] brechen die aktuelle Transaktion nicht ab.  
  
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
 Ein anbieterspezifischer Fehler aufgetreten. Ausführliche Informationen erhalten Sie die [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md) Schnittstelle.  
  
 E_UNEXPECTED  
 Die Methode wurde unerwartet aufgerufen. Zum Beispiel ist das Objekt in einem Zombiezustand, da **ISSAbort::Abort** bereits aufgerufen wurde.  
  
 E_OUTOFMEMORY  
 Fehler aufgrund von nicht genügend Arbeitsspeicher.  
  
## <a name="see-also"></a>Siehe auch  
 [ISSAbort &#40;OLE DB&#41;](../../database-engine/dev-guide/issabort-ole-db.md)  
  
  