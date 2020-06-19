---
title: Datenquellenobjekte (OLE DB) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
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
author: rothja
ms.author: jroth
ms.openlocfilehash: ec5479d3b1e4ee1e828ba1c43cd86ce5e42b6497
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85043894"
---
# <a name="data-source-objects-ole-db"></a>Datenquellenobjekte (OLE DB)
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
  
-   [Datenquelleneigenschaften &#40;OLE DB&#41;](data-source-properties-ole-db.md)  
  
-   [Eigenschaften von Datenquelleninformationen](data-source-information-properties.md)  
  
-   [Initialisierungs- und Autorisierungseigenschaften](initialization-and-authorization-properties.md)  
  
-   [Sitzungen](sessions.md)  
  
-   [Sitzungseigenschaften](session-properties-sql-server-native-client-ole-db-provider.md)  
  
-   [Persistente Datenquellenobjekte](persisted-data-source-objects.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server Native Client &#40;OLE DB&#41;](../native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
