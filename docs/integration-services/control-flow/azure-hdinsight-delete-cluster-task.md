---
title: Azure HDInsight-Delete Cluster-Task | Microsoft-Dokumentation
ms.custom: ''
ms.date: 02/28/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.afpdelcltask.f1
- sql14.dts.designer.afpdelcltask.f1
ms.assetid: e298776e-d18a-4393-a8e6-65ee3d555749
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 87bbb8455169ae0c50475781b3b9e25e9967fd93
ms.sourcegitcommit: 4b775a3ce453b757c7435cc2a4c9b35d0c5a8a9e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/31/2020
ms.locfileid: "87472545"
---
# <a name="azure-hdinsight-delete-cluster-task"></a>Azure HDInsight-Delete Cluster-Task

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


Der **Azure HDInsight-Delete Cluster-Task** ermöglicht einem SSIS-Paket das Löschen eines Azure HDInsight-Clusters im angegebenen Azure-Abonnement und der Ressourcengruppe.
  
Der **Azure HDInsight-Delete Cluster-Task** ist eine Komponente des [SQL Server Integration Services-Feature Packs (SSIS) für Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md).
  
> [!NOTE]
> Das Löschen eines HDInsight-Clusters kann 10-20 Minuten in Anspruch nehmen.  
  
Um einen **Azure HDInsight-Delete Cluster-Task**hinzuzufügen, legen Sie ihn mittels Drag &amp; Drop auf dem SSIS-Designer ab, und doppelklicken Sie darauf, oder klicken Sie mit der rechten Maustaste, und klicken Sie dann auf **Bearbeiten** , um das folgende Dialogfeld A **zure HDInsight-Delete Cluster-Task-Editor** anzuzeigen.  
  
Die folgende Tabelle enthält Beschreibungen für die Felder in diesem Dialogfeld.  
  
|Feld|Beschreibung|  
|-|-|  
|AzureResourceManagerConnection|Wählen Sie einen vorhandenen Azure Resource Manager-Verbindungs-Manager aus, oder erstellen Sie einen neuen, mit dem der HDInsight-Cluster gelöscht wird.|
|SubscriptionId|Geben Sie die ID des Abonnements an, in dem sich der HDInsight-Cluster befindet.|
|ResourceGroup|Geben Sie die Azure-Ressourcengruppe an, in der sich der HDInsight-Cluster befindet.|
|ClusterName|Geben Sie den Namen des zu löschenden Clusters an.|  
|FailIfNotExists|Geben Sie an, ob der Task einen Fehler ausgeben soll, wenn der Cluster nicht vorhanden ist.|
