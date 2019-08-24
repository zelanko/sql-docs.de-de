---
title: Durchführen einer SQL Server Integration Service-Migrations Bewertung (Datenmigrations-Assistent) | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie Datenmigrations-Assistent zum Auswerten eines lokalen SQL Server Integration Service vor der Migration zu einer Azure SQL-Datenbank oder einer verwalteten Azure SQL-Datenbank-Instanz verwenden.
ms.custom: ''
ms.date: 08/23/2019
ms.prod: sql
ms.prod_service: dma
ms.reviewer: ''
ms.technology: dma
ms.topic: conceptual
keywords: ''
helpviewer_keywords:
- Data Migration Assistant, Assess
ms.assetid: ''
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 14e53b3820e784916484cbe6a15ba82cd2ed5c8e
ms.sourcegitcommit: 01c8df19cdf0670c02c645ac7d8cc9720c5db084
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/23/2019
ms.locfileid: "70001372"
---
# <a name="perform-a-sql-server-integration-service-migration-assessment-with-data-migration-assistant"></a>Durchführen einer SQL Server Integration Service-Migrations Bewertung mit Datenmigrations-Assistent

Die folgenden schrittweisen Anweisungen unterstützen Sie bei der ersten Bewertung der Migration von SSIS-Paketen (SQL Server Integration Service) zu Azure SQL-Datenbank oder einer verwalteten Azure SQL-Datenbank-Instanz mithilfe von Datenmigrations-Assistent.

## <a name="create-an-assessment"></a>Erstellen einer Bewertung

1. Wählen Sie das Symbol **neu** (+) aus, und wählen Sie dann den Projekttyp **Bewertung** als **Integrations Dienst**aus.

1. Legen Sie den Quell-und Ziel Servertyp fest.

    Wählen Sie die Quelle als **SQL Server**aus, und legen Sie den Ziel Servertyp als **Azure SQL-Datenbank** oder **verwaltete Azure SQL-Datenbank-Instanz**fest.

1. Klicken Sie auf **Erstellen**.

    ![Bewertung erstellen](media/dma-assess-ssis/dma-assess-ssis-create.png)

## <a name="add-sources-to-assess"></a>Hinzufügen von Quellen zur Bewertung

1. Befolgen Sie die Standardoption, und klicken Sie auf **weiter** , um **Quellen auszuwählen**.

1. Geben Sie den SQL Server-Instanznamen ein, wählen Sie den Authentifizierungstyp und die richtigen Verbindungs Eigenschaften
1. Geben Sie einen Ordner Pfad ein, der SSIS-Pakete enthält.
1. Geben Sie ggf. das Paket Verschlüsselungs Kennwort ein, und **verbinden**Sie
1. Wählen Sie das zu überprüfen Dateisystem aus, und klicken Sie dann auf **Hinzufügen**.
  ![Quelle hinzufügen](media/dma-assess-ssis/dma-assess-ssis-addsource.png)
1. Wählen Sie **Quellen hinzufügen** aus, um das Menü verbindungsflyout zu öffnen, wenn Sie mehrere Ordner bewerten müssen.
1. Klicken Sie auf **Bewertung starten**.
  ![Bewertung starten](media/dma-assess-ssis/dma-assess-ssis-assess.png)

## <a name="view-results"></a>Anzeigen der Ergebnisse

Die Kategorie Kompatibilitätsprobleme bietet teilweise unterstützte oder nicht unterstützte Funktionen, die die Migration von lokalen SSIS-Paketen zu Azure-SSIS Integration Runtime blockieren. Anschließend werden Empfehlungen bereitstellen, die Ihnen helfen, diese Probleme zu beheben.

![Anzeigen der Ergebnisse](media/dma-assess-ssis/dma-assess-ssis-result.png)

## <a name="next-steps"></a>Nächste Schritte

- [Migrieren von SQL Server Integration Services Paketen zu einer verwalteten Azure SQL-Datenbank-Instanz](https://docs.microsoft.com/en-us/azure/dms/how-to-migrate-ssis-packages-managed-instance)
- [Erneutes Bereitstellen von SQL Server Integration Services Paketen in Azure SQL-Datenbank](https://docs.microsoft.com/en-us/azure/dms/how-to-migrate-ssis-packages)
