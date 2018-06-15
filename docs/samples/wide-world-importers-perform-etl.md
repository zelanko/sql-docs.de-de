---
title: WideWorldImportersDW - ETL-Workflows | Microsoft Docs
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
ms.sourcegitcommit: 7019ac41524bdf783ea2c129c17b54581951b515
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2018
ms.locfileid: "34467686"
---
# <a name="wideworldimportersdw-etl-workflow"></a>WideWorldImportersDW ETL-Workflows
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
Verwenden der *WWI_Integration* ETL-Pakets zum Migrieren von Daten aus der Datenbank "wideworldimporters" in der Datenbank WideWorldImportersDW datenänderungen. Das Paket in regelmäßigen Abständen ausgeführt wird (in der Regel täglich).

Das Paket wird sichergestellt, dass hohen Leistung mithilfe von SQL Server Integration Services zum orchestrieren von Massenvorgängen T-SQL (anstelle von separaten Transformationen in Integration Services).

Dimensionen werden zuerst geladen, und klicken Sie dann Faktentabellen geladen werden. Sie können das Paket erneut einem beliebigen Zeitpunkt nach einem Fehler ausführen.

Der Workflow sieht folgendermaßen aus:

 ![WideWorldImporters ETL-Workflows](media/wide-world-importers/wideworldimporters-etl-workflow.png)

Der Workflow beginnt mit einem Task "Ausdruck", die das Umstellungsjahr für Angaben mit geeigneten Zeitpunkt bestimmt. Umstellungsjahr für Angaben mit ist die aktuelle Zeit minus ein paar Minuten. (Dieser Ansatz ist robuster als das Anfordern von Daten direkt auf die aktuelle Zeit.) Ab dem Zeitpunkt werden alle Millisekunden gekürzt.

Die hauptverarbeitung, die durch Auffüllen der Tabelle Date-Dimension wird gestartet. Die Verarbeitung wird sichergestellt, dass alle Datumsangaben für das laufende Jahr in der Tabelle aufgefüllt wurden.

Als Nächstes lädt eine Reihe von Datenflusstasks jeder Dimension. Laden sie dann jedes Faktum.

## <a name="prerequisites"></a>Erforderliche Komponenten

- SQLServer 2016 (oder höher) mit den Datenbanken "wideworldimporters" und WideWorldImportersDW (in derselben oder in verschiedenen Instanzen von SQL Server)
- SQL Server Management Studio
- SQL Server 2016 Integration Services
  - Stellen Sie sicher, dass Sie einen Integration Services-Katalog erstellen. Um ein Integration Services-Katalog im Objekt-Explorer von SQL Server Management Studio zu erstellen, Maustaste **Integration Services**, und wählen Sie dann **Add Catalog**. Lassen Sie die Standardoptionen. Sie werden aufgefordert, zum Aktivieren von SQLCLR und ein Kennwort angeben.


## <a name="download"></a>Herunterladen

Die neueste Version des Beispiels, finden Sie unter [Wide World Importers Version](http://go.microsoft.com/fwlink/?LinkID=800630). Herunterladen der *tägliche ETL.ispac* Integration Services-Paketdatei.

Der Quellcode zum Neuerstellen der-Beispieldatenbank, finden Sie unter [Wide-World-Importers](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/wide-world-importers/wwi-integration-etl).

## <a name="install"></a>Install

1. Bereitstellen Sie das Integration Services-Paket:
   1. Öffnen Sie im Windows-Explorer die *tägliche ETL.ispac* Paket. Dadurch wird die SQL Server Integration Services-Bereitstellungs-Assistent gestartet.
   2. Klicken Sie unter **Quelle auswählen**, befolgen Sie die Standardwerte für eine Bereitstellung von Projekten mit dem Pfad verweist auf die *tägliche ETL.ispac* Paket.
   3. Klicken Sie unter **Ziel auswählen**, geben Sie den Namen des Servers, der den Integration Services-Katalog hostet.
   4. Wählen Sie einen Pfad unter dem Integration Services-Katalog, z. B. in einen neuen Ordner namens *"wideworldimporters"*.
   5. Wählen Sie **bereitstellen** um den Assistenten zu beenden.

2. Erstellen Sie einen SQL Server-Agent-Auftrag für ETL-Prozess:
   1. In Management Studio, mit der Maustaste **SQL Server-Agent**, und wählen Sie dann **neu** > **Auftrag**.
   2. Geben Sie einen Namen, z. B. *WideWorldImporters ETL*.
   3. Hinzufügen einer **Auftragsschritt** des Typs **SQL Server Integration Services-Paket**.
   4. Wählen Sie den Server mit Integration Services-Katalog, und wählen Sie dann die *tägliche ETL* Paket.
   5. Klicken Sie unter **Konfiguration** > **Verbindungs-Manager**, stellen Sie sicher, dass die Verbindungen mit den Quell- und Zielservern richtig konfiguriert sind. Der Standardwert ist eine Verbindung mit der lokalen Instanz herstellen.
   6. Wählen Sie **OK** zur Erstellung des Auftrags.

3. Führen Sie aus, oder planen Sie des Auftrags.
