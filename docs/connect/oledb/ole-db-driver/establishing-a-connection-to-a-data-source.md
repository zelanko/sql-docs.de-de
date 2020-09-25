---
title: Herstellen einer Verbindung zu einer Datenquelle (OLE DB-Treiber) | Microsoft-Dokumentation
description: Erfahren Sie, wie ein Verbraucher mithilfe des Microsoft OLE DB-Treibers für SQL Server eine Verbindung zu einer Datenquelle herstellt.
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- data sources [OLE DB Driver for SQL Server]
- connections [OLE DB Driver for SQL Server]
- OLE DB Driver for SQL Server, data source connections
- CoCreateInstance method
- OLE DB data sources [OLE DB Driver for SQL Server]
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0d842bcee76fa989d8212d3c377c25c1f86f2491
ms.sourcegitcommit: c95f3ef5734dec753de09e07752a5d15884125e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88861545"
---
# <a name="establishing-a-connection-to-a-data-source"></a>Herstellen einer Verbindung zu einer Datenquelle
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Der Consumer muss zum Zugreifen auf den OLE DB-Treiber für SQL Server zunächst eine Instanz eines Datenquellenobjekts erstellen, indem er die **CoCreateInstance**-Methode aufruft. Ein eindeutiger Klassenbezeichner (CLSID) identifiziert jeden OLE DB-Anbieter. Die Klassen-ID für den OLE DB-Treiber für SQL Server ist CLSID_MSOLEDBSQL. Sie können auch das Symbol MSOLEDBSQL_CLSID verwenden, das in den OLE DB-Treiber für SQL Server aufgelöst wird, der in der msoledbsql.h-Datei verwendet wird, auf die Sie verweisen.  
  
 Das Datenquellenobjekt macht die **IDBProperties**-Schnittstelle verfügbar, die der Consumer verwendet, um grundlegende Authentifizierungsinformationen wie Servername, Datenbankname, Benutzer-ID und Kennwort bereitzustellen. Die **IDBProperties::SetProperties**-Methode wird aufgerufen, um diese Eigenschaften festzulegen.  
  
 Wenn mehrere Instanzen von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] auf dem Computer ausgeführt werden, wird der Servername als ServerName\InstanceName angegeben.  
  
 Das Datenquellenobjekt macht auch die **IDBInitialize**-Schnittstelle verfügbar. Nachdem die Eigenschaften festgelegt wurden, wird die Verbindung zur Datenquelle durch Aufrufen der **IDBInitialize::Initialize**-Methode hergestellt. Beispiel:  
  
```cpp
CoCreateInstance(CLSID_MSOLEDBSQL,   
                 NULL,   
                 CLSCTX_INPROC_SERVER,  
                 IID_IDBInitialize,   
                 (void **) &pIDBInitialize)  
```
  
 Durch diesen Aufruf von **CoCreateInstance** wird ein einzelnes Objekt der Klasse erstellt, die CLSID_MSOLEDBSQL zugeordnet ist (CSLID ist den Daten und dem Code zugeordnet, die zur Objekterstellung verwendet werden). IID_IDBInitialize ist ein Verweis auf den Bezeichner der Schnittstelle (**IDBInitialize**), die zur Kommunikation mit dem Objekt verwendet werden soll.  
  
 Im folgenden Beispiel sehen Sie, wie Sie eine Verbindung zur Datenquelle initialisieren und herstellen.
  
```cpp
#include "msoledbsql.h"
#include <stdio.h>

HRESULT InitializeAndEstablishConnection(IDBInitialize *&pIDBInitialize);

void main() {
    IDBInitialize       *pIDBInitialize = nullptr;
    HRESULT             hr = S_OK;

    // Initialize The Component Object Module Library
    CoInitialize(nullptr);

    hr = InitializeAndEstablishConnection(pIDBInitialize);
    if (FAILED(hr)) {
        printf("Failed to establish connection.\r\n");
        goto _ExitMain;
    }

    // Insert code that uses the established connection

_ExitMain:
    // Free Up All Allocated Memory
    if (pIDBInitialize)
    {
        pIDBInitialize->Uninitialize();
        pIDBInitialize->Release();
        pIDBInitialize = nullptr;
    }

    // Release The Component Object Module Library
    CoUninitialize();
}

HRESULT InitializeAndEstablishConnection(IDBInitialize *&pIDBInitialize) {
    IDBProperties   *pIDBProperties = nullptr;
    DBPROP          InitProperties[3] = { 0 };
    DBPROPSET       rgInitPropSet[1] = { 0 };
    HRESULT         hr = S_OK;

    // Obtain access to the OLE DB Driver for SQL Server.  
    hr = CoCreateInstance(CLSID_MSOLEDBSQL,
                          NULL,
                          CLSCTX_INPROC_SERVER,
                          IID_IDBInitialize,
                          (void **)&pIDBInitialize);
    if (FAILED(hr)) {
        printf("Failed to obtain access to the OLE DB Driver.\r\n");
        goto _ExitInitialize;
    }
    // Initialize property values needed to establish connection.  
    for (int i = 0; i < 3; i++) {
        VariantInit(&InitProperties[i].vValue);
    }

    // Server name.  
    // See DBPROP structure for more information on InitProperties  
    InitProperties[0].dwPropertyID = DBPROP_INIT_DATASOURCE;
    InitProperties[0].vValue.vt = VT_BSTR;
    InitProperties[0].vValue.bstrVal = SysAllocString(L"Server");
    InitProperties[0].dwOptions = DBPROPOPTIONS_REQUIRED;
    InitProperties[0].colid = DB_NULLID;

    // Database.  
    InitProperties[1].dwPropertyID = DBPROP_INIT_CATALOG;
    InitProperties[1].vValue.vt = VT_BSTR;
    InitProperties[1].vValue.bstrVal = SysAllocString(L"database");
    InitProperties[1].dwOptions = DBPROPOPTIONS_REQUIRED;
    InitProperties[1].colid = DB_NULLID;

    // Username (login).  
    InitProperties[2].dwPropertyID = DBPROP_AUTH_INTEGRATED;
    InitProperties[2].vValue.vt = VT_BSTR;
    InitProperties[2].vValue.bstrVal = SysAllocString(L"SSPI");
    InitProperties[2].dwOptions = DBPROPOPTIONS_REQUIRED;
    InitProperties[2].colid = DB_NULLID;

    // Construct the DBPROPSET structure(rgInitPropSet). The   
    // DBPROPSET structure is used to pass an array of DBPROP   
    // structures (InitProperties) to the SetProperties method.  
    rgInitPropSet[0].guidPropertySet = DBPROPSET_DBINIT;
    rgInitPropSet[0].cProperties = 3;
    rgInitPropSet[0].rgProperties = InitProperties;

    // Set initialization properties.  
    hr = pIDBInitialize->QueryInterface(IID_IDBProperties,
                                        (void **)&pIDBProperties);
    if (FAILED(hr)) {
        printf("Failed to obtain an IDBProperties interface.\r\n");
        goto _ExitInitialize;
    }
    hr = pIDBProperties->SetProperties(1, rgInitPropSet);
    if (FAILED(hr)) {
        printf("Failed to set initialization properties.\r\n");
        goto _ExitInitialize;
    }

    // Now establish the connection to the data source.  
    hr = pIDBInitialize->Initialize();
    if (FAILED(hr)) {
        printf("Failed to establish connection with the server.\r\n");
        goto _ExitInitialize;
    }

_ExitInitialize:
    if (pIDBProperties)
    {
        pIDBProperties->Release();
        pIDBProperties = nullptr;
    }

    if (FAILED(hr))
    {
        if (pIDBInitialize)
        {
            pIDBInitialize->Release();
            pIDBInitialize = nullptr;
        }
    }

    return hr;
}
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen eines OLE DB-Treibers für eine SQL Server-Anwendung](../../oledb/ole-db-driver/creating-a-oledb-driver-for-sql-server-application.md)  
  
  
