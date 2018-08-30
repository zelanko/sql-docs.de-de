---
title: Unterstützungsrichtlinien des OLE DB-Treibers für SQL Server | Microsoft-Dokumentation
description: Unterstützungsrichtlinien des OLE DB-Treibers für SQL Server
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|applications
ms.reviewer: ''
ms.suite: sql
ms.custom: ''
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: 6d71a4944aaf4fe15ba76c4d831f4809f5278f83
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "43021743"
---
# <a name="support-policies-for-ole-db-driver-for-sql-server"></a>Unterstützungsrichtlinien des OLE DB-Treibers für SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Dieser Artikel beschreibt die Verwendung verschiedener Datenzugriffskomponenten mit OLE DB-Treiber für SQL Server verwendet werden können.  

## <a name="server-support"></a>Serverunterstützung  
 OLE DB-Treiber für SQL Server unterstützt Verbindungen mit [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)],[!INCLUDE[ssSQL15](../../../includes/sssql15-md.md)], [!INCLUDE[ssSQL17](../../../includes/sssql17-md.md)], und [!INCLUDE[ssSDSfull](../../../includes/sssdsfull-md.md)].

## <a name="supported-operating-system-versions"></a>Unterstützte Betriebssystemversionen  
 Die folgende Tabelle enthält die Unterstützung von Betriebssystemen OLE DB-Treiber für SQL Server.  

|Unterstützte Betriebssysteme|  
|--------------------------------------|---------------------------------|   
|Microsoft Windows 8.1<br /><br />Microsoft Windows 10<br /><br /> Microsoft Windows Server 2012<br /><br />Microsoft Windows Server 2012<br /><br />Microsoft Windows Server 2016|  

## <a name="ado-support-policies"></a>Richtlinien zur ADO-Unterstützung  
 ADO-Anwendungen können den zum Lieferumfang von Windows gehörenden SQLOLEDB OLE DB-Anbieter verwenden, sofern sie keine Funktionen von [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] oder höher benötigen.  

 ADO-Anwendungen können den OLE DB-Treiber für SQL Server verwenden, aber wenn sie dies müssen sie angeben `DataTypeCompatibility=80` in den Verbindungszeichenfolgen. Wenn `DataTypeCompatibility=80` in den Verbindungszeichenfolgen angegeben wird, sind nur die Funktionen von [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] verfügbar.  

## <a name="ole-db-support-policies"></a>Richtlinien zur OLE DB-Unterstützung  
Anwendungen können den im Windows-Betriebssystem enthaltenen OLE DB-Anbieter (SQLOLEDB) verwenden. Allerdings, die in den Wartungsmodus versetzt wird und nicht mehr aktualisiert. Sie sollten die OLE DB-Treiber für SQL Server (MSOLEDBSQL) verwenden.

## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Erstellen von Anwendungen mit dem OLE DB-Treiber für SQL Server](../../oledb/applications/building-applications-with-oledb-driver-for-sql-server.md)   
