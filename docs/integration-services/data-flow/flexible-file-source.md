---
title: Flexible Dateiquelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 05/22/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.afpextfilesrc.f1
- sql14.dts.designer.afpextfilesrc.f1
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 3e396e40f30571969b347c464687321b3b038212
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66462532"
---
# <a name="flexible-file-source"></a>Flexible Dateiquelle

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]

Die Komponente **Flexible Dateiquelle** ermöglicht einem SSIS-Paket das Lesen von Daten aus verschiedenen unterstützten Speicherdiensten.
Zurzeit unterstützte Speicherdienste:

- [Azure Blob Storage](https://azure.microsoft.com/services/storage/blobs/)
- [Azure Data Lake Storage Gen2](https://docs.microsoft.com/azure/storage/blobs/data-lake-storage-introduction)
  
Um den Editor für die flexible Dateiquelle aufzurufen, ziehen Sie die **flexible Dateiquelle** auf den Datenfluss-Designer, und doppelklicken Sie darauf, um den Editor zu öffnen.
  
Die **flexible Dateiquelle** ist eine Komponente des [SQL Server Integration Services Feature Pack (SSIS) für Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md).  
  
Die folgenden Eigenschaften stehen im **Editor für die flexible Dateiquelle** zur Verfügung.

- **Typ des Verbindungs-Managers:** Gibt den Typ des Quellverbindungs-Managers an. Wählen Sie einen vorhandenen Manager des angegebenen Typs aus, oder erstellen Sie einen neuen.
- **Ordnerpfad:** Gibt den Pfad des Quellordners an.
- **Dateiname:** Gibt den Namen der Quelldatei an.
- **Dateiformat:** Gibt das Format der Quelldatei an. Unterstützte Formate sind **Text**, **Avro**, **ORC**, **Parquet**.
- **Spaltentrennzeichen:** Gibt das als Trennzeichen für Spalten verwendete Zeichen an (Trennzeichen, die aus mehreren Zeichen bestehen, werden nicht unterstützt).
- **Erste Zeile als Spaltenname:** Gibt an, ob die erste Zeile als Spaltenname behandelt werden soll.
- **Datei dekomprimieren:** Gibt an, ob die Quelldatei dekomprimiert werden soll.
- **Komprimierungstyp:** Gibt das Komprimierungsformat der Quelldatei an. Unterstützte Formate sind **GZIP**, **DEFLATE**, **BZIP2**.
  
Die folgenden Eigenschaften stehen im **Erweiterten Editor** zur Verfügung.

- **rowDelimiter:** Das Zeichen, das zum Trennen von Zeilen in einer Datei verwendet wird. Es ist nur ein Zeichen zulässig. Der **Standardwert** ist „\r\n“.
- **escapeChar:** Das Sonderzeichen, mit dem ein Spaltentrennzeichen im Inhalt der Eingabedatei mit Escapezeichen versehen werden kann. Sie können nicht gleichzeitig „escapeChar“ und „quoteChar“ für eine Tabelle angeben. Es ist nur ein Zeichen zulässig. Es gibt keinen Standardwert.
- **quoteChar:** Das Zeichen, mit dem ein Zeichenfolgenwert in Anführungszeichen gesetzt wird. Die Spalten- und Zeilentrennzeichen innerhalb der Anführungszeichen werden als Teil des Zeichenfolgenwerts behandelt. Diese Eigenschaft gilt sowohl für Eingabe- als auch Ausgabedatasets. Sie können nicht gleichzeitig „escapeChar“ und „quoteChar“ für eine Tabelle angeben. Es ist nur ein Zeichen zulässig. Es gibt keinen Standardwert.
- **nullValue:** Ein oder mehrere Zeichen, mit denen ein NULL-Wert dargestellt wird. Der **Standardwert** ist „\N“.
- **encodingName:** Geben Sie den Codierungsnamen an. Siehe Eigenschaft [Encoding.EncodingName](https://docs.microsoft.com/en-us/dotnet/api/system.text.encoding?redirectedfrom=MSDN&view=netframework-4.8).
- **skipLineCount:**  Gibt die Anzahl der nicht leeren Zeilen an, die beim Lesen von Daten aus Eingabedateien übersprungen werden sollen. Wenn „skipLineCount“ und „firstRowAsHeader“ gleichzeitig angegeben sind, werden die Zeilen zuerst übersprungen, und anschließend werden die Kopfzeileninformationen aus der Eingabedatei gelesen.
- **treatEmptyAsNull:** Gibt an, ob Null- oder leere Zeichenfolgen beim Lesen von Daten aus einer Eingabedatei als NULL-Werte behandelt werden sollen. Der Standardwert ist **True**.

Nachdem Sie die Verbindungsinformationen angegeben haben, wechseln Sie zur Seite **Spalten**, um den Zielspalten für den SSIS-Datenfluss Quellspalten zuzuordnen.

**Voraussetzung für das ORC/Parquet-Dateiformat**

Zur Verwendung des ORC/Parquet-Dateiformats ist Java erforderlich.
Die Architektur (32/64 Bit) des Java-Builds muss mit der der zu verwendenden SSIS-Runtime übereinstimmen.
Die folgenden Java-Builds wurden getestet.

- [OpenJDK 8u192 für Zulu](https://www.azul.com/downloads/zulu/zulu-windows/)
- [Oracle Java SE Runtime Environment 8u192](https://www.oracle.com/technetwork/java/javase/downloads/java-archive-javase8-2177648.html)

**Einrichten von OpenJDK für Zulu**

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

**Einrichten von Oracle Java SE Runtime** Environment

1. Laden Sie das EXE-Installationsprogramm herunter, und führen Sie es aus.
2. Führen Sie die Installationsanweisungen aus, um das Setup abzuschließen.
