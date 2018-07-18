---
title: 'Ibcpsession:: Bcpwritefmt (OLE DB) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- IBCPSession::BCPWriteFmt (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- BCPWriteFmt method
ms.assetid: add50425-2ed6-411a-a391-4ce63c364892
caps.latest.revision: 24
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 68be3cd9b1296ed1f9e3530c4aadcc5a28cea891
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37431049"
---
# <a name="ibcpsessionbcpwritefmt-ole-db"></a>IBCPSession::BCPWriteFmt (OLE DB)
  Schreibt für jede Spalte Formatinformationen in die Formatdatei.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
HRESULT BCPWriteFmt(   
const wchar_t *pwszFormatFile);  
```  
  
## <a name="remarks"></a>Hinweise  
 Die Formatdatei gibt das Datenformat einer durch Massenkopieren erstellten Datendatei an. Aufrufe von der [ibcpsession:: BCPColumns](ibcpsession-bcpcolumns-ole-db.md) und [ibcpsession:: BCPColFmt](ibcpsession-bcpcolfmt-ole-db.md) Methoden definieren das Format der Datendatei. Die Methode **BCPWriteFmt** speichert diese Definition in der im Argument pwszFormatFile angegebenen Datei.  
  
 Die **BCPWriteFmt** -Methode kann die Formatdateien in XML- oder Textformat speichern. Dies muss angegeben werden, mithilfe der BCP_OPTION_XML-Steueroption und der [ibcpsession:: Bcpcontrol](ibcpsession-bcpcontrol-ole-db.md) Methode.  
  
 Um eine gespeicherte Formatdatei zu laden, verwenden die [ibcpsession:: Bcpreadfmt](ibcpsession-bcpreadfmt-ole-db.md) Methode.  
  
## <a name="arguments"></a>Argumente  
 *pwszFormatFile*[in]  
 Pfad und Dateiname der Datei, die die Formatwerte für die Datendatei enthält.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 S_OK  
 Die Methode wurde erfolgreich ausgeführt.  
  
 E_FAIL  
 Ein anbieterspezifischer Fehler ist aufgetreten; Verwenden Sie ausführliche Informationen, die [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md) Schnittstelle.  
  
 E_OUTOFMEMORY  
 Fehler aufgrund nicht genügenden Arbeitsspeichers  
  
 E_UNEXPECTED  
 Die Methode wurde unerwartet aufgerufen. Z. B. die [ibcpsession:: BCPInit](ibcpsession-bcpinit-ole-db.md) Methode wurde nicht aufgerufen, bevor diese Methode aufgerufen.  
  
## <a name="see-also"></a>Siehe auch  
 [IBCPSession &#40;OLE-DB&#41;](ibcpsession-ole-db.md)   
 [Durchführen von Massenkopiervorgängen](../native-client/features/performing-bulk-copy-operations.md)  
  
  
