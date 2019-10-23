---
title: Unterstützungsrichtlinien des OLE DB-Treibers für SQL Server | Microsoft-Dokumentation
description: Unterstützungsrichtlinien des OLE DB-Treibers für SQL Server
ms.date: 10/11/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.custom: ''
ms.technology: connectivity
ms.topic: reference
author: pmasl
ms.author: pelopes
ms.openlocfilehash: b02789c787266a3370e3c5c9bfae50ea337d19db
ms.sourcegitcommit: 4c75b49599018124f05f91c1df3271d473827e4d
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72381858"
---
# <a name="support-policies-for-ole-db-driver-for-sql-server"></a>Unterstützungsrichtlinien des OLE DB-Treibers für SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  In diesem Artikel wird erläutert, wie verschiedene Datenzugriffs Komponenten mit OLE DB Treiber für SQL Server verwendet werden können.  

## <a name="server-support"></a>Serverunterstützung  
 OLE DB Treiber für SQL Server unterstützt Verbindungen mit [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] über [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] und [!INCLUDE[ssSDSfull](../../../includes/sssdsfull-md.md)].

## <a name="supported-operating-system-versions"></a>Unterstützte Betriebssystemversionen  
 In der folgenden Tabelle ist aufgeführt, welche Betriebssysteme OLE DB Treiber für SQL Server unterstützen.  

| Unterstützte Betriebssysteme |  |
|--------------------------------------|---------------------------------|   
| Microsoft Windows 8.1 + [April 2014 Update](https://go.microsoft.com/fwlink/?linkid=2073785)  + [KB2999226](https://go.microsoft.com/fwlink/?linkid=2074061)<br /><br />Microsoft Windows 10<br /><br /> Microsoft Windows Server 2012 + [KB2999226](https://go.microsoft.com/fwlink/?linkid=2074061)<br /><br />Microsoft Windows Server 2012 R2 + [April 2014 Update](https://go.microsoft.com/fwlink/?linkid=2073785)  + [KB2999226](https://go.microsoft.com/fwlink/?linkid=2074061)<br /><br />Microsoft Windows Server 2016<br /><br />Microsoft Windows Server 2019 |  |


## <a name="ado-support-policies"></a>Richtlinien zur ADO-Unterstützung  
 ADO-Anwendungen können den zum Lieferumfang von Windows gehörenden SQLOLEDB OLE DB-Anbieter verwenden, sofern sie keine Funktionen von [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] oder höher benötigen.  

 ADO-Anwendungen können den OLE DB Treiber für SQL Server verwenden, aber wenn dies der Fall ist, müssen Sie `DataTypeCompatibility=80` in den Verbindungs Zeichenfolgen angeben. Wenn `DataTypeCompatibility=80` in den Verbindungszeichenfolgen angegeben wird, sind nur die Funktionen von [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] verfügbar.  

## <a name="ole-db-support-policies"></a>Richtlinien zur OLE DB-Unterstützung  
Anwendungen können den im Windows-Betriebssystem enthaltenen OLE DB-Anbieter (SQLOLEDB) verwenden. Dies befindet sich jedoch im Wartungsmodus und wird nicht mehr aktualisiert. Verwenden Sie stattdessen den OLE DB Treiber für SQL Server (msoledbsql).

## <a name="see-also"></a>Siehe auch  
 [Erstellen von Anwendungen mit dem OLE DB-Treiber für SQL Server](../../oledb/applications/building-applications-with-oledb-driver-for-sql-server.md)   
