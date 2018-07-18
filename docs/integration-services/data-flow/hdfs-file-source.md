---
title: HDFS-Dateiquelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql13.ssis.designer.hdfsfilesrc.f1
ms.assetid: f8cda200-c389-4a2e-8ee9-5d59b326aac1
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 3a91a00dad5cb2299aaa11e14d0e952c1b363ec3
ms.sourcegitcommit: cc46afa12e890edbc1733febeec87438d6051bf9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2018
ms.locfileid: "35399872"
---
# <a name="hdfs-file-source"></a>HDFS-Dateiquelle
  Mit der HDFS-Dateiquelle (HDFS File Source) kann ein SSIS-Paket Daten aus einer HDFS-Datei lesen. Die unterstützten Dateiformate sind Text und AVRO. (ORC-Quellen werden nicht unterstützt.)  
  
 Um die HDFS-Dateiquelle zu konfigurieren, ziehen Sie sie in den Datenfluss-Designer. Doppelklicken Sie darauf, um den Editor zu öffnen.  
  
 ![HDFS-Dateiquellen-Editor](../../integration-services/data-flow/media/hdfs-file-source.png "HDFS-Dateiquellen-Editor")  
  
## <a name="options"></a>Tastatur  
 Konfigurieren Sie die folgenden Optionen auf der Registerkarte **Allgemein** im Dialogfeld **Quellen-Editor für Hadoop-Dateien** .  
  
|Feld|und Beschreibung|  
|-----------|-----------------|  
|**Hadoop-Verbindung**|Geben Sie einen vorhandenen Hadoop-Verbindungs-Manager an, oder erstellen Sie einen neuen. Dieser Verbindungs-Manager gibt an, wo die HDFS-Dateien gehostet werden.|  
|**Dateipfad**|Geben Sie den Namen der HDFS-Datei an.|  
|**Dateiformat**|Geben Sie das Format für die HDFS-Datei an. Die verfügbaren Optionen sind "Text" oder "Avro". (ORC-Quellen werden nicht unterstützt.)|  
|**Spaltentrennzeichen**|Wenn Sie das Textformat auswählen, geben Sie das Spaltentrennzeichen an.|  
|**Spaltennamen in der ersten Datenzeile**|Wenn Sie das Textformat auswählen, geben Sie an, ob die erste Zeile in der Datei Spaltennamen enthält.|  
  
 Nachdem Sie diese Optionen konfiguriert haben, wählen Sie die Registerkarte **Spalten** aus, um Quellspalten zu Zielspalten im Datenfluss zuzuordnen.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Hadoop-Verbindungs-Manager](../../integration-services/connection-manager/hadoop-connection-manager.md)   
 [HDFS-Dateiziel](../../integration-services/data-flow/hdfs-file-destination.md)  
  
  
