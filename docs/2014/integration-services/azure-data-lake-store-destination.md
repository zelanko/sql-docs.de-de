---
title: Azure Data Lake Store Destination | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- SQL12.DTS.DESIGNER.AFPADLSDEST.F1
- SQL11.DTS.DESIGNER.AFPADLSDEST.F1
ms.assetid: d0e86032-2a6b-48b2-898f-e94328474fde
author: yualan
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 980e9c4c1b903518d49ea7f3945646e1af2d8c8e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48125420"
---
# <a name="azure-data-lake-store-destination"></a>Azure Data Lake Store Destination
  Die Komponente **Azure Data Lake Store Destination** ermöglicht einem SSIS-Paket das Schreiben von Daten in Azure Data Lake Store. Die unterstützten Dateiformate sind: Text, Avro und ORC. 
  
## <a name="configure-the-azure-data-lake-store-destination"></a>Konfigurieren von Azure Data Lake Store Destination 

1. Ziehen Sie **Azure Data Lake Store Destination** auf den Datenfluss-Designer, und doppelklicken Sie darauf, um den Code-Editor aufzurufen.  

2.  Geben Sie im Feld **Azure Data Lake Store connection manager** (Azure Data Lake Store-Verbindungs-Manager) einen vorhandenen Azure Data Lake Store-Verbindungs-Manager an, oder erstellen Sie einen neuen, der auf einen Azure Data Lake Store-Dienst verweist.  
  
    1.  Geben Sie im Feld **Dateipfad** den Namen der Datei an, in die Daten geschrieben werden sollen. Wenn diese Datei bereits vorhanden ist, wird der Inhalt überschrieben.  
  
    2.  Geben Sie im Feld **Dateiformat** das gewünschte Dateiformat an.  
  
        Wenn es sich um Textformat handelt, geben Sie den Wert für das **Spaltentrennzeichen** ein. Aktivieren Sie außerdem **Spaltennamen in der ersten Datenzeile** , wenn die erste Zeile in der Datei Spaltennamen enthält.  

        Wenn das Dateiformat ORC ist, müssen Sie JRE auf der entsprechenden Plattform installieren. 
  
3.  Nachdem Sie die Verbindungsinformationen angegeben haben, wechseln Sie zur Seite **Spalten** , um Quellspalten zu den Zielspalten für den SSIS-Datenfluss zuzuordnen.  
