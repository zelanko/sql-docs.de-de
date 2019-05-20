---
title: Azure-Blob-Quelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/20/2018
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.afpblobsrc.f1
- sql14.dts.designer.afpblobsrc.f1
ms.assetid: 80645c5c-88c8-4fb0-8607-de1bb7bffcbb
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 7d0dd556e17d50e66a0d74805fd754318f5226ad
ms.sourcegitcommit: fd71d04a9d30a9927cbfff645750ac9d5d5e5ee7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/16/2019
ms.locfileid: "65727188"
---
# <a name="azure-blob-source"></a>Azure-Blob-Quelle

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Die **Azure-Blobquelle** ermöglicht es einem SSIS-Paket, Daten aus einem Azure-Blob zu lesen. Die folgenden Dateiformate werden unterstützt: CSV und AVRO.
  
  Um den Editor für die Azure-Blobquelle aufzurufen, ziehen Sie die **Azure-Blobquelle** auf den Datenfluss-Designer, und doppelklicken Sie darauf, um den Editor zu öffnen.  
  
 Die **Azure-Blob-Quelle** ist eine Komponente des [SQL Server Integration Services-Feature Packs (SSIS) für Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md).  
  
1.  Geben Sie für den **Azure Storage-Verbindungs-Manager** einen vorhandenen Azure Storage-Verbindungs-Manager an, oder erstellen Sie einen neuen, der auf ein Azure-Speicherkonto verweist.  
  
2.  Geben Sie im Feld **Blobcontainername** den Namen des Blobcontainers an, der die Quelldateien enthält.  
  
3.  Geben Sie im Feld **Blobname** den Pfad für das Blob an.  
  
4.  Wählen Sie im Feld **Blobdateiformat** das gewünschte Blobformat aus: **Text** oder **Avro**.  
  
5.  Wenn Sie das Dateiformat **Text** auswählen, geben Sie den Wert für das **Spaltentrennzeichen** an. (Trennzeichen mit mehreren Zeichen werden nicht unterstützt.)

    Aktivieren Sie außerdem **Spaltennamen in der ersten Datenzeile** , wenn die erste Zeile in der Datei Spaltennamen enthält.

6.  Wenn die Datei komprimiert ist, klicken Sie auf **Datei dekomprimieren**.

7.  Wenn die Datei komprimiert ist, wählen Sie den **Komprimierungstyp** aus: **GZIP**, **DEFLATE** oder **BZIP2**. Beachten Sie, dass das ZIP-Format nicht unterstützt wird.
  
8.  Nachdem Sie die Verbindungsinformationen angegeben haben, wechseln Sie zur Seite **Spalten**, um den Zielspalten für den SSIS-Datenfluss Quellspalten zuzuordnen.  
  
  
