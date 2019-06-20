---
title: 'IRowsetFastLoad:: InsertRow (OLE DB) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- IRowsetFastLoad::InsertRow (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- InsertRow method
ms.assetid: 594d3461-34d2-41e7-8ad4-bd2753601ab6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9c4cd4aff0a8868b8870374fcffb8c7b7169fe2e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62511629"
---
# <a name="irowsetfastloadinsertrow-ole-db"></a>IRowsetFastLoad::InsertRow (OLE DB)
  Fügt dem Rowset für das Massenkopieren eine Zeile hinzu. Beispiele finden Sie [Bulk Daten mithilfe von IRowsetFastLoad &#40;OLE DB&#41; ](../native-client-ole-db-how-to/bulk-copy-data-using-irowsetfastload-ole-db.md) und [Senden von BLOB-Daten zu SQL SERVER mithilfe von IROWSETFASTLOAD und ISEQUENTIALSTREAM &#40;OLE DB&#41;](../native-client-ole-db-how-to/send-blob-data-to-sql-server-using-irowsetfastload-and-isequentialstream-ole-db.md).  
  
## <a name="syntax"></a>Syntax  
  
```  
  
HRESULT InsertRow(  
HACCESSOR  
hAccessor  
,  
void*  
pData  
);  
  
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
 SQLNCLI11 konnte keinen ausreichenden Arbeitsspeicher zum Ausführen der Anforderung zuordnen.  
  
 E_UNEXPECTED  
 Die Methode wurde für ein Rowset für das Massenkopieren aufgerufen, das zuvor von der [IRowsetFastLoad::Commit](irowsetfastload-commit-ole-db.md) -Methode für ungültig erklärt wurde.  
  
 DB_E_BADACCESSORHANDLE  
 Das vom Consumer bereitgestellte *hAccessor* -Argument ist ungültig.  
  
 DB_E_BADACCESSORTYPE  
 Der angegebene Accessor war kein Zeilenaccessor oder hat keinen consumer-eigenen Arbeitsspeicher angegeben.  
  
## <a name="remarks"></a>Hinweise  
 Ein Fehler bei der Konvertierung der Consumerdaten in den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datentyp einer Spalte ruft eine E_FAIL-Rückgabe durch den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-OLE DB-Anbieter hervor. Die Daten können entweder über eine beliebige [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] InsertRow **-Methode oder nur über die** Commit **-Methode an** übertragen werden. lDie Consumer-Anwendung kann die **InsertRow** -Methode mehrere Male mit fehlerhaften Daten aufrufen, bevor eine Meldung eintrifft, dass die Daten nicht korrekt sind. Die **Commit** -Methode gewährleistet, dass alle Daten ordnungsgemäß vom Consumer angegeben werden. Der Consumer kann die **Commit** -Methode gegebenenfalls verwenden, um die Daten zu überprüfen.  
  
 Die Massenkopiervorgänge des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-OLE DB-Anbieters erlauben nur den Schreibzugriff. Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-OLE DB-Anbieter macht keine Methoden verfügbar, die Abfragen von Consumern hinsichtlich des Rowsets verfügbar machen. Um die Verarbeitung zu beenden, kann der Consumer seine Verweise auf die [IRowsetFastLoad](irowsetfastload-ole-db.md)-Schnittstelle ohne die **Commit**-Methode senden. Es gibt keine Möglichkeit, auf von Consumern eingefügte Zeilen im Rowset zuzugreifen und deren Werte zu ändern oder diese einzeln aus dem Rowset zu entfernen.  
  
 Massenkopierte Zeilen werden auf dem Server für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] formatiert. Das Zeilenformat entspricht den Optionen, die eventuell für die Verbindung oder die Sitzung festgelegt wurden, wie z. B. ANSI_PADDING. Diese Option ist standardmäßig für alle über den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-OLE DB-Anbieter angebotenen Verbindungen aktiviert.  
  
## <a name="see-also"></a>Siehe auch  
 [IRowsetFastLoad &#40;OLE DB&#41;](irowsetfastload-ole-db.md)  
  
  
