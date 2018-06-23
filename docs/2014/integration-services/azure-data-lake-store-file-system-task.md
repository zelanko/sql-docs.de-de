---
title: Azure Data Lake Store-Task „Dateisystem“ | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SQL12.DTS.DESIGNER.AFPADLSTASK.F1
- SQL11.DTS.DESIGNER.AFPADLSTASK.F1
ms.assetid: 02b9edd7-6ef9-463e-abbf-e1830bcae875
caps.latest.revision: 3
author: Lingxi-Li
ms.author: lingxl
manager: jhubbard
ms.openlocfilehash: 240780efd1b12596b0ebb6156ad98c508f0e8051
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36046476"
---
# <a name="azure-data-lake-store-file-system-task"></a>Azure Data Lake Store-Task „Dateisystem“
Die **Azure Data Lake-Speicher-Dateisystemtask** ermöglicht Benutzern das Ausführen von verschiedenen Dateisystemvorgänge auf [Azure Data Lake-Speicher (ADLS)](https://azure.microsoft.com/en-us/services/data-lake-store/).

Ziehen Sie den Azure Data Lake Store-Task „Dateisystem“ von der SSIS-Toolbox in die Designercanvas, um diesen zu einem Paket hinzuzufügen. Klicken Sie dann doppelklicken Sie auf die Aufgabe oder mit der rechten Maustaste in der Aufgabe und wählen Sie **bearbeiten**, um das Dialogfeld Task-Editor zu öffnen.

Mit der **Operation**-Eigenschaft wird der auszuführende Dateisystemvorgang angegeben. Die folgenden Vorgänge werden unterstützt.

* **CopyToADLS:** Hochladen von Dateien in ADLS.
* **CopyFromADLS:** Herunterladen von Dateien von ADLS.

Sie müssen für jeden Vorgang einen Azure Data Lake-Verbindungs-Manager angeben.

Hier sind die Beschreibungen der Eigenschaften für jeden Vorgang spezifisch.

## <a name="copytoadls"></a>CopyToADLS
* **LocalDirectory:** gibt das Quellverzeichnis der hochzuladenden Dateien enthält.
* **FileNamePattern:** legt einen Dateinamensfilter für Quelldateien fest Nur Dateien, deren Name mit das angegebene Muster übereinstimmt, werden hochgeladen werden. Die Platzhalterzeichen `*` und `?` werden unterstützt.
* **SearchRecursively:** gibt an, ob das Quellverzeichnis rekursiv nach hochzuladenden Dateien durchsucht werden soll
* **AzureDataLakeDirectory:** gibt das ADLS-Zielverzeichnis an, in das Dateien hochgeladen werden
* **FileExpiry:** ein Ablaufdatum und die Uhrzeit angibt, für die Dateien in ADLS hochgeladen, oder lassen diese Eigenschaft leer, um anzugeben, dass die Dateien nie ablaufen.

## <a name="copyfromadls"></a>CopyFromADLS
* **AzureDataLakeDirectory:** gibt das ADLS-Quellverzeichnis an, das die herunterzuladenden Dateien enthält
* **SearchRecursively:** gibt an, ob das Quellverzeichnis rekursiv nach herunterzuladenden Dateien durchsucht werden soll
* **LocalDirectory:** gibt das Zielverzeichnis an, in dem heruntergeladene Dateien gespeichert werden
