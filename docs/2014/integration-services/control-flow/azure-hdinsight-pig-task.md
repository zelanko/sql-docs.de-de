---
title: Azure HDInsight Pig-Task | Microsoft-Dokumentation
ms.custom: ''
ms.date: 02/28/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.designer.afppigtask.f1
- sql11.dts.designer.afppigtask.f1
ms.assetid: 26f34f64-f344-486e-9190-acf71aef29a8
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: bd7520ca6b9b621f22960fe6013cf34cc4959cd0
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36059868"
---
# <a name="azure-hdinsight-pig-task"></a>Azure HDInsight Pig-Task
Verwenden Sie den **Azure HDInsight Pig-Task** zum Ausführen eines Pig-Skripts auf einem Azure HDInsight-Cluster.
     
Um einen **Azure HDInsight-Pig-Task**hinzuzufügen, legen Sie ihn mittels Drag &amp; Drop auf dem SSIS-Designer ab, und doppelklicken Sie darauf, oder klicken Sie mit der rechten Maustaste, und klicken Sie anschließend auf **Bearbeiten** , um das folgende Dialogfeld **Azure HDInsight-Pig-Task-Editor** anzuzeigen.  
  
 Die folgende Liste beschreibt Felder in diesem Dialogfeld.  
  
1.  Wählen Sie für das Feld **HDInsightConnection** einen vorhandenen HDInsight-Verbindungs-Manager aus, oder erstellen Sie einen neuen, der auf einen Azure HDInsight-Cluster verweist, in dem das Skript ausgeführt wird.
  
2.  Wählen Sie für das Feld **AzureStorageConnection** einen vorhandenen Azure Storage-Verbindungs-Manager aus, oder erstellen Sie einen neuen, der auf das Azure Storage-Konto verweist, das mit dem Cluster verbunden ist. Dies ist nur erforderlich, wenn Sie die Skriptausführungsausgabe- und Fehlerprotokolle herunterladen möchten.
 
3.  Geben Sie für das Feld **BlobContainer** den Speichercontainernamen an, der mit dem Cluster verbunden ist. Dies ist nur erforderlich, wenn Sie die Skriptausführungsausgabe- und Fehlerprotokolle herunterladen möchten.
  
4.  Geben Sie für das Feld **LocalLogFolder** den Ordner an, in den die Skriptausführungsausgabe- und Fehlerprotokolle heruntergeladen werden sollen. Dies ist nur erforderlich, wenn Sie die Skriptausführungsausgabe- und Fehlerprotokolle herunterladen möchten.   
  
5.  Sie haben zwei Möglichkeiten, das auszuführende Pig-Skript anzugeben:
  
    1.  **Inlineskript**: Legen Sie das Feld **Skript** fest, indem Sie im Dialogfeld **Skript eingeben** inline das auszuführende Skript eingeben.
  
    2.  **Skriptdatei**: Laden Sie die Skriptdatei in Azure Blob Storage hoch, und legen Sie das Feld **BlobName** fest. Befindet sich das Blob nicht im Standardspeicherkonto oder -container des HDInsight-Clusters, müssen die Felder **ExternalStorageAccountName** und **ExternalBlobContainer** festgelegt werden. Stellen Sie bei einem externen Blob sicher, dass es als öffentlich zugänglich konfiguriert ist.  
  
     Wenn Skriptdatei und Inlineskript angegeben sind, wird die Skriptdatei verwendet und das Inlineskript ignoriert.