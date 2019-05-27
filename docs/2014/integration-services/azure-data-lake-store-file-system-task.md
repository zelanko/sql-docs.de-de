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
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 69a521cb72e68141f5706f5187a0288a3f44f241
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66061376"
---
# <a name="azure-data-lake-store-file-system-task"></a>Azure Data Lake Store-Task „Dateisystem“

Die **Azure Data Lake Store-Dateisystemtask** ermöglicht Benutzern das Ausführen verschiedener Dateisystemvorgänge für [Azure Data Lake Store (ADLS)](https://azure.microsoft.com/services/data-lake-store/).

Ziehen Sie den Azure Data Lake Store-Task „Dateisystem“ von der SSIS-Toolbox in die Designercanvas, um diesen zu einem Paket hinzuzufügen. Klicken Sie dann doppelklicken Sie auf der Aufgabe oder mit der rechten Maustaste in der Aufgabe und wählen Sie **bearbeiten**, um das Dialogfeld des Task-Editor zu öffnen.

Mit der **Operation**-Eigenschaft wird der auszuführende Dateisystemvorgang angegeben. Die folgenden Vorgänge werden unterstützt.

* **CopyToADLS:** Dateien in ADLS hochladen.
* **CopyFromADLS:** Dateien aus ADLS herunterladen.

Sie müssen für jeden Vorgang einen Azure Data Lake-Verbindungs-Manager angeben.

Hier sind die Beschreibungen der Eigenschaften für jeden Vorgang spezifisch.

## <a name="copytoadls"></a>CopyToADLS

* **LocalDirectory:** Gibt das Quellverzeichnis, das hochzuladenden Dateien enthält.
* **FileNamePattern:** Legt einen Dateinamensfilter für Quelldateien fest. Nur Dateien, deren Name mit dem angegebenen Muster übereinstimmt, werden hochgeladen werden. Die Platzhalterzeichen `*` und `?` werden unterstützt.
* **SearchRecursively:** Gibt an, ob das Quellverzeichnis rekursiv nach hochzuladenden Dateien durchsucht werden soll.
* **AzureDataLakeDirectory:** Gibt das ADLS-Zielverzeichnis an, in das Dateien hochgeladen werden.
* **FileExpiry:** Gibt ein Ablaufdatum und die Uhrzeit für die Dateien in ADLS hochgeladen, oder lassen Sie diese Eigenschaft ist leer, um anzugeben, dass die Dateien nie ablaufen.

## <a name="copyfromadls"></a>CopyFromADLS

* **AzureDataLakeDirectory:** Gibt das ADLS-Quellverzeichnis an, das die herunterzuladenden Dateien enthält.
* **SearchRecursively:** Gibt an, ob das Quellverzeichnis rekursiv nach herunterzuladende Dateien durchsucht werden soll.
* **LocalDirectory:** Gibt das Zielverzeichnis an, in dem heruntergeladene Dateien gespeichert werden.
