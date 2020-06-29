---
title: Azure Data Lake Store-Task „Dateisystem“ | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/09/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- SQL12.DTS.DESIGNER.AFPADLSTASK.F1
- SQL11.DTS.DESIGNER.AFPADLSTASK.F1
ms.assetid: 02b9edd7-6ef9-463e-abbf-e1830bcae875
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 2d01c61521bf746076b359c65103e0ea46ec0f1b
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/26/2020
ms.locfileid: "85439407"
---
# <a name="azure-data-lake-store-file-system-task"></a>Azure Data Lake Store-Task „Dateisystem“

Der **Task "Azure Data Lake Store Dateisystem** " ermöglicht es Benutzern, verschiedene Dateisystem Vorgänge auf [Azure Data Lake Store (ADLS)](https://azure.microsoft.com/services/data-lake-store/)auszuführen.

Ziehen Sie den Azure Data Lake Store-Task „Dateisystem“ von der SSIS-Toolbox in die Designercanvas, um diesen zu einem Paket hinzuzufügen. Doppelklicken Sie auf den Task, oder klicken Sie mit der rechten Maustaste auf den Task, und wählen Sie **Bearbeiten**aus, um das Dialogfeld Task-Editor zu öffnen.

Mit der **Operation**-Eigenschaft wird der auszuführende Dateisystemvorgang angegeben. Die folgenden Operatoren werden unterstützt:

* **CopyToADLS:** Hochladen von Dateien in ADLS.
* **CopyFromADLS:** Herunterladen von Dateien von ADLS.

Sie müssen für jeden Vorgang einen Azure Data Lake-Verbindungs-Manager angeben.

Hier sind die Beschreibungen der Eigenschaften, die für jeden Vorgang spezifisch sind.

## <a name="copytoadls"></a>CopyToADLS

* **Localdirectory:** Gibt das Quellverzeichnis an, das hoch zuladende Dateien enthält.
* **FileNamePattern:** legt einen Dateinamensfilter für Quelldateien fest Nur Dateien, deren Name mit dem angegebenen Muster übereinstimmt, werden hochgeladen. Die Platzhalterzeichen `*` und `?` werden unterstützt.
* **SearchRecursively:** gibt an, ob das Quellverzeichnis rekursiv nach hochzuladenden Dateien durchsucht werden soll
* **AzureDataLakeDirectory:** gibt das ADLS-Zielverzeichnis an, in das Dateien hochgeladen werden
* **Datei Ablauf:** Gibt ein Ablaufdatum und eine Uhrzeit für die in ADLS hochgeladenen Dateien an, oder lassen Sie diese Eigenschaft leer, um anzugeben, dass die Dateien nie ablaufen.

## <a name="copyfromadls"></a>CopyFromADLS

* **AzureDataLakeDirectory:** gibt das ADLS-Quellverzeichnis an, das die herunterzuladenden Dateien enthält
* **SearchRecursively:** gibt an, ob das Quellverzeichnis rekursiv nach herunterzuladenden Dateien durchsucht werden soll
* **LocalDirectory:** gibt das Zielverzeichnis an, in dem heruntergeladene Dateien gespeichert werden
