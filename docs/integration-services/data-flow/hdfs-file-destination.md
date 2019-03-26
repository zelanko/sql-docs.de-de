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
ms.openlocfilehash: 6a18a12c10e23e44b597ec6dc5bddebf6a5a77db
ms.sourcegitcommit: 7ccb8f28eafd79a1bddd523f71fe8b61c7634349
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/20/2019
ms.locfileid: "58275792"
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
