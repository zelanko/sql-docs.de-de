---
title: Unterstützungsrichtlinien des OLE DB-Treibers für SQL Server | Microsoft-Dokumentation
description: Unterstützungsrichtlinien des OLE DB-Treibers für SQL Server
ms.date: 02/12/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.custom: ''
ms.technology: connectivity
ms.topic: reference
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: 790f19d136470458620e0c00de00885e079256bf
ms.sourcegitcommit: 958cffe9288cfe281280544b763c542ca4025684
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 02/23/2019
ms.locfileid: "56744600"
---
# <a name="support-policies-for-ole-db-driver-for-sql-server"></a>Unterstützungsrichtlinien des OLE DB-Treibers für SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Dieser Artikel beschreibt die Verwendung verschiedener Datenzugriffskomponenten mit OLE DB-Treiber für SQL Server verwendet werden können.  

## <a name="server-support"></a>Serverunterstützung  
 OLE DB-Treiber für SQL Server unterstützt Verbindungen mit [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)], [!INCLUDE[ssSQL15](../../../includes/sssql15-md.md)], [!INCLUDE[ssSQL17](../../../includes/sssql17-md.md)], und [!INCLUDE[ssSDSfull](../../../includes/sssdsfull-md.md)].

## <a name="supported-operating-system-versions"></a>Unterstützte Betriebssystemversionen  
 Die folgende Tabelle enthält die Unterstützung von Betriebssystemen OLE DB-Treiber für SQL Server.  

|Unterstützte Betriebssysteme|  
|--------------------------------------|---------------------------------|   
|Microsoft Windows 8.1 und höher [April 2014-update](https://go.microsoft.com/fwlink/?linkid=2073785) + [KB2999226](https://go.microsoft.com/fwlink/?linkid=2074061)<br /><br />Microsoft Windows 10<br /><br /> Microsoft Windows Server 2012 + [KB2999226](https://go.microsoft.com/fwlink/?linkid=2074061)<br /><br />Microsoft Windows Server 2012 R2 + [April 2014-update](https://go.microsoft.com/fwlink/?linkid=2073785) + [KB2999226](https://go.microsoft.com/fwlink/?linkid=2074061)<br /><br />Microsoft Windows Server 2016|  

## <a name="ado-support-policies"></a>Richtlinien zur ADO-Unterstützung  
 ADO-Anwendungen können den zum Lieferumfang von Windows gehörenden SQLOLEDB OLE DB-Anbieter verwenden, sofern sie keine Funktionen von [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] oder höher benötigen.  

 ADO-Anwendungen können den OLE DB-Treiber für SQL Server verwenden, aber wenn sie dies müssen sie angeben `DataTypeCompatibility=80` in den Verbindungszeichenfolgen. Wenn `DataTypeCompatibility=80` in den Verbindungszeichenfolgen angegeben wird, sind nur die Funktionen von [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] verfügbar.  

## <a name="ole-db-support-policies"></a>Richtlinien zur OLE DB-Unterstützung  
Anwendungen können den im Windows-Betriebssystem enthaltenen OLE DB-Anbieter (SQLOLEDB) verwenden. Allerdings, die in den Wartungsmodus versetzt wird und nicht mehr aktualisiert. Stattdessen Sie das OLE DB-Treiber für SQL Server (MSOLEDBSQL).

## <a name="see-also"></a>Siehe auch  
 [Erstellen von Anwendungen mit dem OLE DB-Treiber für SQL Server](../../oledb/applications/building-applications-with-oledb-driver-for-sql-server.md)   
