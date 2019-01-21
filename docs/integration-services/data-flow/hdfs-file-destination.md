---
title: HDFS-Dateiziel | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/09/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.ssis.designer.hdfsfiledest.f1
ms.assetid: 4338ce9f-c077-4301-aca5-47ed070ec94d
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: f18f6b0516ab9ae417251e49f5a3cf24fd2aa997
ms.sourcegitcommit: 1c01af5b02fe185fd60718cc289829426dc86eaa
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2019
ms.locfileid: "54185006"
---
# <a name="hdfs-file-destination"></a>HDFS-Dateiziel
  Die HDFS-Dateizielkomponente ermöglicht einem SSIS-Paket das Schreiben von Daten in eine HDFS-Datei. Die unterstützten Dateiformate sind Text, Avro und ORC.  
  
 Um das HDFS-Dateiziel zu konfigurieren, ziehen Sie die HDFS-Dateiquelle in den Datenfluss-Designer, und doppelklicken Sie auf die Komponente, um den Editor zu öffnen.  
  
 ![HDFS-Dateiziel-Editor](../../integration-services/data-flow/media/hdfs-file-dest.png "HDFS-Dateiziel-Editor")  
  
## <a name="options"></a>enthalten  
 Konfigurieren Sie die folgenden Optionen auf der Registerkarte **Allgemein** im Dialogfeld **Dateiziel-Editor für Hadoop** .  
  
|Feld|und Beschreibung|  
|-----------|-----------------|  
|**Hadoop-Verbindung**|Geben Sie einen vorhandenen Hadoop-Verbindungs-Manager an, oder erstellen Sie einen neuen. Dieser Verbindungs-Manager gibt an, wo die HDFS-Dateien gehostet werden.|  
|**Dateipfad**|Geben Sie den Namen der HDFS-Datei an.|  
|**Dateiformat**|Geben Sie das Format für die HDFS-Datei an. Die verfügbaren Optionen sind Text, Avro und ORC.|  
|**Spaltentrennzeichen**|Wenn Sie das Textformat auswählen, geben Sie das Spaltentrennzeichen an.|  
|**Spaltennamen in der ersten Datenzeile**|Wenn Sie das Textformat auswählen, geben Sie an, ob die erste Zeile in der Datei Spaltennamen enthält.|  
  
 Nachdem Sie diese Optionen konfiguriert haben, wählen Sie die Registerkarte **Spalten** aus, um Quellspalten zu Zielspalten im Datenfluss zuzuordnen.  

::: moniker range=">= sql-server-ver15"
## <a name="prerequisite-for-orc-format"></a>Voraussetzung für das ORC-Format

Bevor Sie das ORC-Dateiformat verwenden können, müssen Sie die Java Runtime Environment (JRE) und Version 1.7.51 oder höher der entsprechenden Plattform installieren.

Es wird sowohl die Zulu- als auch die Oracle-JRE unterstützt.
-   [Zulu-JRE](https://www.azul.com/downloads/zulu/zulu-windows/)
-   [Oracle-JRE](https://www.oracle.com/technetwork/java/javase/downloads/jre8-downloads-2133155.html)

### <a name="set-up-the-zulu-jre"></a>Einrichten der Zulu-JRE

1. Laden Sie das ZIP-Paket für die Installation von OpenJDK für Zulu herunter, und extrahieren Sie dieses.

2.  Führen Sie über die Eingabeaufforderung `sysdm.cpl` aus.

3. Klicken Sie auf der Registerkarte **Erweitert** auf **Umgebungsvariablen**.

4. Klicken Sie im Abschnitt **Systemvariablen** auf **Neu**.

5. Geben Sie `JAVA_HOME` für den **Variablennamen** ein.

6. Klicken Sie auf **Verzeichnis durchsuchen**, navigieren Sie zum Installationsordner für Zulu OpenJDK, und wählen Sie den Unterordner `jre` aus. Klicken Sie anschließend auf „OK“. Der Variablenwert wird automatisch aufgefüllt.

7. Klicken Sie auf **OK**, um das Dialogfeld **New System Variable** (Neue Systemvariable) zu schließen.

8. Klicken Sie auf **OK**, um das Dialogfeld „Umgebungsvariablen“ zu schließen.

### <a name="set-up-the-oracle-jre"></a>Einrichten der Oracle-JRE

1. Laden Sie das EXE-Installationsprogramm für die Oracle-JRE herunter, und führen Sie es aus.

1. Führen Sie die Installationsanweisungen aus, um das Setup abzuschließen.

::: moniker-end

## <a name="see-also"></a>Weitere Informationen  
 [Hadoop-Verbindungs-Manager](../../integration-services/connection-manager/hadoop-connection-manager.md)   
 [HDFS-Dateiquelle](../../integration-services/data-flow/hdfs-file-source.md)  
