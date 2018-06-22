---
title: Bcpwritefmt (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IBCPSession::BCPWriteFmt (OLE DB)
apitype: COM
helpviewer_keywords:
- BCPWriteFmt method
ms.assetid: add50425-2ed6-411a-a391-4ce63c364892
caps.latest.revision: 24
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 517ee0611a613d7a450f29e66eeb4d9d431a3056
ms.sourcegitcommit: a78fa85609a82e905de9db8b75d2e83257831ad9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2018
ms.locfileid: "35694512"
---
# <a name="ibcpsessionbcpwritefmt-ole-db"></a>IBCPSession::BCPWriteFmt (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Schreibt für jede Spalte Formatinformationen in die Formatdatei.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
HRESULT BCPWriteFmt(   
      const wchar_t *pwszFormatFile);  
```  
  
## <a name="remarks"></a>Hinweise  
 Die Formatdatei gibt das Datenformat einer durch Massenkopieren erstellten Datendatei an. Aufrufe von der [ibcpsession:: BCPColumns](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpcolumns-ole-db.md) und [ibcpsession:: BCPColFmt](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpcolfmt-ole-db.md) Methoden definieren Sie das Format der Datendatei. Die Methode **BCPWriteFmt** speichert diese Definition in der im Argument pwszFormatFile angegebenen Datei.  
  
 Die **BCPWriteFmt** -Methode kann die Formatdateien in XML- oder Textformat speichern. Dies muss angegeben werden, mithilfe der BCP_OPTION_XML-Steueroption der [ibcpsession:: Bcpcontrol](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpcontrol-ole-db.md) Methode.  
  
 Um eine gespeicherte Formatdatei zu laden, verwenden die [ibcpsession:: Bcpreadfmt](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpreadfmt-ole-db.md) Methode.  
  
## <a name="arguments"></a>Argumente  
 *pwszFormatFile*[in]  
 Pfad und Dateiname der Datei, die die Formatwerte für die Datendatei enthält.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 S_OK  
 Die Methode wurde erfolgreich ausgeführt.  
  
 E_FAIL  
 Ein anbieterspezifischer Fehler aufgetreten. Ausführliche Informationen erhalten Sie die [ISQLServerErrorInfo](http://msdn.microsoft.com/library/a8323b5c-686a-4235-a8d2-bda43617b3a1) Schnittstelle.  
  
 E_OUTOFMEMORY  
 Fehler aufgrund nicht genügenden Arbeitsspeichers  
  
 E_UNEXPECTED  
 Die Methode wurde unerwartet aufgerufen. Z. B. die [ibcpsession:: BCPInit](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpinit-ole-db.md) Methode vor dem Aufrufen dieser Methode nicht aufgerufen wurde.  
  
## <a name="see-also"></a>Siehe auch  
 [IBCPSession &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-ole-db.md)   
 [Durchführen von Massenkopiervorgängen](../../relational-databases/native-client/features/performing-bulk-copy-operations.md)  
  
  
