---
title: Hadoop-Dateisystemtask | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.ssis.designer.hadoopfiletask.f1
ms.assetid: 594aaf5d-7703-4788-897d-fb95aca798c5
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: ffb3559a379a8d1f64c76072f262b89d41164533
ms.sourcegitcommit: fd71d04a9d30a9927cbfff645750ac9d5d5e5ee7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/16/2019
ms.locfileid: "65727631"
---
# <a name="hadoop-file-system-task"></a>Hadoop-Dateisystemtask

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Der Hadoop-Dateisystemtask ermöglicht einem SSIS-Paket das Kopieren von Dateien aus einem, in ein oder innerhalb eines Hadoop-Clusters.  
  
 Zum Hinzufügen eines Hadoop-Dateisystemtasks ziehen Sie diesen auf den Designer. Doppelklicken Sie anschließend auf den Task, oder klicken Sie mit der rechten Maustaste darauf, und klicken Sie auf **Bearbeiten**, um das Hadoop-Dialogfeld **Editor für den Task „Dateisystem“** zu öffnen.  
  
 ![Editor für den Task „Dateisystem“](../../integration-services/control-flow/media/hadoop-filesystem-task.png "Editor für den Task „Dateisystem“")  
  
## <a name="options"></a>enthalten  
 Konfigurieren Sie die folgenden Optionen im Hadoop-Dialogfeld **Editor für den Task „Dateisystem“** .  
  
|Feld|und Beschreibung|  
|-----------|-----------------|  
|**Hadoop-Verbindung**|Geben Sie einen vorhandenen Hadoop-Verbindungs-Manager an, oder erstellen Sie einen neuen. Dieser Verbindungs-Manager gibt an, wo die Zieldateien gehostet werden.|  
|**Hadoop-Dateipfad**|Geben Sie den Datei- oder Verzeichnispfad auf HDFS an.|  
|**Hadoop-Dateityp**|Geben Sie an, ob es sich beim HDFS-Dateisystemobjekt um eine Datei oder um ein Verzeichnis handelt.|  
|**Ziel überschreiben**|Geben Sie an, ob die Zieldatei überschrieben werden soll, wenn sie bereits vorhanden ist.|  
|**Vorgang**|Geben Sie den Vorgang an. Verfügbare Vorgänge sind **CopyToHDFS**, **CopyFromHDFS**und **CopyWithinHDFS**.|  
|**Lokale Dateiverbindung**|Geben Sie einen vorhandenen Dateiverbindungs-Manager an, oder erstellen Sie einen neuen. Dieser Verbindungs-Manager gibt an, wo die Quelldateien gehostet werden.|  
|**Ist rekursiv**|Geben Sie an, ob alle Unterordner rekursiv kopiert werden sollen.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Hadoop-Verbindungs-Manager](../../integration-services/connection-manager/hadoop-connection-manager.md)   
 [Dateiverbindungs-Manager](../../integration-services/connection-manager/file-connection-manager.md)  
  
  
