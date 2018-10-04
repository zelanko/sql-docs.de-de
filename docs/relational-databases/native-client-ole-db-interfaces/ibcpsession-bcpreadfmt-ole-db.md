---
title: 'Ibcpsession:: Bcpreadfmt (OLE DB) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apiname:
- IBCPSession::BCPReadFmt (OLE DB)
apitype: COM
helpviewer_keywords:
- BCPReadFmt method
ms.assetid: e2a12050-94e4-48a3-8a48-b780d646f116
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 6ea7cc7aa437e5a5241579356c805f67bd017435
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47658696"
---
# <a name="ibcpsessionbcpreadfmt-ole-db"></a>'IBCPSession::BCPReadFmt' (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Liest für jede Spalte Formatinformationen aus der Formatdatei.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
HRESULT BCPReadFmt(   
      const wchar_t *pwszFormatFile);  
```  
  
## <a name="remarks"></a>Hinweise  
 Die **BCPReadFmt** -Methode wird verwendet, um Daten aus einer Formatdatei zu lesen, die das Format der Daten in der Datendatei angibt. Diese Methode kann die korrekte Version der Formatdatei ermitteln. Sie kann automatisch erkennen, ob die Formatdatei im XML-Format oder dem alten Textformat abgefasst ist und sich entsprechend verhält. Die Versionen der Format-Dateien, die von unterstützt die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter BCP werden Version 6.0 oder höher.  
  
 Nachdem die **BCPReadFmt**-Methode die Formatwerte gelesen hat, nimmt sie geeignete Aufrufe der Methoden [IBCPSession::BCPColumns](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpcolumns-ole-db.md) und [IBCPSession::BCPColFmt](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpcolfmt-ole-db.md) vor. Der Benutzer muss eine Formatdatei nicht analysieren, um diese Aufrufe zu tätigen.  
  
 Rufen Sie zum Speichern einer Formatdatei die [IBCPSession::BCPWriteFmt](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpwritefmt-ole-db.md)-Methode auf. Aufrufe der **BCPReadFmt** -Methode können auf gespeicherte Formate verweisen. Alternativ dazu kann das Hilfsprogramm zum Massenkopieren (**bcp**) benutzerdefinierte Datenformate in Dateien speichern, auf die mit der **BCPReadFmt** -Methode verwiesen werden kann.  
  
 Die **BCP_OPTION_DELAYREADFMT** Wert, der die *eOption* Parameter [ibcpsession:: Bcpcontrol](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpcontrol-ole-db.md) ändert das Verhalten von ibcpsession:: Bcpreadfmt.  
  
## <a name="arguments"></a>Argumente  
 *pwszFormatFile*[in]  
 Pfad und Dateiname der Datei, die die Formatwerte für die Datendatei enthält.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 S_OK  
 Die Methode wurde erfolgreich ausgeführt.  
  
 E_FAIL  
 Ein anbieterspezifischer Fehler ist aufgetreten. Ausführliche Informationen erhalten Sie über die [ISQLServerErrorInfo](http://msdn.microsoft.com/library/a8323b5c-686a-4235-a8d2-bda43617b3a1)-Schnittstelle.  
  
 E_OUTOFMEMORY  
 Fehler aufgrund von nicht genügend Arbeitsspeicher.  
  
 E_UNEXPECTED  
 Die Methode wurde unerwartet aufgerufen. Die [IBCPSession::BCPInit](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpinit-ole-db.md)-Methode wurde beispielsweise erst nach dem Aufruf dieser Methode aufgerufen.  
  
## <a name="see-also"></a>Siehe auch  
 [IBCPSession &#40;OLE-DB&#41;](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-ole-db.md)   
 [Durchführen von Massenkopiervorgängen](../../relational-databases/native-client/features/performing-bulk-copy-operations.md)  
  
  
