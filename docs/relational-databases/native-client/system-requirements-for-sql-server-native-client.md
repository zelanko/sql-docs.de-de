---
title: Systemanforderungen für SQL Server Native Client | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- system requirements [SQL Server Native Client]
- data access [SQL Server Native Client], system requirements
- SQL Server Native Client, system requirements
- SQLNCLI, system requirements
ms.assetid: 1c8e2f8a-a440-44da-8e3a-af632d34c52c
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: bdf5d2de1c465300be803386e75acecfb61db93b
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305038"
---
# <a name="system-requirements-for-sql-server-native-client"></a>Systemanforderungen für SQL Server Native Client
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Um Datenzugriffsfunktionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], wie z. B. MARS, zu verwenden, muss die folgende Software installiert sein:  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client auf Ihrem Client.  
  
-   Eine Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auf Ihrem Server.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client erfordert Windows Installer 3.0. Windows Installer 3.0 ist bereits auf [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Betriebssystemen installiert. Für alle anderen Plattformen müssen Sie es explizit installieren. Weitere Informationen finden Sie unter [Windows Installer 3.0 Redistributable](https://www.microsoft.com/download/details.aspx?id=16821).  
  
> [!NOTE]  
>  Melden Sie sich vor der Installation dieser Software mit Administratorberechtigungen an.  
  
## <a name="operating-system-requirements"></a>Betriebssystemanforderungen  
 Eine Liste der Betriebssysteme, die Native Client unterstützen, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] finden Sie unter [Supportrichtlinien für SQL Server Native Client](../../relational-databases/native-client/applications/support-policies-for-sql-server-native-client.md).  
  
## <a name="sql-server-requirements"></a>SQL Server-Anforderungen  
 Um mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client auf Daten in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbanken zugreifen zu können, muss eine Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installiert sein.  
  
 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] unterstützt Verbindungen von allen Versionen von MDAC, Windows Data Access Components und alle Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client. Wenn eine ältere Clientversion eine Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] herstellt, werden Serverdatentypen, die dem Client nicht bekannt sind, Typen zugeordnet, die mit der Clientversion kompatibel sind. Weitere Informationen finden Sie unter „Datentypkompatibilität für Clientversionen“ später in diesem Thema.  
  
## <a name="cross-language-requirements"></a>Anforderungen an die sprachübergreifende Unterstützung  
 Die englische Sprachversion von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client wird von allen lokalisierten Versionen unterstützter Betriebssysteme unterstützt. Lokalisierte Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client werden von lokalisierten Betriebssystemen unterstützt, deren Sprache der lokalisierten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-Version entspricht. Lokalisierte Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client werden auch auf englischsprachigen Versionen von unterstützten Betriebssystemen unterstützt, vorausgesetzt die entsprechenden Spracheinstellungen sind installiert.  
  
 Für Upgrades:  
  
-   Englischsprachige Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client können auf jede lokalisierte Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] aktualisiert werden.  
  
-   Lokalisierte Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client können auf lokalisierte Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client der gleichen Sprache aktualisiert werden.  
  
-   Lokalisierte Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client können auf die englischsprachige Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client aktualisiert werden.  
  
-   Lokalisierte Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client können nicht auf eine lokalisierte Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client einer anderen Sprache aktualisiert werden.  
  
## <a name="data-type-compatibility-for-client-versions"></a>Datentypkompatibilität für Clientversionen  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ordnen neue Datentypen alten Datentypen zu, die mit Downlevelclients kompatibel sind (siehe folgende Tabelle).  
  
 OLE DB- und ADO-Anwendungen können das **DataTypeCompatibility-Verbindungszeichenfolgenschlüsselwort** mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client verwenden, um mit älteren Datentypen zu arbeiten. Bei **DataTypeCompatibility=80** stellen OLE DB-Clients eine Verbindung mit der [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] TDS-Version (Tabular Data Stream; tabellarischer Datenstrom) anstelle der späteren TDS-Version her. Dies bedeutet, dass für [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]-Datentypen (und höher) eine Downlevelkonvertierung durch den Server vorgenommen wird anstatt von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client. Darüber hinaus bedeutet dies, dass die auf der Verbindung verfügbaren Funktionen auf den  [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]-Funktionssatz beschränkt sein werden. Der Versuch, neue Datentypen oder Funktionen zu verwenden, wird auf API-Aufrufen so früh wie möglich entdeckt und zur aufrufenden Anwendung zurückgegeben, anstatt dass ein Versuch unternommen wird, ungültige Anforderungen an den Server zu übergeben.  
  
 Es gibt kein **DataTypeCompatibility-Steuerelement** für ODBC.  
  
 IDBInfo::GetKeywords wird immer eine Liste mit Schlüsselwörtern zurückgeben, die der Serverversion auf der Verbindung entspricht und nicht von **DataTypeCompatibility** beeinträchtigt wird.  
  
|Datentyp|SQL Server Native Client<br /><br /> SQL Server 2005|SQL Server Native Client 11.0<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|Windows Data Access Components, MDAC und<br /><br /> SQL Server Native Client OLE DB-Anwendungen mit DataTypeCompatibility=80|  
|---------------|--------------------------------------------------|-------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------|  
|CLR UDT (\<= 8 KB)|udt|Udt|Varbinary|  
|varbinary(max)|varbinary|varbinary|Image|  
|varchar(max)|varchar|varchar|Text|  
|nvarchar(max)|NVARCHAR|NVARCHAR|Ntext|  
|Xml|Xml|Xml|Ntext|  
|CLR UDT (> 8 KB)|udt|varbinary|Image|  
|date|date|varchar|Varchar|  
|datetime2|datetime2|varchar|Varchar|  
|datetimeoffset|datetimeoffset|varchar|Varchar|  
|time|time|varchar|Varchar|  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server Native Client-Programmierung](../../relational-databases/native-client/sql-server-native-client-programming.md)   
 [Installieren von SQL Server Native Client](../../relational-databases/native-client/applications/installing-sql-server-native-client.md)  
  
  
