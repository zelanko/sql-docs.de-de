---
title: Azure Data Lake Store Destination | Microsoft-Dokumentation
ms.custom: ''
ms.date: 05/22/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- SQL13.DTS.DESIGNER.AFPADLSDEST.F1
- sql14.dts.designer.afpadlsdest.f1
ms.assetid: 4c4f504f-dd2b-42c5-8a20-1a8ad9a5d632
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: d934cafef262f5c07b5eeac95d65abd776d8bb35
ms.sourcegitcommit: fc0eb955b41c9c508a1fe550eb5421c05fbf11b4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/30/2019
ms.locfileid: "66403036"
---
# <a name="azure-data-lake-store-destination"></a>Azure Data Lake Store Destination

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Die Komponente **Azure Data Lake Store Destination** ermöglicht einem SSIS-Paket das Schreiben von Daten in Azure Data Lake Store. Die folgenden Dateiformate werden unterstützt: Text, Avro und ORC. 
  
 **Azure Data Lake Store Destination** ist eine Komponente des [SQL Server Integration Services-Feature Packs (SSIS) für Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md).
 
> [!NOTE]
> Um sicherzustellen, dass der Azure Data Lake Store-Verbindungsmanager und die Komponenten, die ihn verwenden – das bedeutet Azure Data Lake Store Source und Azure Data Lake Store Destination – eine Verbindung zu Diensten herstellen können, stellen Sie sicher, dass Sie die neueste Version von Azure Feature Pack [hier](https://www.microsoft.com/download/details.aspx?id=49492)herunterladen. 

## <a name="configure-the-azure-data-lake-store-destination"></a>Konfigurieren von Azure Data Lake Store Destination  
1. Ziehen Sie **Azure Data Lake Store Destination** auf den Datenfluss-Designer, und doppelklicken Sie darauf, um den Code-Editor aufzurufen.  

2.  Geben Sie im Feld **Azure Data Lake Store connection manager** (Azure Data Lake Store-Verbindungs-Manager) einen vorhandenen Azure Data Lake Store-Verbindungs-Manager an, oder erstellen Sie einen neuen, der auf einen Azure Data Lake Store-Dienst verweist.  
  
    1.  Geben Sie im Feld **Dateipfad** den Namen der Datei an, in die Daten geschrieben werden sollen. Wenn diese Datei bereits vorhanden ist, wird ihr Inhalt überschrieben.  
  
    2.  Geben Sie im Feld **Dateiformat** das gewünschte Dateiformat an.  
  
       Wenn es sich um Textformat handelt, geben Sie den Wert für das **Spaltentrennzeichen** ein. Aktivieren Sie außerdem **Spaltennamen in der ersten Datenzeile** , wenn die erste Zeile in der Datei Spaltennamen enthält.  

       Hat die Datei das Format ORC, müssen Sie die Java Runtime Environment (JRE) für die betreffende Plattform installieren.
  
3.  Nachdem Sie die Verbindungsinformationen angegeben haben, wechseln Sie zur Seite **Spalten** , um Quellspalten zu den Zielspalten für den SSIS-Datenfluss zuzuordnen.  

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