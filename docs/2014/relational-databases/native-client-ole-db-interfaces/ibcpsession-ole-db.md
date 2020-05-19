---
title: IBCPSession (OLE DB) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- IBCPSession interface
ms.assetid: 00d0311f-8b71-4ad6-824d-0e89119347a3
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 10165ed57c12b06fc1317bb440dd1635849582f6
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/01/2020
ms.locfileid: "82695249"
---
# <a name="ibcpsession-ole-db"></a>IBCPSession (OLE DB)
  Die **IBCPSession**-Schnittstelle unterstützt dateibasierte Massenkopiervorgänge für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Die **IBCPSession** Schnittstelle wird im OLE DB-Anbieter von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client auf derselben Ebene wie Session-Objekte verfügbar gemacht. Im OLE DB-Anbieter von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client sind Datenquellenobjekte Factorys für Session-Objekte, und Massenkopiervorgänge werden in der Verbindungseigenschaft SSPROP_ENABLEBULKCOPY angegeben. Außerdem sollte die SSPROP_ENABLEFASTLOAD-Eigenschaft auf true festgelegt werden.  
  
 Ein Aufruf der **IDBCreateSession::CreateSession** -Methode führt dann zur Erstellung eines **BulkCopySession** -Objekts. Alle durch das **IBCPSession** -Objekt verfügbar gemachten dateibasierten Massenkopiermethoden sind mit einer ganz ähnlichen Syntax über die **IBCPSession** -Schnittstelle dieses **IBCPSession** -Objekts aufrufbar.  
  
> [!NOTE]  
>  Der OLE DB-Anbieter von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client unterstützt speicherbasierte Massenkopiervorgänge durch die [IRowsetFastLoad](irowsetfastload-ole-db.md) -Schnittstelle.  
  
 Weitere Informationen zur Verwendung des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-OLE DB Anbieters für Massen Kopiervorgänge finden Sie unter [Durchführen von Massen Kopier Vorgängen](../native-client/features/performing-bulk-copy-operations.md).  
  
 Ein Beispiel für die Verwendung der **IBCPSession**-Schnittstelle finden Sie unter [IBCPSession::BCPDone &#40;OLE DB&#41;](ibcpsession-bcpdone-ole-db.md).  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IBCPSession::BCPColFmt &#40;OLE DB&#41;](ibcpsession-bcpcolfmt-ole-db.md)|Erstellt eine Bindung zwischen Programmvariablen und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Spalten.|  
|[IBCPSession::BCPColumns &#40;OLE DB&#41;](ibcpsession-bcpcolumns-ole-db.md)|Legt die Anzahl von Feldern fest, die an die Spalten einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Tabelle gebunden werden sollen.|  
|[IBCPSession::BCPControl &#40;OLE DB&#41;](ibcpsession-bcpcontrol-ole-db.md)|Legt die Optionen für einen Massenkopiervorgang fest.|  
|[IBCPSession::BCPDone &#40;OLE DB&#41;](ibcpsession-bcpdone-ole-db.md)|Führt einen Commit für die übrigen Zeilen aus, die an [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]gesendet werden sollen.|  
|[IBCPSession::BCPExec &#40;OLE DB&#41;](ibcpsession-bcpexec-ole-db.md)|Führt den Massenkopiervorgang aus.|  
|[IBCPSession::BCPInit &#40;OLE DB&#41;](ibcpsession-bcpinit-ole-db.md)|Initialisiert die Massenkopierstruktur, führt einige Fehlerprüfungen durch, überprüft die korrekte Angabe der Daten- und Formatdateinamen und öffnet dann diese Dateien.|  
|[IBCPSession::BCPReadFmt &#40;OLE DB&#41;](ibcpsession-bcpreadfmt-ole-db.md)|Liest für jede Spalte Formatinformationen aus der Formatdatei.|  
|[IBCPSession::BCPWriteFmt &#40;OLE DB&#41;](ibcpsession-bcpwritefmt-ole-db.md)|Schreibt für jede Spalte Formatinformationen in die Formatdatei.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Schnittstellen &#40;OLE DB&#41;](../../database-engine/dev-guide/interfaces-ole-db.md)  
  
  
