---
title: Übersicht über die Migration von SQL Server Integration Services zu Azure | Microsoft-Dokumentation
description: In diesem Artikel werden der Migrationsprozess von SQL Server Integration Services zu Azure sowie die dafür erforderlichen Tools beschrieben.
ms.date: 04/10/2020
ms.topic: conceptual
ms.prod: sql
ms.prod_service: integration-services
ms.custom: ''
ms.technology: integration-services
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7bf5aa9ee503dff3a00053365485c3ef70cc9247
ms.sourcegitcommit: 777704aefa7e574f4b7d62ad2a4c1b10ca1731ff
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/06/2020
ms.locfileid: "87823264"
---
# <a name="migrate-on-premises-ssis-workloads-to-ssis-in-adf"></a>Migrieren von lokalen SSIS-Workloads zu SSIS in ADF

Dieser Artikel enthält Informationen zum Migrationsprozess von SQL Server Integration Services-Workloads (SSIS) zu SSIS in ADF sowie die erforderlichen Tools.

In der [Übersicht zur Migration](https://docs.microsoft.com/azure/data-factory/scenario-ssis-migration-overview) wird der gesamte Migrationsprozess Ihrer ETL-Workloads von lokalen SSIS zu SSIS in ADF beschrieben.

Der Migrationsprozess besteht aus zwei Phasen: [Bewertung](https://docs.microsoft.com/azure/data-factory/scenario-ssis-migration-overview#assessment) und [Migration](https://docs.microsoft.com/azure/data-factory/scenario-ssis-migration-overview#migration).

## <a name="assessment"></a>Bewertung

Der Datenmigrations-Assistent (DMA) ist ein zu diesem Zweck frei herunterladbares Tool, das lokal installiert und ausgeführt werden kann. Das DMA-Bewertungsprojekt vom Typ „Integration Services“ kann erstellt werden, um SSIS-Pakete in Batches zu bewerten und Kompatibilitätsprobleme zu identifizieren.

Hier können Sie den [Datenbankmigrations-Assistenten](https://docs.microsoft.com/sql/dma/dma-overview) abrufen und eine [Paketbewertung](https://docs.microsoft.com/sql/dma/dma-assess-ssis) durchführen.

## <a name="migration"></a>Migration

In Abhängigkeit von den Speichertypen der SSIS-Quellpakete und dem Migrationsziel der Datenbankworkloads können die Schritte für die Migration von SSIS-Paketen und SQL Server-Agent-Aufträgen variieren, die die Ausführung von SSIS-Paketen planen. Weitere Informationen finden Sie auf [dieser Seite](https://docs.microsoft.com/azure/data-factory/scenario-ssis-migration-overview#migration).

## <a name="next-steps"></a>Nächste Schritte

- [Migrieren von SSIS-Paketen zu Azure SQL Managed Instance](https://docs.microsoft.com/azure/dms/how-to-migrate-ssis-packages-managed-instance)
- [Migrieren von SSIS-Aufträgen zu Azure Data Factory (ADF) mit SQL Server Management Studio (SSMS)](https://docs.microsoft.com/azure/data-factory/how-to-migrate-ssis-job-ssms)
