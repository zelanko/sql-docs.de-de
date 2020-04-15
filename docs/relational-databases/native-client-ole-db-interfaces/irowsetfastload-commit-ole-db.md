---
title: IRowsetFastLoad::Commit (OLE DB) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apiname:
- IRowsetFastLoad::Commit (OLE DB)
apitype: COM
helpviewer_keywords:
- Commit method
ms.assetid: 19de9128-b91a-4626-847f-af721edaa24e
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 832fd37dc17edc155fb55101a8ae367190f1e57d
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307249"
---
# <a name="irowsetfastloadcommit-ole-db"></a>IRowsetFastLoad::Commit (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Markiert das Ende eines Batches eingefügter Zeilen und schreibt die Zeilen in die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Tabelle. Beispiele finden Sie unter [Massenkopieren von Daten mithilfe von IRowsetFastLoad &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-how-to/bulk-copy-data-using-irowsetfastload-ole-db.md) und [Senden von BLOB-Daten an SQL SERVER mit IROWSETFASTLOAD und ISEQUENTIALSTREAM &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-how-to/send-blob-data-to-sql-server-using-irowsetfastload-and-isequentialstream-ole-db.md).  
  
## <a name="syntax"></a>Syntax  
  
```  
  
HRESULT Commit(  
      BOOL fDone);  
```  
  
## <a name="arguments"></a>Argumente  
 *fDone*[in]  
 Wenn FALSE angegeben wird, behält das Rowset seine Gültigkeit und kann vom Consumer zum Einfügen zusätzlicher Zeilen verwendet werden. Wird TRUE angegeben, dann verliert das Rowset seine Gültigkeit, und der Consumer kann keine weiteren Einfügungen vornehmen.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 S_OK  
 Die Methode wurde erfolgreich ausgeführt, und alle eingefügten Daten wurden in die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Tabelle geschrieben.  
  
 E_FAIL  
 Es ist ein anbieterspezifischer Fehler aufgetreten. Rufen Sie Fehlerinformationen für den betreffenden Fehlertext vom Anbieter ab.  
  
 E_UNEXPECTED  
 Die Methode wurde für ein Rowset für das Massenkopieren aufgerufen, das zuvor von der **IRowsetFastLoad::Commit**-Methode für ungültig erklärt wurde.  
  
## <a name="remarks"></a>Bemerkungen  
 Ein [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Stammzeilenset eines nativen Client-OLE-DB-Anbieters verhält sich wie ein Rowset im verzögerten Aktualisierungsmodus. Wenn der Benutzer Zeilendaten über das Rowset einfügt, dann werden die eingefügten Zeilen so behandelt wie ausstehende Einfügungen in einem Rowset, das **IRowsetUpdate** unterstützt.  
  
 Der Consumer muss die **Commit**-Methode für das Rowset für das Massenkopieren ebenso aufrufen, um die eingefügten Zeilen in die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Tabelle zu schreiben, wie mithilfe der **IRowsetUpdate::Update-Methode** ausstehende Zeilen an eine Instanz von SQL Server gesendet werden.  
  
 Wenn der Consumer seinen Verweis auf das Rowset für das Massenkopieren freigibt, ohne die **Commit**-Methode aufzurufen, gehen alle Zeilen verloren, die vorher nicht in die Tabelle geschrieben wurden.  
  
 Der Consumer kann die eingefügten Zeilen als Batch definieren, indem er die **Commit**-Methode aufruft und das *fDone*-Argument auf FALSE festlegt. Wenn *fDone* auf TRUE festgelegt wird, wird das Rowset ungültig. Ein ungültiges Rowset für das Massenkopieren unterstützt nur die **ISupportErrorInfo**-Schnittstelle und die **IRowsetFastLoad::Release**-Methode.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IRowsetFastLoad &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/irowsetfastload-ole-db.md)  
  
  
