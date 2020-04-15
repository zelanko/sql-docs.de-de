---
title: Abrufen großer Datenmengen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- BLOBs, OLE objects
- DBPROP_ACCESSORDER property
- SQL Server Native Client OLE DB provider, BLOBs
- large data, OLE objects
ms.assetid: a31c5632-96aa-483f-a307-004c5149fbc0
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 9ba1762bdc54c5ffe3e3879d21edd5e48c096f03
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303621"
---
# <a name="getting-large-data"></a>Abrufen großer Datenmengen
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Im Allgemeinen sollten Verbraucher Code [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] isolieren, der ein Native Client OLE DB-Anbieterspeicherobjekt aus anderem Code erstellt, der Daten verarbeitet, auf die nicht über einen **ISequentialStream-Schnittstellenzeiger** verwiesen wird.  
  
 In diesem Thema wird die mit folgenden Funktionen verfügbare Funktionalität behandelt:  
  
-   IRowset:GetData  
  
-   IRow::GetColumns  
  
-   ICommand::Execute  
  
 Wenn die DBPROP_ACCESSORDER-Eigenschaft (in der Rowset-Eigenschaftsgruppe) entweder auf die Werte DBPROPVAL_AO_SEQUENTIAL oder DBPROPVAL_AO_SEQUENTIALSTORAGEOBJECTS festgelegt ist, sollte der Consumer nur eine einzelne Datenzeile in einem Aufruf der **GetNextRows-Methode** abrufen, da BLOB-Daten nicht gepuffert sind. Ist der Wert von DBPROP_ACCESSORDER auf DBPROPVAL_AO_RANDOM festgelegt, kann der Consumer mehrere Datenzeilen mit **GetNextRows** abrufen.  
  
 Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native Client-OLE-DB-Anbieter [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ruft keine großen Daten ab, bis der Consumer dies angefordert hat. Der Consumer sollte alle kleinen Datenmengen in einem Accessor zusammenfassen und dann einen oder mehrere Accessoren zum Abrufen großer Datenwerte verwenden.  
  
## <a name="example"></a>Beispiel  
 In diesem Beispiel wird ein großer Datenwert aus einer einzelnen Spalte abgerufen:  
  
```  
HRESULT GetUnboundData  
    (  
    IRowset* pIRowset,  
    HROW hRow,  
    ULONG nCol,   
    BYTE* pUnboundData  
    )  
    {  
    UINT                cbRow = sizeof(IUnknown*) + sizeof(ULONG);  
    BYTE*               pRow = new BYTE[cbRow];  
  
    DBOBJECT            dbobject;  
  
    IAccessor*          pIAccessor = NULL;  
    HACCESSOR           haccessor;  
  
    DBBINDING           dbbinding;  
    ULONG               ulbindstatus;  
  
    ULONG               dwStatus;  
    ISequentialStream*  pISequentialStream;  
    ULONG               cbRead;  
  
    HRESULT             hr;  
  
    // Set up the DBOBJECT structure.  
    dbobject.dwFlags = STGM_READ;  
    dbobject.iid = IID_ISequentialStream;  
  
    // Create the DBBINDING, requesting a storage-object pointer from  
    // The SQL Server Native Client OLE DB provider.  
    dbbinding.iOrdinal = nCol;  
    dbbinding.obValue = 0;  
    dbbinding.obStatus = sizeof(IUnknown*);  
    dbbinding.obLength = 0;  
    dbbinding.pTypeInfo = NULL;  
    dbbinding.pObject = &dbobject;  
    dbbinding.pBindExt = NULL;  
    dbbinding.dwPart = DBPART_VALUE | DBPART_STATUS;  
    dbbinding.dwMemOwner = DBMEMOWNER_CLIENTOWNED;  
    dbbinding.eParamIO = DBPARAMIO_NOTPARAM;  
    dbbinding.cbMaxLen = 0;  
    dbbinding.dwFlags = 0;  
    dbbinding.wType = DBTYPE_IUNKNOWN;  
    dbbinding.bPrecision = 0;  
    dbbinding.bScale = 0;  
  
    if (FAILED(hr = pIRowset->  
        QueryInterface(IID_IAccessor, (void**) &pIAccessor)))  
        {  
        // Process QueryInterface failure.  
        return (hr);  
        }  
  
    // Create the accessor.  
    if (FAILED(hr = pIAccessor->CreateAccessor(DBACCESSOR_ROWDATA, 1,  
        &dbbinding, 0, &haccessor, &ulbindstatus)))  
        {  
        // Process error from CreateAccessor.  
        pIAccessor->Release();  
        return (hr);  
        }  
  
    // Read and process BLOCK_SIZE bytes at a time.  
    if (SUCCEEDED(hr = pIRowset->GetData(hRow, haccessor, pRow)))  
        {  
        dwStatus = *((ULONG*) (pRow + dbbinding.obStatus));  
  
        if (dwStatus == DBSTATUS_S_ISNULL)  
            {  
            // Process NULL data  
            }  
        else if (dwStatus == DBSTATUS_S_OK)  
            {  
            pISequentialStream = *((ISequentialStream**)   
                (pRow + dbbinding.obValue));  
  
            do  
                {  
                if (SUCCEEDED(hr =  
                    pISequentialStream->Read(pUnboundData,  
                    BLOCK_SIZE, &cbRead)))  
                    {  
                    pUnboundData += cbRead;  
                    }  
                }  
            while (SUCCEEDED(hr) && cbRead >= BLOCK_SIZE);  
  
            pISequentialStream->Release();  
            }  
        }  
    else  
        {  
        // Process error from GetData.  
        }  
  
    pIAccessor->ReleaseAccessor(haccessor, NULL);  
    pIAccessor->Release();  
    delete [] pRow;  
  
    return (hr);  
    }  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [BLOBs und OLE-Objekte](../../relational-databases/native-client-ole-db-blobs/blobs-and-ole-objects.md)   
 [Verwenden von Datentypen mit umfangreichen Werten](../../relational-databases/native-client/features/using-large-value-types.md)  
  
  
