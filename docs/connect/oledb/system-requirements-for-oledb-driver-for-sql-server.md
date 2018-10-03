---
title: Systemanforderungen für den OLE DB-Treiber für SQL Server | Microsoft-Dokumentation
description: Anforderungen für den OLE DB-Treiber für SQL Server
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- system requirements [OLE DB Driver for SQL Server]
- data access [OLE DB Driver for SQL Server], system requirements
- OLE DB Driver for SQL Server, system requirements
- MSOLEDBSQL, system requirements
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: a2ff38f4322209c7ed6eb46a5ba97f360ca3650b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47821028"
---
# <a name="system-requirements-for-ole-db-driver-for-sql-server"></a>Systemanforderungen für den OLE DB-Treiber für SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../includes/driver_oledb_download.md)]

  Um Datenzugriffsfunktionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], wie z. B. MARS, zu verwenden, muss die folgende Software installiert sein:  

-   OLE DB-Treiber für SQL Server auf dem Client.  

-   Eine Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auf Ihrem Server.   

> [!NOTE]  
>  Melden Sie sich vor der Installation dieser Software mit Administratorberechtigungen an.  

## <a name="operating-system-requirements"></a>Betriebssystemanforderungen  
 Eine Liste der Betriebssysteme, die OLE DB-Treiber für SQL Server zu unterstützen, finden Sie unter [für OLE DB-Treiber für SQL Server-Richtlinien unterstützen](../oledb/applications/support-policies-for-oledb-driver-for-sql-server.md).  

## <a name="sql-server-requirements"></a>SQL Server-Anforderungen  
 Verwenden von OLE DB-Treiber für SQL Server für den Datenzugriff in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbanken, benötigen Sie eine Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installiert.  

 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] unterstützt Verbindungen von allen Versionen von MDAC, Windows Data Access Components sowie alle Versionen des OLE DB-Treibers für SQL Server. Wenn eine ältere Clientversion eine Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] herstellt, werden Serverdatentypen, die dem Client nicht bekannt sind, Typen zugeordnet, die mit der Clientversion kompatibel sind. Weitere Informationen finden Sie unter „Datentypkompatibilität für Clientversionen“ später in diesem Thema.  

## <a name="cross-language-requirements"></a>Anforderungen an die sprachübergreifende Unterstützung  
 Die englische Version des OLE DB-Treiber für SQL Server wird unter allen lokalisierten Versionen unterstützter Betriebssysteme unterstützt. Lokalisierte Versionen des OLE DB-Treiber für SQL Server werden auf lokalisierten Betriebssystemen unterstützt, die der Sprache der lokalisierten OLE DB-Treiber für SQL Server-Version sind. Lokalisierte Versionen des OLE DB-Treibers für SQL Server werden auch in englischsprachigen Versionen von unterstützten Betriebssystemen unterstützt, vorausgesetzt die entsprechenden Spracheinstellungen sind installiert.  

 Für Upgrades:  

-   Englische Versionen des OLE DB-Treiber für SQL Server können auf jede lokalisierte Version des OLE DB-Treiber für SQL Server aktualisiert werden.  

-   Lokalisierte Versionen des OLE DB-Treiber für SQL Server können auf lokalisierte Versionen des OLE DB-Treiber für SQL Server mit derselben Sprache aktualisiert werden.  

-   Lokalisierte Version des OLE DB-Treiber für SQL Server kann auf die englischsprachige Version des OLE DB-Treiber für SQL Server aktualisiert werden.  

-   Lokalisierte Versionen des OLE DB-Treiber für SQL Server können nicht auf lokalisierte OLE DB-Treiber für SQL Server-Versionen von einer anderen lokalisierten Sprache aktualisiert werden.  

## <a name="data-type-compatibility-for-client-versions"></a>Datentypkompatibilität für Clientversionen  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und der OLE DB-Treiber für SQL Server ordnen neue Datentypen alten Datentypen zu, die mit Downlevelclients kompatibel sind (siehe folgende Tabelle).  

 OLE DB und ADO-Anwendungen können die **DataTypeCompatibility** Schlüsselwort für Verbindungszeichenfolgen mit OLE DB-Treiber für SQL Server mit älteren Datentypen verwendet werden. Bei **DataTypeCompatibility=80** stellen OLE DB-Clients eine Verbindung mit der [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] TDS-Version (Tabular Data Stream; tabellarischer Datenstrom) anstelle der späteren TDS-Version her. Dies bedeutet, dass für [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]-Datentypen (und höher) eine Downlevelkonvertierung durch den Server vorgenommen wird anstatt durch den OLE DB-Treiber für SQL Server. Darüber hinaus bedeutet dies, dass die auf der Verbindung verfügbaren Funktionen auf den  [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]-Funktionssatz beschränkt sein werden. Der Versuch, neue Datentypen oder Funktionen zu verwenden, wird auf API-Aufrufen so früh wie möglich entdeckt und zur aufrufenden Anwendung zurückgegeben, anstatt dass ein Versuch unternommen wird, ungültige Anforderungen an den Server zu übergeben.   


 IDBInfo:: GetKeywords gibt stets eine Schlüsselwortliste, entspricht der Serverversion für die Verbindung und ist nicht betroffen von **DataTypeCompatibility**.  

|Datentyp|SQL Server Native Client<br /><br />SQL Server 2005|SQL Server Native Client 11.0<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|OLE DB-Treiber für SQL Server|Windows Data Access Components, MDAC und<br /><br /> OLE DB-Treiber für SQL Server-OLE DB-Anwendungen mit DataTypeCompatibility = 80|  
|---------------|--------------------------------------------------|-------------------------------------------------------------|-------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------|  
|CLR UDT (\<= 8 KB)|udt|udt|udt|Varbinary|  
|varbinary(max)|varbinary|varbinary|varbinary|image|  
|varchar(max)|varchar|varchar|varchar|Textmodus|  
|nvarchar(max)|NVARCHAR|NVARCHAR|NVARCHAR|Ntext|  
|xml|xml|xml|xml|Ntext|  
|CLR UDT (> 8Kb)|varbinary|udt|udt|image|  
|date|varchar|date|date|Varchar|  
|datetime2|varchar|datetime2|datetime2|Varchar|  
|datetimeoffset|varchar|datetimeoffset|datetimeoffset|Varchar|  
|Uhrzeit|varchar|Uhrzeit|Uhrzeit|Varchar|  

## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [OLE DB-Treiber für SQL Server](../oledb/oledb-driver-for-sql-server.md)   
 [Installation des OLE DB-Treibers für SQL Server](../oledb/applications/installing-oledb-driver-for-sql-server.md)  
