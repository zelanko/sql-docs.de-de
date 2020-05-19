---
title: IBCPSession::BCPColumns (OLE DB) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- IBCPSession::BCPColumns (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- BCPColumns method
ms.assetid: c338abe8-9e30-4853-a7c6-b1a6c00095e1
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: f18437b807c9cc45b54841255d2b7bb4ba98b45c
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/01/2020
ms.locfileid: "82695749"
---
# <a name="ibcpsessionbcpcolumns-ole-db"></a>IBCPSession::BCPColumns (OLE DB)
  Legt die Anzahl von Feldern fest, die an die Spalten einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Tabelle gebunden werden sollen.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
HRESULT BCPColumns(   
DBCOUNTITEMnColumns);  
```  
  
## <a name="remarks"></a>Bemerkungen  
 Intern wird [IBCPSession::BCPColFmt](ibcpsession-bcpcolfmt-ole-db.md) aufgerufen, um die Standardwerte für Felddaten festzulegen. Diese Standardwerte werden aus den SQL Server-Spalteninformationen abgerufen, die der Anbieter intern abruft, wenn der Tabellenname über [IBCPSession::BCPInit](ibcpsession-bcpinit-ole-db.md) angegeben wird.  
  
> [!NOTE]  
>   Diese Methode kann erst nach dem Aufruf von **BCPInit** mit einem gültigen Dateinamen aufgerufen werden.  
  
 Sie sollten diese Methode nur aufrufen, wenn Sie ein Benutzerdateiformat verwenden möchten, das sich vom Standardformat unterscheidet. Weitere Informationen mit einer Beschreibung des Standardformats für Benutzerdateien finden Sie unter der **BCPInit** -Methode.  
  
 Nach dem Aufruf der **BCPColumns** -Methode müssen Sie für alle Spalten in der Benutzerdatei die **BCPColFmt** -Methode aufrufen, um das benutzerdefinierte Dateiformat vollständig zu definieren.  
  
## <a name="arguments"></a>Argumente  
 *nColumns*[in]  
 Die Gesamtzahl der Felder in der Benutzerdatei. Auch wenn Sie das Massenkopieren von Daten aus der Benutzerdatei in eine SQL Server-Tabelle vorbereiten und nicht alle Felder in der Benutzerdatei kopieren möchten, müssen Sie das *nColumns* -Argument auf die Gesamtzahl der Benutzerdateifelder festlegen. Die übersprungenen Felder können dann durch **BCPColFmt**angegeben werden.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 S_OK  
 Die Methode wurde erfolgreich ausgeführt.  
  
 E_FAIL  
 Ein Anbieter spezifischer Fehler ist aufgetreten. Ausführliche Informationen erhalten Sie, wenn Sie die [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md) -Schnittstelle verwenden.  
  
 E_UNEXPECTED  
 Die Methode wurde unerwartet aufgerufen. Die **BCPInit** -Methode wurde beispielsweise erst nach dem Aufruf dieser Methode aufgerufen. Tritt auch auf, wenn diese Methode mehr als einmal für einen Massenkopiervorgang aufgerufen wird.  
  
 E_OUTOFMEMORY  
 Fehler aufgrund nicht genügenden Arbeitsspeichers  
  
## <a name="see-also"></a>Weitere Informationen  
 [IBCPSession &#40;OLE DB&#41;](ibcpsession-ole-db.md)   
 [Durchführen von Massenkopiervorgängen](../native-client/features/performing-bulk-copy-operations.md)  
  
  
