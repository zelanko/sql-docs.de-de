---
title: Unterstützungsrichtlinien des OLE DB-Treibers für SQL Server | Microsoft-Dokumentation
description: Unterstützungsrichtlinien des OLE DB-Treibers für SQL Server
ms.date: 05/25/2020
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.custom: ''
ms.technology: connectivity
ms.topic: reference
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 7e4b77a700d494f1ed8f11a0004c60b37c5cc361
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/06/2020
ms.locfileid: "86007042"
---
# <a name="support-policies-for-ole-db-driver-for-sql-server"></a>Unterstützungsrichtlinien des OLE DB-Treibers für SQL Server
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

In diesem Artikel wird die Verwendung verschiedener Datenzugriffskomponenten mit dem OLE DB-Treiber für SQL Server erläutert.  

## <a name="sql-version-support"></a>SQL-Versionsunterstützung  

Der OLE DB-Treiber für SQL Server wird mitgetestet und unterstützt Verbindungen mit den folgenden Versionen von SQL Server.

| Treiberversion | Azure SQL-Datenbank | Azure SQL DW | Verwaltete Azure SQL-Instanz | SQL Server 2019 | SQL Server 2017 | SQL Server 2016 | SQL Server 2014 | SQL Server 2012 |
|----|-|-|-|-|-|-|-|-|
|18.4|J|J|J|J|J|J|J|J|
|18.3|J|J|J|J|J|J|J|J|
|18.2|J|J|J|J|J|J|J|J|
|18.1|J|J|J| |J|J|J|J|
|18.0|J|J|J| |J|J|J|J|
| &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; |

## <a name="supported-operating-system-versions"></a>Unterstützte Betriebssystemversionen  

In der folgenden Tabelle werden die Betriebssysteme aufgeführt, die vom OLE DB-Treiber für SQL Server unterstützt werden.  

| Treiberversion | Windows Server 2019 | Windows Server 2016 | Windows Server 2012<sup>1</sup> | Windows Server 2012 R2<sup>2</sup> | Windows 10 | Windows 8.1<sup>3</sup> |
|----|-|-|-|-|-|-|
|18.4|J|J|J|J|J|J|
|18.3|J|J|J|J|J|J|
|18.2|J|J|J|J|J|J|
|18.1| |J|J|J|J|J|
|18.0| |J|J|J|J|J|
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
