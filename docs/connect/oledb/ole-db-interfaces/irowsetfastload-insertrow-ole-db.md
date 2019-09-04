---
title: 'IRowsetFastLoad:: InsertRow (OLE DB) | Microsoft-Dokumentation'
description: IRowsetFastLoad::InsertRow (OLE DB)
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
apiname:
- IRowsetFastLoad::InsertRow (OLE DB)
apitype: COM
helpviewer_keywords:
- InsertRow method
author: pmasl
ms.author: pelopes
ms.openlocfilehash: b01c63e74ee26cea327a01e3bf9a3595bc5012d8
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68015452"
---
# <a name="irowsetfastloadinsertrow-ole-db"></a>IRowsetFastLoad::InsertRow (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Fügt dem Rowset für das Massenkopieren eine Zeile hinzu. Beispiele finden Sie unter [Massen Daten kopieren mit IRowsetFastLoad &#40;OLE DB&#41; ](../../oledb/ole-db-how-to/bulk-copy-data-using-irowsetfastload-ole-db.md) und [Senden von BLOB-Daten an SQL Server mit IRowsetFastLoad und ISequentialStream &#40;OLE DB&#41;](../../oledb/ole-db-how-to/send-blob-data-to-sql-server-using-irowsetfastload-and-isequentialstream-ole-db.md).  
  
## <a name="syntax"></a>Syntax  
  
```  
  
HRESULT InsertRow(  
      HACCESSOR hAccessor,  
      void* pData);  
```  
  
## <a name="arguments"></a>Argumente  
 *hAccessor*[in]  
 Das Handle des Accessors, der die Zeilendaten für das Massenkopieren definiert. Der Accessor, auf den verwiesen wird, ist ein Zeilenaccessor, der den consumer-eigenen Speicher bindet, in dem sich die Datenwerte befinden.  
  
 *pData*[in]  
 Ein Zeiger zum consumer-eigenen Speicher, in dem sich die Datenwerte befinden. Weitere Informationen finden Sie unter [DBBINDING-Strukturen](https://go.microsoft.com/fwlink/?LinkId=65955).  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 S_OK  
 Die Methode wurde erfolgreich ausgeführt. Alle gebundenen Statuswerte für alle Spalten weisen den Wert DBSTATUS_S_OK oder DBSTATUS_S_NULL auf.  
  
 E_FAIL  
 Ein Fehler ist aufgetreten. Fehlerinformationen sind über die Fehlerschnittstellen des Rowsets verfügbar.  
  
 E_INVALIDARG  
 Das *pData* -Argument wurde auf einen NULL-Zeiger festgelegt.  
  
 E_OUTOFMEMORY  
 MSOLEDBSQL konnte keinen ausreichenden Arbeitsspeicher zum Ausführen der Anforderung zuweisen.  
  
 E_UNEXPECTED  
 Die Methode wurde für ein Rowset für das Massenkopieren aufgerufen, das zuvor von der [IRowsetFastLoad::Commit](../../oledb/ole-db-interfaces/irowsetfastload-commit-ole-db.md) -Methode für ungültig erklärt wurde.  
  
 DB_E_BADACCESSORHANDLE  
 Das vom Consumer bereitgestellte *hAccessor* -Argument ist ungültig.  
  
 DB_E_BADACCESSORTYPE  
 Der angegebene Accessor war kein Zeilenaccessor oder hat keinen consumer-eigenen Arbeitsspeicher angegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Ein Fehler bei der Konvertierung der Consumerdaten in den [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Datentyp einer Spalte ruft eine E_FAIL-Rückgabe durch den OLE DB-Treiber für SQL Server hervor. Die Daten können entweder über eine beliebige [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]InsertRow **-Methode oder nur über die** Commit **-Methode an**  übertragen werden. lDie Consumer-Anwendung kann die **InsertRow** -Methode mehrere Male mit fehlerhaften Daten aufrufen, bevor eine Meldung eintrifft, dass die Daten nicht korrekt sind. Die **Commit** -Methode gewährleistet, dass alle Daten ordnungsgemäß vom Consumer angegeben werden. Der Consumer kann die **Commit** -Methode gegebenenfalls verwenden, um die Daten zu überprüfen.  
  
 Der OLE DB Treiber für SQL Server Rowsets zum Massen kopieren ist schreibgeschützt. Der OLE DB-Treiber für SQL Server macht keine Methoden verfügbar, die Consumer-Abfragen des Rowsets zulassen. Um die Verarbeitung zu beenden, kann der Consumer seine Verweise auf die [IRowsetFastLoad](../../oledb/ole-db-interfaces/irowsetfastload-ole-db.md)-Schnittstelle ohne die **Commit**-Methode senden. Es gibt keine Möglichkeit, auf von Consumern eingefügte Zeilen im Rowset zuzugreifen und deren Werte zu ändern oder diese einzeln aus dem Rowset zu entfernen.  
  
 Massenkopierte Zeilen werden auf dem Server für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] formatiert. Das Zeilenformat entspricht den Optionen, die eventuell für die Verbindung oder die Sitzung festgelegt wurden, wie z. B. ANSI_PADDING. Diese Option wird standardmäßig für alle Verbindungen festgelegt, die über den OLE DB-Treiber für SQL Server hergestellt werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IRowsetFastLoad &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/irowsetfastload-ole-db.md)  
  
  
