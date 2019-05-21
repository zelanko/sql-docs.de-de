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
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 418921c7ce0f37cbbf7953f6b8023a717f8ae54b
ms.sourcegitcommit: fd71d04a9d30a9927cbfff645750ac9d5d5e5ee7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/16/2019
ms.locfileid: "65726782"
---
# <a name="hdfs-file-destination"></a>HDFS-Dateiziel

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Die HDFS-Dateizielkomponente ermöglicht einem SSIS-Paket das Schreiben von Daten in eine HDFS-Datei. Die unterstützten Dateiformate sind Text, Avro und ORC.

 Um das HDFS-Dateiziel zu konfigurieren, ziehen Sie die HDFS-Dateiquelle in den Datenfluss-Designer, und doppelklicken Sie auf die Komponente, um den Editor zu öffnen.

 ![HDFS-Dateiziel-Editor](../../integration-services/data-flow/media/hdfs-file-dest.png "HDFS-Dateiziel-Editor")

## <a name="options"></a>Optionen
 Konfigurieren Sie die folgenden Optionen auf der Registerkarte **Allgemein** im Dialogfeld **Dateiziel-Editor für Hadoop** .

|Feld|Beschreibung|
|-----------|-----------------|
|**Hadoop-Verbindung**|Geben Sie einen vorhandenen Hadoop-Verbindungs-Manager an, oder erstellen Sie einen neuen. Dieser Verbindungs-Manager gibt an, wo die HDFS-Dateien gehostet werden.|
|**Dateipfad**|Geben Sie den Namen der HDFS-Datei an.|
|**Dateiformat**|Geben Sie das Format für die HDFS-Datei an. Die verfügbaren Optionen sind Text, Avro und ORC.|
|**Spaltentrennzeichen**|Wenn Sie das Textformat auswählen, geben Sie das Spaltentrennzeichen an.|
|**Spaltennamen in der ersten Datenzeile**|Wenn Sie das Textformat auswählen, geben Sie an, ob die erste Zeile in der Datei Spaltennamen enthält.|

 Nachdem Sie diese Optionen konfiguriert haben, wählen Sie die Registerkarte **Spalten** aus, um Quellspalten zu Zielspalten im Datenfluss zuzuordnen.

::: moniker range=">= sql-server-ver15"

## <a name="prerequisite-for-orc-file-format"></a>Voraussetzung für das ORC-Dateiformat
Zur Verwendung des ORC-Dateiformats ist Java erforderlich.
Die Architektur (32/64 Bit) des Java-Builds muss mit der der zu verwendenden SSIS-Runtime übereinstimmen.
Die folgenden Java-Builds wurden getestet.

- [OpenJDK 8u192 für Zulu](https://www.azul.com/downloads/zulu/zulu-windows/)
- [Oracle Java SE Runtime Environment 8u192](https://www.oracle.com/technetwork/java/javase/downloads/java-archive-javase8-2177648.html)

### <a name="set-up-zulus-openjdk"></a>Einrichten von OpenJDK für Zulu
1. Laden Sie das ZIP-Paket für die Installation herunter, und extrahieren Sie es.
2. Führen Sie über die Eingabeaufforderung `sysdm.cpl` aus.
3. Klicken Sie auf der Registerkarte **Erweitert** auf **Umgebungsvariablen**.
4. Klicken Sie im Abschnitt **Systemvariablen** auf **Neu**.
5. Geben Sie `JAVA_HOME` für den **Variablennamen** ein.
6. Klicken Sie auf **Verzeichnis durchsuchen**, navigieren Sie zum extrahierten Ordner, und wählen Sie den Unterordner `jre` aus.
   Wählen Sie anschließend **OK** aus. Daraufhin wird der **Variablenwert** automatisch aufgefüllt.
7. Klicken Sie auf **OK**, um das Dialogfeld **New System Variable** (Neue Systemvariable) zu schließen.
8. Klicken Sie auf **OK**, um das Dialogfeld **Umgebungsvariablen** zu schließen.
9. Klicken Sie auf **OK**, um das Dialogfeld **Systemeigenschaften** zu schließen.

### <a name="set-up-oracles-java-se-runtime-environment"></a>Einrichten von Oracle Java SE Runtime Environment
1. Laden Sie das EXE-Installationsprogramm herunter, und führen Sie es aus.
2. Führen Sie die Installationsanweisungen aus, um das Setup abzuschließen.

::: moniker-end

## <a name="see-also"></a>Weitere Informationen
[Hadoop-Verbindungs-Manager](../../integration-services/connection-manager/hadoop-connection-manager.md)  
[HDFS-Dateiquelle](../../integration-services/data-flow/hdfs-file-source.md)
