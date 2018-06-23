---
title: Datenquellenobjekte (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
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
caps.latest.revision: 32
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 9f89825aaca32b542a6788fc9ef849975695f275
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36148358"
---
# <a name="data-source-objects-ole-db"></a>Datenquellenobjekte (OLE DB)
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client verwendet den Begriff-Datenquelle für den Satz von OLE DB-Schnittstellen verwendet, um einen Link zu einem Datenspeicher, z. B. herzustellen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Erstellen einer Instanz von das Datenquellenobjekt des Anbieters ist die erste Aufgabe von einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-Consumers.  
  
 Jeder OLE DB-Anbieter deklariert einen Klassenbezeichner (CLSID) für sich. Die CLSID für den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter ist der C/C++-GUID CLSID_SQLNCLI10 (das Symbol in den richtigen sqlncli_clsid wird progid in der Datei sqlncli.h aufgelöst, die Sie referenzieren). Mit der CLSID verwendet der Consumer die OLE **CoCreateInstance** Funktion zur Herstellung einer Instanz des Datenquellenobjekts.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ist ein in-Process-Server. Instanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter-Objekte werden erstellt, mithilfe des CLSCTX_INPROC_SERVER-Makros zu den ausführbaren Kontext anzugeben.  
  
 Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter-Datenquellenobjekts verfügbar macht, die OLE DB-Initialisierungsschnittstellen bereit, mit denen den Consumer für die Verbindung zu vorhandenen können [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbanken.  
  
 Jede Verbindung, die über die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter legt diese Optionen automatisch fest:  
  
-   SET ANSI_WARNINGS ON  
  
-   SET ANSI_NULLS ON  
  
-   SET ANSI_PADDING ON  
  
-   SET ANSI_NULL_DFLT_ON ON  
  
-   SET QUOTED_IDENTIFIER ON  
  
-   SET CONCAT_OF_NULL_YIELDS_NULL ON  
  
 Dieses Beispiel verwendet das klassenbezeichnermakro zum Erstellen einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter-Datenquellenobjekts, und Abrufen eines Verweises auf die **IDBInitialize** Schnittstelle.  
  
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
  
 Mit der erfolgreichen Erstellung einer Instanz von einem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter-Datenquellenobjekts kann die Consumeranwendung kann fortsetzen, indem die Datenquelle initialisiert und Sitzungen erstellt. OLE DB-Sitzungen präsentieren die Schnittstellen, die Datenzugriff und -bearbeitung ermöglichen.  
  
 Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter stellt die erste Verbindung zu einer angegebenen Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] als Teil einer erfolgreichen datenquelleninitialisierung. Die Verbindung wird beibehalten, solange ein Verweis auf eine beliebige Datenquellen-Initialisierungsschnittstelle oder bis beibehalten wird die **IDBInitialize:: UnInitialize** -Methode aufgerufen wird.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
-   [Datenquelleneigenschaften &#40;OLE DB&#41;](data-source-properties-ole-db.md)  
  
-   [Eigenschaften von Datenquelleninformationen](data-source-information-properties.md)  
  
-   [Initialisierungs- und Autorisierungseigenschaften](initialization-and-authorization-properties.md)  
  
-   [Sitzungen](sessions.md)  
  
-   [Sitzungseigenschaften](session-properties-sql-server-native-client-ole-db-provider.md)  
  
-   [Persistente Datenquellenobjekte](persisted-data-source-objects.md)  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server Native Client &#40;OLE DB&#41;](../native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  