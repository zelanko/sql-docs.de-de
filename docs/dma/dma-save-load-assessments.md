---
title: Speichern und Laden von Bewertungen mit Datenmigrations-Assistent
description: Erfahren Sie, wie Sie mit Datenmigrations-Assistent Bewertungen speichern und laden.
ms.date: 01/10/2020
ms.prod: sql
ms.prod_service: dma
ms.reviewer: ''
ms.technology: dma
ms.topic: conceptual
keywords: ''
helpviewer_keywords:
- Data Migration Assistant, Assess
ms.assetid: ''
author: HJToland3
ms.author: rajpo
ms.custom: seo-lt-2019
ms.openlocfilehash: 995b6b131d9e65ca7a91ce9053583a036fd80fbb
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "75840519"
---
# <a name="save-and-load-assessments-with-data-migration-assistant"></a>Speichern und Laden von Bewertungen mit Datenmigrations-Assistent

Die folgenden Schritt-für-Schritt-Anweisungen helfen Ihnen bei der Verwendung des Datenmigrations-Assistent v 5.0 oder höher, um eine Daten Bank Bewertung in einer Datei zu speichern und dann eine Bewertung aus einer Datei zu laden.

> [!NOTE]
> Zusätzlich zum Laden von Bewertungen, die mit der neuesten Version von DMA gespeichert wurden, können Benutzer diese Funktion auch zum Laden von Bewertungen nutzen, die als JSON-Dateien aus früheren Versionen von Datenmigrations-Assistent exportiert wurden, um die Ergebnisse in Version 5.0 und höher anzuzeigen.

## <a name="saving-an-assessment-to-a-file"></a>Speichern einer Bewertung in einer Datei

1. Wählen Sie nach dem Ausführen einer Bewertung mithilfe Datenmigrations-Assistent die Option **Bewertung speichern**aus.

   ![Öffnen des Dialog Felds "Bewertung speichern"](../dma/media/dma-save-load-assessments/dma-open-save-dialog.png)

   Der Standard **Speicher...** Das Dialogfeld wird angezeigt.

   > [!NOTE]
   > Weitere Informationen zum Ausführen einer Bewertung in Datenmigrations-Assistent finden Sie im Artikel [Durchführen einer SQL Server Migrations Bewertung mit Datenmigrations-Assistent](../dma/dma-assesssqlonprem.md).

2. Geben Sie einen Namen für die Datei an, und klicken Sie dann auf **Speichern**.

   ![Benennen und Speichern einer Bewertungs Datei](../dma/media/dma-save-load-assessments/dma-name-save-assessment.png)

## <a name="loading-an-assessment-saved-to-a-file"></a>Laden einer in eine Datei gespeicherten Bewertung

1. Zum Laden einer Bewertung, die Sie zuvor in einer Datei gespeichert haben, starten Sie Datenmigrations-Assistent, und wählen Sie dann auf der Registerkarte **Alle Bewertungen** die Option **Auslastungs Bewertung**aus.

   ![Öffnen des Dialog Felds "Auslastungs Bewertung"](../dma/media/dma-save-load-assessments/dma-open-load-dialog.png)

2. Navigieren Sie zur gespeicherten Bewertungs Datei, die Sie laden möchten, wählen Sie die Datei aus, und wählen Sie dann **Öffnen**aus.

   ![Öffnen einer Bewertungs Datei](../dma/media/dma-save-load-assessments/dma-open-assessment.png)

   Ein Eintrag für die von Ihnen geladene Bewertung wird auf der Registerkarte **Alle Bewertungen** angezeigt.

   ![Anzeigen des Bewertungs Eintrags](../dma/media/dma-save-load-assessments/dma-display-assessment-entry.png)

3. Wählen Sie den Eintrag Bewertung aus, und wählen Sie dann **Bewertung öffnen**aus.

   ![Öffnen der Bewertungs Details](../dma/media/dma-save-load-assessments/dma-open-assessment-detail.png)

   Datenmigrations-Assistent zeigt jetzt Details der Bewertung an, die Sie zuvor ausgeführt haben.

   ![Anzeigen von Bewertungs Details](../dma/media/dma-save-load-assessments/dma-display-assessment-detail.png)
