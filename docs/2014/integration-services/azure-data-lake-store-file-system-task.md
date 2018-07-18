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
ms.topic: conceptual
f1_keywords:
- SQL12.DTS.DESIGNER.AFPADLSTASK.F1
- SQL11.DTS.DESIGNER.AFPADLSTASK.F1
ms.assetid: 02b9edd7-6ef9-463e-abbf-e1830bcae875
caps.latest.revision: 3
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 768113129fd380d335895364344742eb9bb8e791
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37292850"
---
# <a name="azure-data-lake-store-file-system-task"></a>Azure Data Lake Store-Task „Dateisystem“
Die **Azure Data Lake Store-Dateisystemtask** ermöglicht Benutzern das Ausführen verschiedener Dateisystemvorgänge für [Azure Data Lake Store (ADLS)](https://azure.microsoft.com/en-us/services/data-lake-store/).

Ziehen Sie den Azure Data Lake Store-Task „Dateisystem“ von der SSIS-Toolbox in die Designercanvas, um diesen zu einem Paket hinzuzufügen. Klicken Sie dann doppelklicken Sie auf der Aufgabe oder mit der rechten Maustaste in der Aufgabe und wählen Sie **bearbeiten**, um das Dialogfeld des Task-Editor zu öffnen.

Mit der **Operation**-Eigenschaft wird der auszuführende Dateisystemvorgang angegeben. Die folgenden Vorgänge werden unterstützt.

* **CopyToADLS:** Hochladen von Dateien in ADLS.
* **CopyFromADLS:** Herunterladen von Dateien von ADLS.

Sie müssen für jeden Vorgang einen Azure Data Lake-Verbindungs-Manager angeben.

Hier sind die Beschreibungen der Eigenschaften für jeden Vorgang spezifisch.

## <a name="copytoadls"></a>CopyToADLS
* **LocalDirectory:** gibt das Quellverzeichnis der hochzuladenden Dateien enthält.
* **FileNamePattern:** legt einen Dateinamensfilter für Quelldateien fest Nur Dateien, deren Name mit dem angegebenen Muster übereinstimmt, werden hochgeladen werden. Die Platzhalterzeichen `*` und `?` werden unterstützt.
* **SearchRecursively:** gibt an, ob das Quellverzeichnis rekursiv nach hochzuladenden Dateien durchsucht werden soll
* **AzureDataLakeDirectory:** gibt das ADLS-Zielverzeichnis an, in das Dateien hochgeladen werden
* **FileExpiry:** ein Ablaufdatum und die Uhrzeit angibt, für die Dateien in ADLS hochgeladen, oder lassen Sie diese Eigenschaft ist leer, um anzugeben, dass die Dateien nie ablaufen.

## <a name="copyfromadls"></a>CopyFromADLS
* **AzureDataLakeDirectory:** gibt das ADLS-Quellverzeichnis an, das die herunterzuladenden Dateien enthält
* **SearchRecursively:** gibt an, ob das Quellverzeichnis rekursiv nach herunterzuladenden Dateien durchsucht werden soll
* **LocalDirectory:** gibt das Zielverzeichnis an, in dem heruntergeladene Dateien gespeichert werden
