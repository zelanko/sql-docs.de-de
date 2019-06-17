---
title: Azure HDInsight Create Cluster-Task | Microsoft-Dokumentation
ms.custom: ''
ms.date: 02/28/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.afpcreatecltask.f1
- sql11.dts.designer.afpcreatecltask.f1
ms.assetid: a8ec413a-38d3-45df-887e-6f5f4d9f8465
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: f41d86d0f757f9ccd0e698ac1bc81423a3118bb9
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62832780"
---
# <a name="azure-hdinsight-create-cluster-task"></a>Azure HDInsight Create Cluster-Task
Der **Azure HDInsight Create Cluster-Task** ermöglicht einem SSIS-Paket das Erstellen eines Azure HDInsight-Clusters im angegebenen Azure-Abonnement und in der Ressourcengruppe.
  
> [!NOTE]  
> - Das Erstellen eines neuen HDInsight-Clusters kann 10-20 Minuten in Anspruch nehmen.  
> - Beim Erstellen und Ausführen eines Azure HDInsight-Clusters fallen Kosten an. Details finden Sie auf der Webseite mit den [Preisinformationen für HDInsight](http://azure.microsoft.com/en-us/pricing/details/hdinsight/).  
  
Um einen **Azure HDInsight Create Cluster-Task**hinzuzufügen, legen Sie ihn mittels Drag &amp; Drop auf dem SSIS-Designer ab, und doppelklicken Sie darauf, oder klicken Sie mit der rechten Maustaste darauf. Klicken Sie dann auf **Bearbeiten** , um das folgende Dialogfeld **Azure HDInsight Create Cluster-Task-Editor** anzuzeigen.  
  
Die folgende Tabelle enthält eine Beschreibung für die Felder in diesem Dialogfeld.  
  
|||  
|-|-|  
|**Feld**|**Beschreibung**|  
|AzureResourceManagerConnection|Wählen Sie einen vorhandenen Azure Resource Manager-Verbindungs-Manager aus, oder erstellen Sie einen neuen, mit dem der HDInsight-Cluster erstellt wird.|  
|AzureStorageConnection|Wählen Sie einen vorhandenen Azure Storage-Verbindungs-Manager aus, oder erstellen Sie einen neuen, der auf ein Azure Storage-Konto verweist, um ihn mit dem HDInsight-Cluster zu verknüpfen.|
|SubscriptionId|Geben Sie die ID des Abonnements an, in dem der HDInsight-Cluster erstellt wird.|
|ResourceGroup|Geben Sie die Azure-Ressourcengruppe an, wo der HDInsight-Cluster erstellt wird.|
|Speicherort|Geben Sie den Speicherort des HDInsight-Clusters an. Der Cluster muss am selben Speicherort erstellt werden, wo sich das Azure-Speicherkonto befindet.|  
|ClusterName|Geben Sie einen Namen für den zu erstellenden HDInsight-Cluster an.|  
|ClusterSize|Geben Sie die Anzahl der Knoten an, die im Cluster erstellt werden sollen.|  
|BlobContainer|Geben Sie den Namen des standardmäßigen Speichercontainers an, der mit dem HDInsight-Cluster verbunden sein soll.|  
|UserName|Geben Sie den Benutzernamen zum Herstellen einer Verbindung mit dem HDInsight-Cluster an.|  
|Kennwort|Geben Sie das Kennwort zum Herstellen einer Verbindung mit dem HDInsight-Cluster an.|
|SshUserName|Geben Sie den Benutzernamen für den Remotezugriff auf den HDInsight-Cluster mithilfe von SSH an.|
|SshPassword|Geben Sie das Kennwort für den Remotezugriff auf den HDInsight-Cluster mithilfe von SSH an.|
|FailIfExists|Geben Sie an, ob der Task einen Fehler ausgeben soll, wenn der Cluster bereits vorhanden ist.|  
  
> [!NOTE]  
> Die Speicherorte von HDInsight-Cluster und Azure-Speicherkonto müssen identisch sein.
