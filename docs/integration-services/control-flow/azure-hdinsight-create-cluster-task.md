---
title: Azure HDInsight Create Cluster-Task | Microsoft-Dokumentation
ms.custom: ''
ms.date: 02/28/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.afpcreatecltask.f1
- sql14.dts.designer.afpcreatecltask.f1
ms.assetid: a8ec413a-38d3-45df-887e-6f5f4d9f8465
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 3fff08c4259424319621127d3e91762beaa46885
ms.sourcegitcommit: 4b775a3ce453b757c7435cc2a4c9b35d0c5a8a9e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/31/2020
ms.locfileid: "87472414"
---
# <a name="azure-hdinsight-create-cluster-task"></a>Azure HDInsight Create Cluster-Task

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


Der **Azure HDInsight Create Cluster-Task** ermöglicht einem SSIS-Paket das Erstellen eines Azure HDInsight-Clusters im angegebenen Azure-Abonnement und in der Ressourcengruppe.
  
Der **Azure HDInsight Create Cluster-Task** ist eine Komponente des [SQL Server Integration Services-Feature Packs (SSIS) für Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md).
  
> [!NOTE]  
> - Das Erstellen eines neuen HDInsight-Clusters kann 10-20 Minuten in Anspruch nehmen.  
> - Beim Erstellen und Ausführen eines Azure HDInsight-Clusters fallen Kosten an. Details finden Sie auf der Webseite mit den [Preisinformationen für HDInsight](https://azure.microsoft.com/pricing/details/hdinsight/).  
  
Um einen **Azure HDInsight Create Cluster-Task**hinzuzufügen, legen Sie ihn mittels Drag &amp; Drop auf dem SSIS-Designer ab, und doppelklicken Sie darauf, oder klicken Sie mit der rechten Maustaste darauf. Klicken Sie dann auf **Bearbeiten** , um das folgende Dialogfeld **Azure HDInsight Create Cluster-Task-Editor** anzuzeigen.  
  
Die folgende Tabelle enthält eine Beschreibung für die Felder in diesem Dialogfeld.  
  
|Feld|Beschreibung|  
|-|-|  
|AzureResourceManagerConnection|Wählen Sie einen vorhandenen Azure Resource Manager-Verbindungs-Manager aus, oder erstellen Sie einen neuen, mit dem der HDInsight-Cluster erstellt wird.|  
|AzureStorageConnection|Wählen Sie einen vorhandenen Azure Storage-Verbindungs-Manager aus, oder erstellen Sie einen neuen, der auf ein Azure Storage-Konto verweist, um ihn mit dem HDInsight-Cluster zu verknüpfen.|
|SubscriptionId|Geben Sie die ID des Abonnements an, in dem der HDInsight-Cluster erstellt wird.|
|ResourceGroup|Geben Sie die Azure-Ressourcengruppe an, wo der HDInsight-Cluster erstellt wird.|
|Location|Geben Sie den Speicherort des HDInsight-Clusters an. Der Cluster muss am selben Speicherort erstellt werden, wo sich das Azure-Speicherkonto befindet.|  
|ClusterName|Geben Sie einen Namen für den zu erstellenden HDInsight-Cluster an.|  
|clusterSize|Geben Sie die Anzahl der Knoten an, die im Cluster erstellt werden sollen.|  
|BlobContainer|Geben Sie den Namen des standardmäßigen Speichercontainers an, der mit dem HDInsight-Cluster verbunden sein soll.|  
|UserName|Geben Sie den Benutzernamen zum Herstellen einer Verbindung mit dem HDInsight-Cluster an.|  
|Kennwort|Geben Sie das Kennwort zum Herstellen einer Verbindung mit dem HDInsight-Cluster an.|
|SshUserName|Geben Sie den Benutzernamen für den Remotezugriff auf den HDInsight-Cluster mithilfe von SSH an.|
|SshPassword|Geben Sie das Kennwort für den Remotezugriff auf den HDInsight-Cluster mithilfe von SSH an.|
|FailIfExists|Geben Sie an, ob der Task einen Fehler ausgeben soll, wenn der Cluster bereits vorhanden ist.|  
  
> [!NOTE]  
> Die Speicherorte von HDInsight-Cluster und Azure-Speicherkonto müssen identisch sein.
