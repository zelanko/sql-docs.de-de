---
title: Azure HDInsight-Delete Cluster-Task | Microsoft-Dokumentation
ms.custom: ''
ms.date: 02/28/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.afpdelcltask.f1
- sql11.dts.designer.afpdelcltask.f1
ms.assetid: e298776e-d18a-4393-a8e6-65ee3d555749
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 513faad27977b3a4aef9b1e4907c85cd3a2905be
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52767172"
---
# <a name="azure-hdinsight-delete-cluster-task"></a>Azure HDInsight-Delete Cluster-Task
Der **Azure HDInsight-Delete Cluster-Task** ermöglicht einem SSIS-Paket das Löschen eines Azure HDInsight-Clusters im angegebenen Azure-Abonnement und der Ressourcengruppe.
  
> [!NOTE]
> Das Löschen eines HDInsight-Clusters kann 10-20 Minuten in Anspruch nehmen.  
  
Um einen **Azure HDInsight-Delete Cluster-Task**hinzuzufügen, legen Sie ihn mittels Drag &amp; Drop auf dem SSIS-Designer ab, und doppelklicken Sie darauf, oder klicken Sie mit der rechten Maustaste, und klicken Sie dann auf **Bearbeiten** , um das folgende Dialogfeld A **zure HDInsight-Delete Cluster-Task-Editor** anzuzeigen.  
  
Die folgende Tabelle enthält Beschreibungen für die Felder in diesem Dialogfeld.  
  
|||  
|-|-|  
|**Feld**|**Beschreibung**|  
|AzureResourceManagerConnection|Wählen Sie einen vorhandenen Azure Resource Manager-Verbindungs-Manager aus, oder erstellen Sie einen neuen, mit dem der HDInsight-Cluster gelöscht wird.|
|SubscriptionId|Geben Sie die ID des Abonnements an, in dem sich der HDInsight-Cluster befindet.|
|ResourceGroup|Geben Sie die Azure-Ressourcengruppe an, in der sich der HDInsight-Cluster befindet.|
|ClusterName|Geben Sie den Namen des zu löschenden Clusters an.|  
|FailIfNotExists|Geben Sie an, ob der Task einen Fehler ausgeben soll, wenn der Cluster nicht vorhanden ist.|
