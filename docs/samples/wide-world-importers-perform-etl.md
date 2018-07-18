---
title: "\"Wideworldimportersdw\" - ETL-Workflow | Microsoft-Dokumentation"
ms.prod: sql
ms.prod_service: sql
ms.technology: samples
ms.custom: ''
ms.date: 04/04/2018
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 36638c4cc2bda58ac277822d5c4a4ce5421ab8b4
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2018
ms.locfileid: "38066528"
---
# <a name="wideworldimportersdw-etl-workflow"></a>WideWorldImportersDW ETL-workflow
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
Verwenden der *WWI_Integration* ETL-Pakets zum Migrieren von Daten aus der Datenbank "wideworldimporters" in der Datenbank "wideworldimportersdw" Wenn sich Daten ändern. Das Paket in regelmäßigen Abständen ausgeführt wird (in der Regel täglich).

Das Paket wird eine hohe Leistung mithilfe von SQL Server Integration Services zum orchestrieren von T-SQL-Massenvorgänge (anstelle von separaten Transformationen in Integration Services) sichergestellt.

Dimensionen werden zuerst geladen, und klicken Sie dann die Faktentabellen werden geladen. Sie können das Paket erneut einem beliebigen Zeitpunkt nach einem Fehler ausführen.

Der Workflow sieht folgendermaßen aus:

 ![WideWorldImporters-ETL-workflow](media/wide-world-importers/wideworldimporters-etl-workflow.png)

Der Workflow beginnt mit einem Task "Ausdruck", die das Umstellungsjahr für Angaben mit geeigneten Zeitpunkt bestimmt. Das Umstellungsjahr für Angaben mit wird die aktuelle Zeit minus ein paar Minuten. (Dieser Ansatz ist robuster als die Daten direkt auf die aktuelle Zeit anfordern.) Alle Millisekunden werden ab dem Zeitpunkt abgeschnitten.

Die wichtigsten Verarbeitung beginnt mit dem Auffüllen der Tabelle Date-Dimension. Die Verarbeitung wird sichergestellt, dass alle Datumsangaben für das aktuelle Jahr in der Tabelle aufgefüllt wurden.

Als Nächstes lädt eine Reihe von Datenflusstasks jeder Dimension. Dann laden sie jede Faktentabelle aus.

## <a name="prerequisites"></a>Erforderliche Komponenten

- SQLServer 2016 (oder höher) mit den Datenbanken "wideworldimporters" und "wideworldimportersdw" (in der gleichen oder in verschiedenen Instanzen von SQL Server)
- SQL Server Management Studio
- SQL Server 2016 Integration Services
  - Stellen Sie sicher, dass Sie einen Integration Services-Katalog erstellen. Um Integration Services-Katalog, in Objekt-Explorer von SQL Server Management Studio zu erstellen, mit der rechten Maustaste **Integrationsdienste**, und wählen Sie dann **Add Catalog**. Lassen Sie die Standardoptionen aus. Sie werden aufgefordert, zum Aktivieren von SQLCLR, und geben Sie ein Kennwort.


## <a name="download"></a>Herunterladen

Die neueste Version des Beispiels, finden Sie unter [Wide-Welt-Importer-Release](http://go.microsoft.com/fwlink/?LinkID=800630). Herunterladen der *tägliche ETL.ispac* Integration Services-Paketdatei.

Der Quellcode zum Neuerstellen der-Beispieldatenbank, finden Sie unter [Wide-Welt-Importers](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/wide-world-importers/wwi-integration-etl).

## <a name="install"></a>Install

1. Stellen Sie das Integration Services-Paket:
   1. Öffnen Sie im Windows Explorer die *tägliche ETL.ispac* Paket. Dadurch wird die SQL Server Integration Services-Bereitstellungs-Assistent gestartet.
   2. Klicken Sie unter **Quelle auswählen**, befolgen Sie die Standardwerte für die Bereitstellung von Projekten, mit dem Pfad, der auf die *tägliche ETL.ispac* Paket.
   3. Klicken Sie unter **Ziel auswählen**, geben Sie den Namen des Servers, der den Integration Services-Katalog hostet.
   4. Wählen Sie einen Pfad unter dem Integration Services-Katalog, z. B. in einem neuen Ordner mit dem Namen *"wideworldimporters"*.
   5. Wählen Sie **bereitstellen** um den Assistenten abzuschließen.

2. Erstellen eines SQL Server-Agent-Auftrags für ETL-Prozess:
   1. In Management Studio, mit der Maustaste **SQL Server-Agent**, und wählen Sie dann **neu** > **Auftrag**.
   2. Geben Sie einen Namen ein, z. B. *WideWorldImporters ETL*.
   3. Hinzufügen einer **Auftragsschritt** des Typs **SQL Server Integration Services-Paket**.
   4. Wählen Sie den Server mit Integration Services-Katalog, und wählen Sie dann die *tägliche ETL* Paket.
   5. Klicken Sie unter **Konfiguration** > **Verbindungs-Manager**, stellen Sie sicher, dass die Verbindungen mit den Quell- und Zielservern richtig konfiguriert sind. Der Standardwert ist eine Verbindung mit der lokalen Instanz herstellen.
   6. Wählen Sie **OK** zum Erstellen des Auftrags.

3. Führen Sie aus, oder planen Sie den Auftrag.
