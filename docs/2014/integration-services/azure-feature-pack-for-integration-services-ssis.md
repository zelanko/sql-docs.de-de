---
title: Azure FeaturePack für | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- SQL11.SSIS.AZURE.F1
- SQL12.SSIS.AZURE.F1
ms.assetid: 31de555f-ae62-4f2f-a6a6-77fea1fa8189
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 9c815b6d3dd2a70e484575fc49f90186f1273ba7
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48106690"
---
# <a name="azure-feature-pack"></a>Azure Feature Pack
Das SQL Server Integration Services-Feature Pack (SSIS) für Azure ist eine Erweiterung, die die auf dieser Seite für SSIS aufgelisteten Komponenten für Verbindungen mit Azure-Diensten, für die Übertragung von Daten zwischen Azure und lokalen Datenquellen und für die Verarbeitung der in Azure gespeicherten Daten bereitstellt.

## <a name="components-in-the-feature-pack"></a>Komponenten im Feature Pack
  
-   Verbindungs-Manager  
  
    -   [Azure Storage-Verbindungs-Manager](connection-manager/azure-storage-connection-manager.md)  
  
    -   [Azure-Abonnementverbindungs-Manager](connection-manager/azure-subscription-connection-manager.md)  
    
    -   [Azure Data Lake Store Connection Manager (Azure Data Lake Store-Verbindungs-Manager)](../../2014/integration-services/azure-data-lake-store-connection-manager.md)
    
    -   [Azure Resource Manager-Verbindungs-Manager](../../2014/integration-services/azure-resource-manager-connection-manager.md)
    
    -   [Azure HDInsight-Verbindungs-Manager](../../2014/integration-services/azure-hdinsight-connection-manager.md)
  
-   Aufgaben  
  
    -   [Azure-Blob-Uploadtask](control-flow/azure-blob-upload-task.md)  
  
    -   [Azure Blob-Download-Task](control-flow/azure-blob-download-task.md)  
  
    -   [Azure HDInsight Hive-Task](control-flow/azure-hdinsight-hive-task.md)  
  
    -   [Azure HDInsight Pig-Task](https://msdn.microsoft.com/library/mt146781(v=sql.120).aspx)
  
    -   [Azure HDInsight Create Cluster-Task](control-flow/azure-hdinsight-create-cluster-task.md)  
  
    -   [Azure HDInsight-Delete Cluster-Task](control-flow/azure-hdinsight-delete-cluster-task.md)
    
    -   [Azure SQL DW-Uploadtask](../../2014/integration-services/azure-sql-dw-upload-task.md)    
    
    -   [Azure Data Lake Store-Dateisystemtask](control-flow/file-system-task.md)    
  
-   Datenflusskomponenten  
  
    -   [Azure-Blob-Quelle](https://msdn.microsoft.com/library/mt146775(v=sql.120).aspx)  
  
    -   [Azure-BLOB-Ziel](data-flow/azure-blob-destination.md)  
    
    -   [Azure Data Lake Store Source](../../2014/integration-services/azure-data-lake-store-source.md)
    
    -   [Azure Data Lake Store Destination](../../2014/integration-services/azure-data-lake-store-destination.md)
  
-   Azure-Blob-Enumerator und ADLS-Dateienumerator. Siehe [Foreach Loop Container](control-flow/foreach-loop-container.md).  
  
 
## <a name="download-the-feature-pack"></a>Download des Feature Packs  
Sie können das SQL Server Integration Services-Feature Pack (SSIS) für Azure hier herunterladen.  
  
-   [Microsoft SQL Server 2014 Integration Services Feature Pack für Azure](https://www.microsoft.com/download/details.aspx?id=47366)  

## <a name="prerequisites"></a>Erforderliche Komponenten  
Sie müssen die folgenden erforderlichen Komponenten installieren, bevor Sie dieses Feature Pack installieren.  
  
-   SQL Server Integration Services  
-   .NET Framework 4.5  
  
## <a name="scenarios"></a>Szenarien  
  
### <a name="big-data-processing"></a>Big Data-Verarbeitung  
 Verwenden Sie den Azure Connector zum Ausführen der folgenden Big Data-Verarbeitungsaufgaben:  
  
1.  Verwenden Sie den Azure Blob Upload-Task zum Hochladen von Eingabedaten in den Azure BLOB-Speicher.  
  
2.  Verwenden Sie den Azure HDInsight Create Cluster-Task zum Erstellen eines Azure HDInsight-Clusters. Dieser Schritt ist optional, wenn Sie einen eigenen Cluster verwenden möchten.  
  
3.  Verwenden Sie den Azure HDInsight Hive-Task oder Azure HDInsight Pig-Task zum Aufrufen eines Pig- oder Hive-Auftrags auf dem Azure HDInsight-Cluster.  
  
4.  Verwenden Sie den Azure HDInsight Delete Cluster-Task zum Löschen des HDInsight-Clusters nach der Verwendung, wenn Sie in Schritt 2 einen HDInsight-Bedarfscluster erstellt haben.  
  
5.  Verwenden Sie den Azure HDInsight Blob Download-Task zum Herunterladen der Pig/Hive-Ausgabedaten vom Azure BLOB-Speicher.  
  
 ![SSIS-AzureConnector-BigDataScenario](media/ssis-azureconnector-bigdatascenario.png "SSIS-AzureConnector-BigDataScenario")  
  
### <a name="cloud-data-archiving"></a>Archivieren von Clouddaten  
 Verwenden Sie das Azure BLOB-Ziel in einem SSIS-Paket, um Ausgabedaten in einen Azure BLOB-Speicher zu schreiben, oder verwenden Sie die Azure Blob-Quelle zum Lesen von Daten aus einem Azure BLOB-Speicher.  
  
 ![SSIS-AzureConnector-CloudArchive-1](media/ssis-azureconnector-cloudarchive-1.png "SSIS-AzureConnector-CloudArchive-1")  
  
 ![SSIS-AzureConnector-CloudArchive-2](media/ssis-azureconnector-cloudarchive-2.png "SSIS-AzureConnector-CloudArchive-2")  
  
 Und verwenden Sie den Foreach-Schleifencontainer mit dem Azure Blob-Enumerator, um Daten in mehreren BLOB-Dateien zu verarbeiten.  
  
 ![SSIS-AzureConnector-CloudArchive-3](media/ssis-azureconnector-cloudarchive-3.png "SSIS-AzureConnector-CloudArchive-3")  
  
  
