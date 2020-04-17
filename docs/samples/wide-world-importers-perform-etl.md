---
title: WideWorldImportersDW - ETL-Workflow | Microsoft Docs
description: Verwenden Sie das ETL-Paket mit SQL Server Integration Services (SSIS), um Daten regelmäßig aus der WideWorldImporters-Datenbank in die WideWorldImportersDW zu migrieren.
ms.prod: sql
ms.prod_service: sql
ms.technology: samples
ms.custom: ''
ms.date: 04/04/2018
ms.reviewer: ''
ms.topic: conceptual
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 98ce2b9aa11b2e1381da1f16455df8a2c0d3f243
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2020
ms.locfileid: "81487429"
---
# <a name="wideworldimportersdw-etl-workflow"></a>WideWorldImportersDW ETL-Workflow
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
Verwenden Sie das *WWI_Integration* ETL-Pakets, um Daten aus der WideWorldImporters-Datenbank in die WideWorldImportersDW-Datenbank zu migrieren, wenn sich die Daten ändern. Das Paket wird regelmäßig (in der Regel täglich) ausgeführt.

Das Paket stellt eine hohe Leistung sicher, indem SQL Server Integration Services verwendet wird, um Massen-T-SQL-Vorgänge zu orchestrieren (anstelle separater Transformationen in Integration Services).

Dimensionen werden zuerst geladen, und dann werden Faktentabellen geladen. Sie können das Paket jederzeit nach einem Fehler erneut ausführen.

Der Workflow sieht wie folgt aus:

 ![WideWorldImporters ETL-Workflow](media/wide-world-importers/wideworldimporters-etl-workflow.png)

Der Workflow beginnt mit einer Ausdrucksaufgabe, die die entsprechende Cutoff-Zeit bestimmt. Die Cutoff-Zeit ist die aktuelle Zeit minus ein paar Minuten. (Dieser Ansatz ist robuster als das Anfordern von Daten direkt auf die aktuelle Zeit.) Alle Millisekunden werden von der Zeit abgeschnitten.

Die Hauptverarbeitung beginnt mit dem Auffüllen der Datumsdimensionstabelle. Die Verarbeitung stellt sicher, dass alle Datumsangaben für das aktuelle Jahr in der Tabelle ausgefüllt wurden.

Als Nächstes lädt eine Reihe von Datenflussaufgaben jede Dimension. Dann laden sie jede Tatsache.

## <a name="prerequisites"></a>Voraussetzungen

- SQL Server 2016 (oder höher) mit den WideWorldImporters- und WideWorldImportersDW-Datenbanken (in derselben oder in verschiedenen Instanzen von SQL Server)
- SQL Server Management Studio
- SQL Server 2016 Integration Services
  - Stellen Sie sicher, dass Sie einen Integration Services-Katalog erstellen. Um einen Integration Services-Katalog zu erstellen, klicken Sie im SQL Server Management Studio-Objekt-Explorer mit der rechten Maustaste auf **Integration Services**, und wählen Sie dann **Katalog hinzufügen**aus. Lassen Sie die Standardoptionen. Sie werden aufgefordert, SQLCLR zu aktivieren und ein Kennwort anzugeben.


## <a name="download"></a>Download

Die neueste Version des Beispiels finden Sie unter [Wide-World-Importers-release](https://go.microsoft.com/fwlink/?LinkID=800630). Laden Sie die *Paketdatei Daily ETL.ispac* Integration Services herunter.

Informationen zum erneuten Erstellen der Beispieldatenbank finden Sie unter [Wide-World-Importer](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/wide-world-importers/wwi-ssis).

## <a name="install"></a>Installieren

1. Stellen Sie das Integration Services-Paket bereit:
   1. Öffnen Sie im Windows Explorer das *Paket Daily ETL.ispac.* Dadurch wird der SQL Server Integration Services-Bereitstellungs-Assistent gestartet.
   2. Folgen Sie unter **Quelle auswählen**die Standardeinstellungen für die Projektbereitstellung, wobei der Pfad auf das Paket Daily *ETL.ispac* verweist.
   3. Geben Sie unter **Ziel auswählen**den Namen des Servers ein, auf dem der Integration Services-Katalog gehostet wird.
   4. Wählen Sie einen Pfad unter dem Integration Services-Katalog aus, z. B. in einem neuen Ordner mit dem Namen *WideWorldImporters*.
   5. Wählen Sie **Bereitstellen** aus, um den Assistenten abzuschließen.

2. Erstellen Sie einen SQL Server-Agent-Auftrag für den ETL-Prozess:
   1. Klicken Sie in Management Studio mit der rechten Maustaste auf **SQL Server Agent**, und wählen Sie dann **Neuer** > **Auftrag aus.**
   2. Geben Sie einen Namen ein, z. B. *WideWorldImporters ETL*.
   3. Fügen Sie einen **Auftragsschritt** vom Typ **SQL Server Integration Services Package**hinzu.
   4. Wählen Sie den Server mit dem Integration Services-Katalog aus, und wählen Sie dann das *tägliche ETL-Paket* aus.
   5. Stellen Sie unter > **Konfigurationsverbindungs-Manager**sicher, dass die Verbindungen zur Quelle und zum Ziel ordnungsgemäß konfiguriert sind. **Configuration** Standardmäßig wird eine Verbindung mit der lokalen Instanz hergestellt.
   6. Wählen Sie **OK** aus, um den Auftrag zu erstellen.

3. Führen Sie den Auftrag aus oder planen Sie ihn.
