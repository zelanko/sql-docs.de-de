---
title: Integrierte Kerberos-Authentifizierung (OLE DB-Treiber) | Microsoft-Dokumentation
description: Erfahren Sie in diesem Beispiel, wie Sie mithilfe von OLE DB im OLE DB-Treiber für SQL Server die gegenseitige Kerberos-Authentifizierung einrichten.
ms.custom: ''
ms.date: 09/30/2020
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e7ba7469d01b75397f706df403041ec68c1ed5f9
ms.sourcegitcommit: 0e0cd9347c029e0c7c9f3fe6d39985a6d3af967d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2020
ms.locfileid: "96506374"
---
# <a name="integrated-kerberos-authentication-ole-db"></a>Integrierte Kerberos-Authentifizierung (OLE DB)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Dieses Beispiel zeigt, wie Sie mithilfe von OLE DB im OLE DB-Treiber für SQL Server die gegenseitige Kerberos-Authentifizierung einrichten. Dieses Beispiel wird mit [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] oder höher ausgeführt.  
  
 Weitere Informationen zu SPNs und Kerberos-Authentifizierung finden Sie unter [Service Principal Name &#40;SPN&#41; Support in Client Connections (Unterstützung von Dienstprinzipalnamen in Clientverbindungen)](../../oledb/features/service-principal-name-spn-support-in-client-connections.md).  
  
## <a name="example"></a>Beispiel  
 Sie müssen einen Server angeben. Ändern Sie in der CPP-Datei „MyServer“ in den Namen eines Computers, auf dem sich eine Instanz von [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] (oder höher) befindet.  
  
 Sie müssen auch einen vom Kunden bereitgestellten SPN angeben. Ändern Sie in der CPP-Datei "CPSPN" in einen vom Kunden bereitgestellten SPN.  
  
 Stellen Sie sicher, dass die INCLUDE-Umgebungsvariable das Verzeichnis einschließt, das „msoledbsql.h“ enthält. Kompilieren Sie mit ole32.lib und oleaut32.lib.  
  
```cpp
// compile with: ole32.lib oleaut32.lib
#pragma once

#define WIN32_LEAN_AND_MEAN   // Exclude rarely-used stuff from Windows headers
#include <stdio.h>
#include <tchar.h>
#include <msoledbsql.h>

#define CHECKHR(stmt) \
do\
{\
    hr = (stmt);\
    if (FAILED(hr))\
    {\
       printf("CHECK_HR " #stmt " failed at (%hs, %d), hr=0x%08X\r\n", __FILE__, __LINE__, hr); \
       goto CleanUp; \
    } \
} while (0)

#define SAFERELEASE(p) \
do\
{\
    if ((p) != nullptr)\
    {\
       p->Release(); \
       p = nullptr; \
    } \
} while (0)


int _tmain(int argc, _TCHAR* argv[])
{
    HRESULT hr = S_OK;
    IDBInitialize* pInitialize = nullptr;
    IDBProperties* pProperties = nullptr;
    DBPROP rgDBProp[1] = {};
    LPCWSTR lpwszProviderString = L"Server=MyServer;"   // server with SQL Server 2008 (or later)
       L"Trusted_Connection=Yes;"
       L"Encrypt=yes;"
       L"ServerSPN=CP_SPN;";   // customer-provided SPN

    DBPROPSET* prgPropertySets = nullptr;
    ULONG cPropertySets = 0;

    CHECKHR(CoInitialize(nullptr));
    CHECKHR(CoCreateInstance(CLSID_MSOLEDBSQL, nullptr, CLSCTX_INPROC_SERVER, __uuidof(IDBProperties), reinterpret_cast<void**>(&pProperties)));

    // set provider string
    rgDBProp[0].dwPropertyID = DBPROP_INIT_PROVIDERSTRING;
    rgDBProp[0].dwOptions = DBPROPOPTIONS_REQUIRED;
    rgDBProp[0].colid = DB_NULLID;
    VariantInit(&(rgDBProp[0].vValue));
    V_VT(&(rgDBProp[0].vValue)) = VT_BSTR;
    V_BSTR(&(rgDBProp[0].vValue)) = SysAllocString(lpwszProviderString);

    { // set the property to the property set
        DBPROPSET PropertySet[1] = {};
        PropertySet[0].rgProperties = &rgDBProp[0];
        PropertySet[0].cProperties = 1;
        PropertySet[0].guidPropertySet = DBPROPSET_DBINIT;

        // set properties and connect to server
        CHECKHR(pProperties->SetProperties(sizeof(PropertySet)/sizeof(DBPROPSET), PropertySet));
    }

    CHECKHR(pProperties->QueryInterface<IDBInitialize>(&pInitialize));
    CHECKHR(pInitialize->Initialize());

    { // get properties
        DBPROPIDSET rgDBPropIDSet[1] = {};

        DBPROPID rgDBPropID[2] = {};
        rgDBPropID[0] = SSPROP_INTEGRATEDAUTHENTICATIONMETHOD;
        rgDBPropID[1] = SSPROP_MUTUALLYAUTHENTICATED;

        rgDBPropIDSet[0].rgPropertyIDs = &rgDBPropID[0];
        rgDBPropIDSet[0].cPropertyIDs = 2;
        rgDBPropIDSet[0].guidPropertySet = DBPROPSET_SQLSERVERDATASOURCEINFO;
        CHECKHR(pProperties->GetProperties(1, rgDBPropIDSet, &cPropertySets, &prgPropertySets));
    }
    wprintf(L"Authentication method: %s\r\n", V_BSTR(&(prgPropertySets[0].rgProperties[0].vValue)));
    wprintf(L"Mutually authenticated: %s\r\n",
        (V_BOOL(&(prgPropertySets[0].rgProperties[1].vValue)) == VARIANT_TRUE) ? L"yes" : L"no");

CleanUp:
    SAFERELEASE(pProperties);
    SAFERELEASE(pInitialize);

    if (prgPropertySets)
    {
        for (ULONG iPropSet = 0; iPropSet < cPropertySets; ++iPropSet)
        {
            for (ULONG iProp = 0; iProp < prgPropertySets[iPropSet].cProperties; ++iProp)
            {
                VariantClear(&prgPropertySets[iPropSet].rgProperties[iProp].vValue);
            }
        }
    }

    VariantClear(&(rgDBProp[0].vValue));
    CoUninitialize();
}
```