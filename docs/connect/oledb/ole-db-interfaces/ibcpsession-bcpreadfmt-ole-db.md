---
title: IBCPSession::BCPReadFmt (OLE DB-Treiber) | Microsoft-Dokumentation
description: Verwenden von „IBCPSession::BCPReadFmt“ zum Lesen von Daten aus einer Formatdatei (OLE DB)
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
apiname:
- IBCPSession::BCPReadFmt (OLE DB)
apitype: COM
helpviewer_keywords:
- BCPReadFmt method
author: pmasl
ms.author: pelopes
ms.openlocfilehash: e8df0e8b64795414734c93512a17951f8867c3a8
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/28/2020
ms.locfileid: "87244596"
---
# <a name="ibcpsessionbcpreadfmt-ole-db"></a>'IBCPSession::BCPReadFmt' (OLE DB)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Liest für jede Spalte Formatinformationen aus der Formatdatei.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
HRESULT BCPReadFmt(   
      const wchar_t *pwszFormatFile);  
```  
  
## <a name="remarks"></a>Bemerkungen  
 Die **BCPReadFmt** -Methode wird verwendet, um Daten aus einer Formatdatei zu lesen, die das Format der Daten in der Datendatei angibt. Diese Methode kann die korrekte Version der Formatdatei ermitteln. Sie kann automatisch erkennen, ob die Formatdatei im XML-Format oder dem alten Textformat abgefasst ist und sich entsprechend verhält. Die Formatdateiversionen, die vom Hilfsprogramm BCP des OLE DB-Treibers für SQL Server unterstützt werden, sind Version 6.0 oder neuer.  
  
 Nachdem die **BCPReadFmt**-Methode die Formatwerte gelesen hat, nimmt sie geeignete Aufrufe der Methoden [IBCPSession::BCPColumns](../../oledb/ole-db-interfaces/ibcpsession-bcpcolumns-ole-db.md) und [IBCPSession::BCPColFmt](../../oledb/ole-db-interfaces/ibcpsession-bcpcolfmt-ole-db.md) vor. Der Benutzer muss eine Formatdatei nicht analysieren, um diese Aufrufe zu tätigen.  
  
 Rufen Sie zum Speichern einer Formatdatei die [IBCPSession::BCPWriteFmt](../../oledb/ole-db-interfaces/ibcpsession-bcpwritefmt-ole-db.md)-Methode auf. Aufrufe der **BCPReadFmt** -Methode können auf gespeicherte Formate verweisen. Alternativ dazu kann das Hilfsprogramm zum Massenkopieren (**bcp**) benutzerdefinierte Datenformate in Dateien speichern, auf die mit der **BCPReadFmt** -Methode verwiesen werden kann.  
  
 Der **BCP_OPTION_DELAYREADFMT**-Wert des Parameters *eOption* von [IBCPSession::BCPControl](../../oledb/ole-db-interfaces/ibcpsession-bcpcontrol-ole-db.md) ändert das Verhalten von „IBCPSession::BCPReadFmt“.  
  
## <a name="arguments"></a>Argumente  
 *pwszFormatFile*[in]  
 Pfad und Dateiname der Datei, die die Formatwerte für die Datendatei enthält.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 S_OK  
 Die Methode wurde erfolgreich ausgeführt.  
  
 E_FAIL  
 Ein anbieterspezifischer Fehler ist aufgetreten. Ausführliche Informationen erhalten Sie über die [ISQLServerErrorInfo](https://msdn.microsoft.com/library/a8323b5c-686a-4235-a8d2-bda43617b3a1)-Schnittstelle.  
  
 E_OUTOFMEMORY  
 Fehler aufgrund von nicht genügend Arbeitsspeicher.  
  
 E_UNEXPECTED  
 Die Methode wurde unerwartet aufgerufen. Die [IBCPSession::BCPInit](../../oledb/ole-db-interfaces/ibcpsession-bcpinit-ole-db.md)-Methode wurde beispielsweise erst nach dem Aufruf dieser Methode aufgerufen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IBCPSession &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/ibcpsession-ole-db.md)   
 [Durchführen von Massenkopiervorgängen](../../oledb/features/performing-bulk-copy-operations.md)  
  
  
