---
title: In tabellarischen 1400-Modellen von SQL Server Analysis Services unterstützte Datenquellen | Microsoft-Dokumentation
ms.date: 02/12/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4c900c6f1683b9f4c96355a759c604022515d2ce
ms.sourcegitcommit: 89a7bd9ccbcb19bb92a1f4ba75576243a58584e8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/13/2019
ms.locfileid: "56159755"
---
# <a name="data-sources-supported-in-sql-server-analysis-services-tabular-1400-models"></a>Unterstützten Datenquellen in SQL Server Analysis Services tabellarischen 1400-Modellen

[!INCLUDE[ssas-appliesto-sql2017](../../includes/ssas-appliesto-sql2017.md)]

Dieser Artikel beschreibt die Typen von Datenquellen, die mit tabellarischen Modellen von SQL Server Analysis Services (SSAS) mit dem Kompatibilitätsgrad 1400 verwendet werden können. 

Für tabellarische SSAS-Modelle mit den 1200 und niedrigeren Kompatibilitätsgraden finden Sie unter [in tabellarischen 1200-Modellen von SQL Server Analysis Services unterstützte Datenquellen](data-sources-supported-ssas-tabular.md).

Azure Analysis Services finden Sie unter [in Azure Analysis Services unterstützte Datenquellen](https://docs.microsoft.com/azure/analysis-services/analysis-services-datasource).


## <a name="cloud-data-sources"></a>Cloud-Datenquellen

|DataSource  |In-memory  |DirectQuery  |
|---------|---------|---------|
|Azure SQL-Datenbank     |   Ja      |    Ja      |
|Azure SQL Data Warehouse     |   Ja      |   Ja       |
|Azure Blob Storage     |   Ja       |    Nein      |
|Azure-Tabellenspeicher    |   Ja       |    Nein      |
|Azure Cosmos DB     |  Ja        |  Nein        |
|Azure Data Lake Store (Gen1)<sup>[1](#gen2)</sup>      |   Ja       |    Nein      |
|Azure HDInsight HDFS    |     Ja     |   Nein       |
|Azure HDInsight Spark <sup>[2](#databricks)</sup>     |   Ja       |   Nein       |
||||

<a name="gen2">1</a> -ADLS-Gen2 wird derzeit nicht unterstützt.   
<a name="databricks">2</a> – Azure Databricks unter Verwendung der Spark-Connector wird derzeit nicht unterstützt.   



**Provider**   
In-Memory und DirectQuery-Modelle, die eine Verbindung mit Azure-Datenquellen verwenden .NET Framework-Datenanbieter für SQL Server.

## <a name="on-premises-data-sources"></a>Auf lokale Datenquellen

### <a name="supported-by-in-memory-and-directquery-models"></a>Von in-Memory und DirectQuery-Modelle unterstützt werden

|DataSource | In-Memory-Anbieter | DirectQuery-Anbieter |
|  --- | --- | --- |
| SQL Server |SQL Server Native Client 11.0, Microsoft OLE DB-Anbieter für SQLServer, .NET Framework-Datenanbieter für SQLServer | .NET Framework-Datenanbieter für SQL Server |
| SQL Server Data Warehouse |SQL Server Native Client 11.0, Microsoft OLE DB-Anbieter für SQLServer, .NET Framework-Datenanbieter für SQLServer | .NET Framework-Datenanbieter für SQL Server |
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
|PostgreSQL-Datenbank    | Ja | Nein
|SAP HANA   | Ja | Nein
|SAP Business Warehouse    | Ja | Nein
|Sybase-Datenbank     | Ja | Nein
|||

|Datei  |  
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
|Exhange Online     |
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
