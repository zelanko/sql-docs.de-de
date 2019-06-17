---
title: Flexibler Dateitask | Microsoft-Dokumentation
ms.custom: ''
ms.date: 05/22/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- SQL13.DTS.DESIGNER.AFPEXTFILETASK.F1
- SQL14.DTS.DESIGNER.AFPEXTFILETASK.F1
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 2d01304a36f7676f53ffef3f6c6e3c600cb87cb6
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66411097"
---
# <a name="flexible-file-task"></a>Flexibler Dateitask

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]

Der flexible Dateitask ermöglicht Benutzern das Ausführen von Dateivorgängen für verschiedene unterstützte Speicherdienste.
Zurzeit unterstützte Speicherdienste:

- Lokales Dateisystem
- [Azure Blob Storage](https://azure.microsoft.com/services/storage/blobs/)
- [Azure Data Lake Storage Gen2](https://docs.microsoft.com/azure/storage/blobs/data-lake-storage-introduction)

Der flexible Dateitask ist eine Komponente des [SQL Server Integration Services Feature Pack (SSIS) für Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md).

Ziehen Sie den flexiblen Dateitask aus der SSIS-Toolbox auf die Designercanvas, um diesen einem Paket hinzuzufügen. Doppelklicken Sie anschließend auf den Task, oder klicken Sie mit der rechten Maustaste darauf, und klicken Sie auf **Bearbeiten**, um das Dialogfeld **Flexibler Dateitask-Editor** zu öffnen.

Mit der **Operation**-Eigenschaft wird der auszuführende Dateivorgang angegeben.
Nur der **Kopiervorgang** wird zurzeit unterstützt.

Die folgenden Eigenschaften sind für den **Kopiervorgang** verfügbar.

- **SourceConnectionType:** Gibt den Typ des Quellverbindungs-Managers an.
- **SourceConnection:** Gibt den Quellverbindungs-Manager an.
- **SourceFolderPath:** Gibt den Pfad des Quellordners an.
- **SourceFileName:** Gibt den Namen der Quelldatei an. Wenn diese Angabe leer gelassen wird, wird der Quellordner kopiert.
- **SearchRecursively:** Gibt an, ob Unterordner rekursiv kopiert werden sollen.
- **DestinationConnectionType:** Gibt den Typ des Zielverbindungs-Managers an.
- **DestinationConnection:** Gibt den Zielverbindungs-Manager an.
- **DestinationFolderPath:** Gibt den Pfad des Zielordners an.
- **DestinationFileName:** Gibt den Namen der Zieldatei an.
