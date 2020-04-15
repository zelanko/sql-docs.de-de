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
ms.openlocfilehash: d8bb984c789f759eb764ad580f971ab71c9fc946
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81297650"
---
# <a name="data-source-objects-ole-db"></a>Datenquellenobjekte (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client verwendet den Begriff Datenquelle für den Satz von OLE DB-Schnittstellen, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]die zum Herstellen einer Verknüpfung zu einem Datenspeicher verwendet werden, z. B. . Das Erstellen einer Instanz des Datenquellenobjekts des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Anbieters ist die erste Aufgabe eines nativen Client-Verbrauchers.  
  
 Jeder OLE DB-Anbieter deklariert einen Klassenbezeichner (CLSID) für sich. Die CLSID [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] für den nativen Client-OLE-DB-Anbieter ist die C/C++-GUID-CLSID_SQLNCLI10 (das Symbol SQLNCLI_CLSID wird in der Datei sqlncli.h, auf die Sie verweisen, auf das richtige Progid aufgelöst). Mit der CLSID verwendet der Consumer die OLE-Funktion **CoCreateInstance** zum Erstellen einer Instanz des Datenquellenobjekts.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client ist ein in-Process-Server. Instanzen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] von nativen Client-OLE-DB-Anbieterobjekten werden mithilfe des CLSCTX_INPROC_SERVER-Makros erstellt, um den ausführbaren Kontext anzugeben.  
  
 Das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenquellenobjekt des nativen Client-OLE-DB-Anbieters macht die OLE [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] DB-Initialisierungsschnittstellen verfügbar, die es dem Consumer ermöglichen, eine Verbindung mit vorhandenen Datenbanken herzustellen.  
  
 Bei jeder Verbindung, die über den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter hergestellt wird, werden diese Optionen automatisch festgelegt:  
  
-   SET ANSI_WARNINGS ON  
  
-   SET ANSI_NULLS ON  
  
-   SET ANSI_PADDING ON  
  
-   SET ANSI_NULL_DFLT_ON ON  
  
-   SET QUOTED_IDENTIFIER ON  
  
-   SET CONCAT_OF_NULL_YIELDS_NULL ON  
  
 In diesem Beispiel wird das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Klassenbezeichnermakro verwendet, um ein Native Client OLE DB-Anbieter-Datenquellenobjekt zu erstellen und einen Verweis auf die **IDBInitialize-Schnittstelle** abzuverweisen.  
  
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
  
 Nach erfolgreicher Erstellung einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Instanz eines nativen Client-OLE-DB-Anbieter-Datenquellenobjekts kann die Consumeranwendung fortfahren, indem sie die Datenquelle initialisiert und Sitzungen erstellt. OLE DB-Sitzungen präsentieren die Schnittstellen, die Datenzugriff und -bearbeitung ermöglichen.  
  
 Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native Client-OLE-DB-Anbieter stellt seine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] erste Verbindung zu einer angegebenen Instanz von als Teil einer erfolgreichen Datenquelleninitialisierung her. Die Verbindung wird beibehalten, solange eine Referenz auf einer beliebigen Datenquellen-Initialisierungsschnittstelle beibehalten wird oder bis die Methode **IDBInitialize::Uninitialize** aufgerufen wird.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
-   [Datenquelleneigenschaften &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-data-source-objects/data-source-properties-ole-db.md)  
  
-   [Eigenschaften von Datenquelleninformationen](../../relational-databases/native-client-ole-db-data-source-objects/data-source-information-properties.md)  
  
-   [Initialisierungs- und Autorisierungseigenschaften](../../relational-databases/native-client-ole-db-data-source-objects/initialization-and-authorization-properties.md)  
  
-   [Sitzungen](../../relational-databases/native-client-ole-db-data-source-objects/sessions.md)  
  
-   [OLE DB-Anbieter von SQL Server Native Client](../../relational-databases/native-client-ole-db-data-source-objects/session-properties-sql-server-native-client-ole-db-provider.md)  
  
-   [Persistente Datenquellenobjekte](../../relational-databases/native-client-ole-db-data-source-objects/persisted-data-source-objects.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server Native Client &#40;OLE DB&#41;](../../relational-databases/native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
