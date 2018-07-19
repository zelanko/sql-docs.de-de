---
title: In tabellarischen 1400-Modellen von SQL Server Analysis Services unterstützte Datenquellen | Microsoft-Dokumentation
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 856e15e7365128bc79d119afe267334fb8470832
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2018
ms.locfileid: "38041658"
---
# <a name="data-sources-supported-in-sql-server-analysis-services-tabular-1400-models"></a>Unterstützten Datenquellen in SQL Server Analysis Services tabellarischen 1400-Modellen

[!INCLUDE[ssas-appliesto-sql2017](../../includes/ssas-appliesto-sql2017.md)]

Dieser Artikel beschreibt die Typen von Datenquellen, die mit tabellarischen Modellen von SQL Server Analysis Services (SSAS) mit dem Kompatibilitätsgrad 1400 verwendet werden können. 

Für tabellarische SSAS-Modelle mit den 1200 und niedrigeren Kompatibilitätsgraden finden Sie unter [in tabellarischen 1200-Modellen von SQL Server Analysis Services unterstützte Datenquellen](data-sources-supported-ssas-tabular.md).

Azure Analysis Services finden Sie unter [in Azure Analysis Services unterstützte Datenquellen](https://docs.microsoft.com/azure/analysis-services/analysis-services-datasource).


## <a name="cloud-data-sources"></a>Cloud-Datenquellen

|Azure-Datenquelle  |In-memory  |DirectQuery  |
|---------|---------|---------|
|Azure SQL-Datenbank     |   ja      |    ja      |
|Azure SQL Data Warehouse     |   ja      |   ja       |
|Azure BLOB-Speicher     |   ja       |    nein      |
|Azure-Tabellenspeicher    |   ja       |    nein      |
|Azure Cosmosdb      |  ja        |  nein        |
|Azure Data Lake Store     |   ja       |    nein      |
|Azure HDInsight-HDFS     |     ja     |   nein       |
|Azure HDInsight Spark (Beta)     |   ja       |   nein       |
||||

**Anbieter**   
In-Memory und DirectQuery-Modelle, die eine Verbindung mit Azure-Datenquellen verwenden .NET Framework-Datenanbieter für SQL Server.

## <a name="on-premises-data-sources"></a>Auf lokale Datenquellen

### <a name="supported-by-in-memory-and-directquery-models"></a>Von in-Memory und DirectQuery-Modelle unterstützt werden

|DataSource | In-Memory-Anbieter | DirectQuery-Anbieter |
|  --- | --- | --- |
| SQL Server |SQL Server Native Client 11.0, Microsoft OLE DB-Anbieter für SQLServer, .NET Framework-Datenanbieter für SQLServer | .NET Framework-Datenanbieter für SQL Server |
| SQL Server Datawarehouse |SQL Server Native Client 11.0, Microsoft OLE DB-Anbieter für SQLServer, .NET Framework-Datenanbieter für SQLServer | .NET Framework-Datenanbieter für SQL Server |
| Oracle |Microsoft OLE DB-Anbieter von Oracle, Oracle-Datenanbieter für .NET |Oracle-Datenanbieter für .NET | |
| Teradata |OLE DB-Anbieter für Teradata, Teradata-Datenanbieter für .NET |Teradata-Datenanbieter für .NET | |
| | | |

> [!NOTE]
> Bei speicherinternen Modellen können OLE DB-Anbieter eine bessere Leistung für umfangreiche Daten bereitstellen. Bei der Auswahl zwischen unterschiedlichen Anbietern für die gleiche Datenquelle müssen Sie zuerst den OLE DB-Anbieter versucht.  

### <a name="supported-by-in-memory-models-only"></a>Von nur Modelle im Arbeitsspeicher unterstützt werden

|Datenbank  |
|---------|---------|---------|
|Access-Datenbank     | 
|SQL Server Analysis Services     | 
|IBM Informix (Beta) | 
|JSON-Dokument     | 
|Zeilen aus Binärdatei     | 
|MySQL-Datenbank     | 
|PostgreSQL-Datenbank    | ja | nein
|SAP HANA   | ja | nein
|SAP Business Warehouse    | ja | nein
|Sybase-Datenbank     | ja | nein
|||

|File  |  
|---------|---------|
|Excel-Arbeitsmappe     |
|Ordner     | 
|JSON | 
|Text/CSV    | 
|XML-Tabelle    | 
|||

|Online-Dienste  |  
|---------|---------|
|Dynamics 365      |
|Exchange Online     |
|Salesforce-Objekte    | 
|Salesforce-Berichte     |
|SharePoint Online-Liste     |
|||

|Andere  |  
|---------|---------|
|Active Directory      | 
|Exchange     |  
|OData-Feed     | 
|ODBC-Abfrage     | 
|OLE DB  | 
|SharePoint-Liste | 
|||

## <a name="see-also"></a>Siehe auch

[Unterstützten Datenquellen in SQL Server Analysis Services tabular 1200-Modelle](data-sources-supported-ssas-tabular.md)

[In Azure Analysis Services unterstützte Datenquellen](https://docs.microsoft.com/azure/analysis-services/analysis-services-datasource)   
