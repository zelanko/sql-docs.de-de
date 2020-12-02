---
description: Azure Data Lake Store-Task „Dateisystem“
title: Azure Data Lake Store-Task „Dateisystem“ | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/22/2017
ms.prod: sql
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- SQL13.DTS.DESIGNER.AFPADLSTASK.F1
- SQL14.DTS.DESIGNER.AFPADLSTASK.F1
author: Lingxi-Li
ms.author: lingxl
ms.reviewer: maghan
ms.openlocfilehash: 27ee71393bfbad6c824de25bd95c9ca465cf2a51
ms.sourcegitcommit: 192f6a99e19e66f0f817fdb1977f564b2aaa133b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/25/2020
ms.locfileid: "96123645"
---
# <a name="azure-data-lake-store-file-system-task"></a>Azure Data Lake Store-Task „Dateisystem“

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]



Der Azure Data Lake Store-Task „Dateisystem“ ermöglicht Benutzern das Ausführen verschiedener Dateisystemvorgänge für [Azure Data Lake Store (ADLS)](https://azure.microsoft.com/services/data-lake-store/).

Der Azure Data Lake Store-Task „Dateisystem“ ist eine Komponente von [SQL Server Integration Services (SSIS) Feature Pack für Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md).

## <a name="configure-the-azure-data-lake-store-file-system-task"></a>Konfigurieren des Azure Data Lake Store-Tasks „Dateisystem“

Ziehen Sie den Azure Data Lake Store-Task „Dateisystem“ von der SSIS-Toolbox in die Designercanvas, um diesen zu einem Paket hinzuzufügen. Doppelklicken Sie anschließend auf den Task, oder klicken Sie mit der rechten Maustaste darauf, und klicken Sie auf **Bearbeiten**, um das Dialogfeld **Azure Data Lake Store File System Task Editor** (Azure Data Lake Store-Editor für den Task „Dateisystem“) zu öffnen.

Mit der **Operation**-Eigenschaft wird der auszuführende Dateisystemvorgang angegeben. Wählen Sie einen der folgenden Vorgänge aus:

- **CopyToADLS:** Hochladen von Dateien in ADLS.
- **CopyFromADLS:** Herunterladen von Dateien von ADLS.

## <a name="configure-the-properties-for-the-operation"></a>Konfigurieren der Eigenschaften für den Vorgang
Sie müssen für jeden Vorgang einen Azure Data Lake-Verbindungs-Manager angeben.

Im Folgenden werden die Eigenschaften der jeweiligen Vorgänge beschrieben:

### <a name="copytoadls"></a>CopyToADLS
- **LocalDirectory:** gibt das lokale Quellverzeichnis an, das die hochzuladenden Dateien enthält
- **FileNamePattern:** legt einen Dateinamensfilter für Quelldateien fest Nur Dateien, deren Namen dem angegebenen Muster entsprechen, werden hochgeladen. Die Platzhalterzeichen `*` und `?` werden unterstützt.
- **SearchRecursively:** gibt an, ob das Quellverzeichnis rekursiv nach hochzuladenden Dateien durchsucht werden soll
- **AzureDataLakeDirectory:** gibt das ADLS-Zielverzeichnis an, in das Dateien hochgeladen werden
- **FileExpiry:** gibt ein Ablaufdatum und die Uhrzeit an, an dem bzw. zu der die Dateien in ADLS hochgeladen werden Geben Sie für diese Eigenschaft keinen Wert an, um festzulegen, dass Dateien über kein Ablaufdatum verfügen.

### <a name="copyfromadls"></a>CopyFromADLS
- **AzureDataLakeDirectory:** gibt das ADLS-Quellverzeichnis an, das die herunterzuladenden Dateien enthält
- **SearchRecursively:** gibt an, ob das Quellverzeichnis rekursiv nach herunterzuladenden Dateien durchsucht werden soll
- **LocalDirectory:** gibt das Zielverzeichnis an, in dem heruntergeladene Dateien gespeichert werden
