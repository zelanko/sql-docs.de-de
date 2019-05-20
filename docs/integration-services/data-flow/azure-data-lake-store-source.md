---
title: Azure Data Lake Store Source | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/16/2018
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- SQL13.DTS.DESIGNER.AFPADLSSRC.F1
- sql14.dts.designer.afpadlssrc.f1
ms.assetid: f9c3311f-7316-48d6-bf10-d810e70b4304
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 105bc5131a4c4c56bb7218de46c1bf6b6e86254c
ms.sourcegitcommit: fd71d04a9d30a9927cbfff645750ac9d5d5e5ee7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/16/2019
ms.locfileid: "65727180"
---
# <a name="azure-data-lake-store-source"></a>Azure Data Lake Store Source

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Die Komponente **Azure Data Lake Store Source** ermöglicht einem SSIS-Paket das Lesen von Daten aus Azure Data Lake Store. Die folgenden Dateiformate werden unterstützt: Text und Avro.
  
 **Azure Data Lake Store Source** ist eine Komponente des [SQL Server Integration Services-Feature Packs (SSIS) für Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md).  
  
> [!NOTE]
> Um sicherzustellen, dass der Azure Data Lake Store-Verbindungsmanager und die Komponenten, die ihn verwenden – das bedeutet Azure Data Lake Store Source und Azure Data Lake Store Destination – eine Verbindung zu Diensten herstellen können, stellen Sie sicher, dass Sie die neueste Version von Azure Feature Pack [hier](https://www.microsoft.com/download/details.aspx?id=49492)herunterladen. 
  
## <a name="configure-the-azure-data-lake-store-source"></a>Konfigurieren von Azure Data Lake Store Source
 1. Um den Editor für Azure Data Lake Store Source aufzurufen, ziehen Sie die **Azure Data Lake Store Source** auf den Datenfluss-Designer, und doppelklicken Sie darauf, um den Editor zu öffnen.  
  
2.  Geben Sie im Feld **Azure Data Lake Store connection manager** (Azure Data Lake Store-Verbindungs-Manager) einen vorhandenen Azure Data Lake Store-Verbindungs-Manager an, oder erstellen Sie einen neuen, der auf einen Azure Data Lake Store-Dienst verweist.  
  
    1.  Geben Sie im Feld **Dateipfad** den Dateipfad der Quelldatei in Azure Data Lake Store an.   
  
    2.  Geben Sie im Feld **Dateiformat** das Dateiformat der Quelldatei an.  
  
        Wenn es sich um Textformat handelt, geben Sie den Wert für das **Spaltentrennzeichen** ein. Aktivieren Sie außerdem **Spaltennamen in der ersten Datenzeile** , wenn die erste Zeile in der Datei Spaltennamen enthält.  
  
3.  Nachdem Sie die Verbindungsinformationen angegeben haben, wechseln Sie zur Seite **Spalten** , um Quellspalten zu den Zielspalten für den SSIS-Datenfluss zuzuordnen.   

## <a name="text-qualifier"></a>Textqualifizierer

Die **Azure Data Lake Store Source** unterstützt keine Textqualifizierer. Wenn Sie einen Textqualifizierer angeben müssen, damit Ihre Dateien ordnungsgemäß verarbeitet werden, laden Sie am besten die Dateien auf Ihren lokalen Computer herunter, und verarbeiten Sie die Dateien mit der **Flatfilequelle**. Mit der Flatfilequelle können Sie einen Textqualifizierer angeben. Weitere Informationen finden Sie unter [Flat File Source (Flatfilequelle)](flat-file-source.md).
