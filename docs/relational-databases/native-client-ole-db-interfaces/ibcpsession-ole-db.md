---
title: IBCPSession (OLE DB) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
apitype: COM
helpviewer_keywords:
- IBCPSession interface
ms.assetid: 00d0311f-8b71-4ad6-824d-0e89119347a3
caps.latest.revision: 28
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 52120c336cd976d8eac8f04aef32217d5fe18ac3
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "43077853"
---
# <a name="ibcpsession-ole-db"></a>IBCPSession (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Die **IBCPSession**-Schnittstelle unterstützt dateibasierte Massenkopiervorgänge für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Die **IBCPSession** Schnittstelle verfügbar gemacht wird, der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter auf derselben Ebene wie Session. In der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter Datenquellenobjekte Factorys für Session-Objekte, und Massenkopiervorgänge werden in der Verbindungseigenschaft SSPROP_ENABLEBULKCOPY angegeben. Außerdem sollte die SSPROP_ENABLEFASTLOAD-Eigenschaft auf true festgelegt werden.  
  
 Ein Aufruf der **IDBCreateSession::CreateSession** -Methode führt dann zur Erstellung eines **BulkCopySession** -Objekts. Alle durch das **IBCPSession** -Objekt verfügbar gemachten dateibasierten Massenkopiermethoden sind mit einer ganz ähnlichen Syntax über die **IBCPSession** -Schnittstelle dieses **IBCPSession** -Objekts aufrufbar.  
  
> [!NOTE]  
>  Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter unterstützt speicherbasierte Massenkopiervorgänge durch die [IRowsetFastLoad](../../relational-databases/native-client-ole-db-interfaces/irowsetfastload-ole-db.md) Schnittstelle.  
  
 Weitere Informationen zur Verwendung der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter für Massenkopiervorgänge, finden Sie unter [Durchführen von Massenkopiervorgängen](../../relational-databases/native-client/features/performing-bulk-copy-operations.md).  
  
 Ein Beispiel zur Verwendung der **IBCPSession** Benutzeroberfläche, siehe [IBCPSession::BCPDone &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpdone-ole-db.md).  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
|Methode|Description|  
|------------|-----------------|  
|[Ibcpsession:: BCPColFmt &#40;OLE-DB&#41;](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpcolfmt-ole-db.md)|Erstellt eine Bindung zwischen Programmvariablen und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Spalten.|  
|[Ibcpsession:: BCPColumns &#40;OLE-DB&#41;](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpcolumns-ole-db.md)|Legt die Anzahl von Feldern fest, die an die Spalten einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Tabelle gebunden werden sollen.|  
|[Ibcpsession:: Bcpcontrol &#40;OLE-DB&#41;](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpcontrol-ole-db.md)|Legt die Optionen für einen Massenkopiervorgang fest.|  
|[IBCPSession::BCPDone &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpdone-ole-db.md)|Führt einen Commit für die übrigen Zeilen aus, die an [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gesendet werden sollen.|  
|[Ibcpsession &#40;OLE-DB&#41;](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpexec-ole-db.md)|Führt den Massenkopiervorgang aus.|  
|[Ibcpsession:: BCPInit &#40;OLE-DB&#41;](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpinit-ole-db.md)|Initialisiert die Massenkopierstruktur, führt einige Fehlerprüfungen durch, überprüft die korrekte Angabe der Daten- und Formatdateinamen und öffnet dann diese Dateien.|  
|[Ibcpsession:: Bcpreadfmt &#40;OLE-DB&#41;](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpreadfmt-ole-db.md)|Liest für jede Spalte Formatinformationen aus der Formatdatei.|  
|[Ibcpsession:: Bcpwritefmt &#40;OLE-DB&#41;](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpwritefmt-ole-db.md)|Schreibt für jede Spalte Formatinformationen in die Formatdatei.|  
  
## <a name="see-also"></a>Siehe auch  
 [Schnittstellen &#40;OLE-DB&#41;](http://msdn.microsoft.com/library/34c33364-8538-45db-ae41-5654481cda93)  
  
  
