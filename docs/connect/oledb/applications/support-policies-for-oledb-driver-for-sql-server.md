---
title: Unterstützungsrichtlinien des OLE DB-Treibers für SQL Server
description: Erfahren Sie mehr über die Supportrichtlinien für den OLE DB-Treiber für SQL Server und darüber, welche Betriebssysteme und SQL-Datenbankversionen mit den einzelnen Treiberversionen unterstützt werden.
ms.date: 08/06/2020
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.custom: ''
ms.technology: connectivity
ms.topic: reference
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ca90e20ef6dab5a61bfa6b2969a1220d4a22db2e
ms.sourcegitcommit: c95f3ef5734dec753de09e07752a5d15884125e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88860642"
---
# <a name="support-policies-for-ole-db-driver-for-sql-server"></a>Unterstützungsrichtlinien des OLE DB-Treibers für SQL Server
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

In diesem Artikel wird die Verwendung verschiedener Datenzugriffskomponenten mit dem OLE DB-Treiber für SQL Server erläutert.  

## <a name="sql-version-support"></a>SQL-Versionsunterstützung  

Der OLE DB-Treiber für SQL Server wird mitgetestet und unterstützt Verbindungen mit den folgenden Versionen von SQL Server.

| Datenbankversion&nbsp;&#8594;<br />&#8595; Treiberversion | Azure SQL-Datenbank | Azure Synapse Analytics | Verwaltete Azure SQL-Instanz | SQL Server 2019 | SQL Server 2017 | SQL Server 2016 | SQL Server 2014 | SQL Server 2012 |
|----|---|---|---|---|---|---|---|---|
|18.4|Ja|Ja|Ja|Ja|Ja|Ja|Ja|Ja|
|18.3|Ja|Ja|Ja|Ja|Ja|Ja|Ja|Ja|
|18.2|Ja|Ja|Ja|Ja|Ja|Ja|Ja|Ja|
|18.1|Ja|Ja|Ja|   |Ja|Ja|Ja|Ja|
|18.0|Ja|Ja|Ja|   |Ja|Ja|Ja|Ja|
| &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; |

## <a name="supported-operating-system-versions"></a>Unterstützte Betriebssystemversionen  

In der folgenden Tabelle werden die Betriebssysteme aufgeführt, die vom OLE DB-Treiber für SQL Server unterstützt werden.  

| Betriebssystem&nbsp;&#8594;<br />&#8595; Treiberversion | Windows Server 2019 | Windows Server 2016 | Windows Server 2012<sup>1</sup> | Windows Server 2012 R2<sup>2</sup> | Windows 10 | Windows 8.1<sup>3</sup> |
|----|---|---|---|---|---|---|
|18.4|Ja|Ja|Ja|Ja|Ja|Ja|
|18.3|Ja|Ja|Ja|Ja|Ja|Ja|
|18.2|Ja|Ja|Ja|Ja|Ja|Ja|
|18.1|   |Ja|Ja|Ja|Ja|Ja|
|18.0|   |Ja|Ja|Ja|Ja|Ja|
| &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; |

<sup>1</sup> unterstützt unter Windows Server 2012 mit [KB2999226](https://go.microsoft.com/fwlink/?linkid=2074061)  
<sup>2</sup> unterstützt unter Windows Server 2012 R2 mit dem [Update vom April 2014](https://go.microsoft.com/fwlink/?linkid=2073785) und [KB2999226](https://go.microsoft.com/fwlink/?linkid=2074061)  
<sup>3</sup> unterstützt unter Windows 8.1 mit dem [Update vom April 2014](https://go.microsoft.com/fwlink/?linkid=2073785) und [KB2999226](https://go.microsoft.com/fwlink/?linkid=2074061)  

## <a name="ado-support-policies"></a>Richtlinien zur ADO-Unterstützung  

ADO-Anwendungen können den zum Lieferumfang von Windows gehörenden SQLOLEDB OLE DB-Anbieter verwenden, sofern sie keine Funktionen von [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] oder höher benötigen.  

ADO-Anwendungen können den OLE DB-Treiber für SQL Server verwenden, müssen in diesem Fall allerdings in den Verbindungszeichenfolgen `DataTypeCompatibility=80` angeben. Wenn `DataTypeCompatibility=80` in den Verbindungszeichenfolgen angegeben wird, sind nur die Funktionen von [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] verfügbar.  

## <a name="ole-db-support-policies"></a>Richtlinien zur OLE DB-Unterstützung  

Anwendungen können den im Windows-Betriebssystem enthaltenen OLE DB-Anbieter (SQLOLEDB) verwenden. Dieser befindet sich allerdings im Wartungsmodus und wird nicht mehr aktualisiert. Verwenden Sie stattdessen den Microsoft OLE DB-Treiber für SQL Server (MSOLEDBSQL).

## <a name="see-also"></a>Weitere Informationen  

[Erstellen von Anwendungen mit dem OLE DB-Treiber für SQL Server](../../oledb/applications/building-applications-with-oledb-driver-for-sql-server.md)
