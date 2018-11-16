---
title: 'Ibcpsession:: BCPColumns (OLE DB) | Microsoft-Dokumentation'
description: IBCPSession::BCPColumns (OLE DB)
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.technology: connectivity
ms.topic: reference
apiname:
- IBCPSession::BCPColumns (OLE DB)
apitype: COM
helpviewer_keywords:
- BCPColumns method
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: 9e308b556a1a35cd52c97024b6dad93aa512bc85
ms.sourcegitcommit: 63b4f62c13ccdc2c097570fe8ed07263b4dc4df0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 11/13/2018
ms.locfileid: "51603200"
---
# <a name="ibcpsessionbcpcolumns-ole-db"></a>IBCPSession::BCPColumns (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Legt die Anzahl von Feldern fest, die an die Spalten einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Tabelle gebunden werden sollen.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
HRESULT BCPColumns(   
      DBCOUNTITEM nColumns);  
```  
  
## <a name="remarks"></a>Remarks  
 Intern wird [IBCPSession::BCPColFmt](../../oledb/ole-db-interfaces/ibcpsession-bcpcolfmt-ole-db.md) aufgerufen, um die Standardwerte für Felddaten festzulegen. Diese Standardwerte werden aus den SQL Server-Spalteninformationen abgerufen, die der Anbieter intern abruft, wenn der Tabellenname über [IBCPSession::BCPInit](../../oledb/ole-db-interfaces/ibcpsession-bcpinit-ole-db.md)angegeben wird.  
  
> [!NOTE]  
>  Diese Methode kann erst nach dem Aufruf von **BCPInit** mit einem gültigen Dateinamen aufgerufen werden.  
  
 Sie sollten diese Methode nur aufrufen, wenn Sie ein Benutzerdateiformat verwenden möchten, das sich vom Standardformat unterscheidet. Weitere Informationen mit einer Beschreibung des Standardformats für Benutzerdateien finden Sie unter der **BCPInit** -Methode.  
  
 Nach dem Aufruf der **BCPColumns** -Methode müssen Sie für alle Spalten in der Benutzerdatei die **BCPColFmt** -Methode aufrufen, um das benutzerdefinierte Dateiformat vollständig zu definieren.  
  
## <a name="arguments"></a>Argumente  
 *nColumns*[in]  
 Die Gesamtzahl der Felder in der Benutzerdatei. Auch wenn Sie das Massenkopieren von Daten aus der Benutzerdatei in eine SQL Server-Tabelle vorbereiten und nicht alle Felder in der Benutzerdatei kopieren möchten, müssen Sie das *nColumns* -Argument auf die Gesamtzahl der Benutzerdateifelder festlegen. Die übersprungenen Felder können dann durch **BCPColFmt**angegeben werden.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 S_OK  
 Die Methode wurde erfolgreich ausgeführt.  
  
 E_FAIL  
 Ein anwenderspezifischer Fehler ist aufgetreten. Ausführlichere Informationen erhalten Sie über die [ISQLServerErrorInfo](https://msdn.microsoft.com/library/a8323b5c-686a-4235-a8d2-bda43617b3a1) -Schnittstelle.  
  
 E_UNEXPECTED  
 Die Methode wurde unerwartet aufgerufen. Die **BCPInit** -Methode wurde beispielsweise erst nach dem Aufruf dieser Methode aufgerufen. Tritt auch auf, wenn diese Methode mehr als einmal für einen Massenkopiervorgang aufgerufen wird.  
  
 E_OUTOFMEMORY  
 Fehler aufgrund nicht genügenden Arbeitsspeichers  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [IBCPSession &#40;OLE-DB&#41;](../../oledb/ole-db-interfaces/ibcpsession-ole-db.md)   
 [Durchführen von Massenkopiervorgängen](../../oledb/features/performing-bulk-copy-operations.md)  
  
  
