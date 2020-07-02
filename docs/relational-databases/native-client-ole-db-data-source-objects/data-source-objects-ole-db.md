---
title: Datenquellenobjekte (OLE DB) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- data access [SQL Server Native Client], data source objects
- SQL Server Native Client, data source objects
- SQLNCLI, data source objects
- SQL Server Native Client OLE DB provider, data source objects
- OLE DB data source objects [SQL Server Native Client]
- data source objects [OLE DB]
- CLSID
ms.assetid: c1d4ed20-ad3b-4e33-a26b-38d7517237b7
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: e4190b13819bddc6a4bdc40d2eae4e09f1a98e7a
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85715275"
---
# <a name="data-source-objects-ole-db"></a>Datenquellenobjekte (OLE DB)
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asdw-pdw.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client verwendet den Begriff Datenquelle für den Satz von OLE DB Schnittstellen, die zum Herstellen einer Verknüpfung mit einem Datenspeicher verwendet werden, z [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . b.. Das Erstellen einer Instanz des Datenquellen Objekts des Anbieters ist die erste Aufgabe eines [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client Consumers.  
  
 Jeder OLE DB-Anbieter deklariert einen Klassenbezeichner (CLSID) für sich. Die CLSID für den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter ist die C/C++-GUID CLSID_SQLNCLI10 (das Symbol SQLNCLI_CLSID wird in die korrekte ProgID in der Datei sqlncli. h aufgelöst, auf die Sie verweisen). Mit der CLSID verwendet der Consumer die OLE-Funktion **CoCreateInstance** zum Erstellen einer Instanz des Datenquellenobjekts.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client ist ein in-Process-Server. Instanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter Objekten werden mithilfe des CLSCTX_INPROC_SERVER-Makros erstellt, um den ausführbaren Kontext anzugeben.  
  
 Das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenquellen Objekt des Native Client OLE DB-Anbieters macht die OLE DB Initialisierungs Schnittstellen verfügbar, die es dem Consumer ermöglichen, eine Verbindung mit vorhandenen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbanken herzustellen.  
  
 Jede Verbindung, die über den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter hergestellt wird, legt diese Optionen automatisch fest:  
  
-   SET ANSI_WARNINGS ON  
  
-   SET ANSI_NULLS ON  
  
-   SET ANSI_PADDING ON  
  
-   SET ANSI_NULL_DFLT_ON ON  
  
-   SET QUOTED_IDENTIFIER ON  
  
-   SET CONCAT_OF_NULL_YIELDS_NULL ON  
  
 In diesem Beispiel wird das Klassenbezeichnermakro verwendet, um ein [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenquellen Objekt des Native Client OLE DB-Anbieters zu erstellen und einen Verweis auf seine **IDBInitialize** -Schnittstelle zu erhalten  
  
```  
IDBInitialize*   pIDBInitialize;  
HRESULT          hr;  
  
hr = CoCreateInstance(CLSID_SQLNCLI10, NULL, CLSCTX_INPROC_SERVER,  
    IID_IDBInitialize, (void**) &pIDBInitialize);  
  
if (SUCCEEDED(hr))  
{  
    //  Perform necessary processing with the interface.  
    pIDBInitialize->Uninitialize();  
    pIDBInitialize->Release();  
}  
else  
{  
    // Display error from CoCreateInstance.  
}  
```  
  
 Bei erfolgreicher Erstellung einer Instanz eines [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenquellen Objekts des Native Client OLE DB Anbieters kann die Consumeranwendung fortgesetzt werden, indem die Datenquelle initialisiert und Sitzungen erstellt werden. OLE DB-Sitzungen präsentieren die Schnittstellen, die Datenzugriff und -bearbeitung ermöglichen.  
  
 Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter stellt die erste Verbindung zu einer angegebenen Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] als Teil einer erfolgreichen Datenquellen Initialisierung her. Die Verbindung wird beibehalten, solange eine Referenz auf einer beliebigen Datenquellen-Initialisierungsschnittstelle beibehalten wird oder bis die Methode **IDBInitialize::Uninitialize** aufgerufen wird.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
-   [Datenquelleneigenschaften &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-data-source-objects/data-source-properties-ole-db.md)  
  
-   [Eigenschaften von Datenquelleninformationen](../../relational-databases/native-client-ole-db-data-source-objects/data-source-information-properties.md)  
  
-   [Initialisierungs- und Autorisierungseigenschaften](../../relational-databases/native-client-ole-db-data-source-objects/initialization-and-authorization-properties.md)  
  
-   [Sitzungen](../../relational-databases/native-client-ole-db-data-source-objects/sessions.md)  
  
-   [OLE DB-Anbieter von SQL Server Native Client](../../relational-databases/native-client-ole-db-data-source-objects/session-properties-sql-server-native-client-ole-db-provider.md)  
  
-   [Persistente Datenquellenobjekte](../../relational-databases/native-client-ole-db-data-source-objects/persisted-data-source-objects.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server Native Client &#40;OLE DB&#41;](../../relational-databases/native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
