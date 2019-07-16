---
title: Wide World Importers - Beispieldatenbank für SQL | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: sql
ms.technology: samples
ms.custom: ''
ms.date: 04/04/2018
ms.reviewer: ''
ms.topic: conceptual
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c178d116dddb5dc18b1bec91066205fe08f6d0c0
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68067607"
---
# <a name="wide-world-importers-sample-databases-for-microsoft-sql"></a>Wide World Importers-Beispieldatenbanken für Microsoft SQL
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
Dies ist eine Übersicht über das fiktive Unternehmen Wide World Importers und die Workflows, die in der WideWorldImporters-Beispieldatenbanken für SQL Server und Azure SQL-Datenbank behoben werden.  

Wide World Importers (WWI) ist eine umfassende Neuheit waren Importer-Tool und dem Verteiler ausgeführt wird, aus der San Francisco Bay Area.

Großhändler sind "wwi" des Kunden größtenteils Unternehmen dar, die Personen zu verkaufen. "Wwi" verkauft Retail-Kunden in den USA einschließlich Specialty gespeichertes Supermärkten, computing, Speicher, die Anziehungskraft Shops Sport- und manche Benutzer. "Wwi" verkauft auch an andere Großhändler über ein Netzwerk von Agents, die die Produkte in der "wwi" Namen höher stufen. Während alle "wwi" des Kunden derzeit in den Vereinigten Staaten basieren, ist das Unternehmen beabsichtigten für eine Erweiterung in anderen Ländern zu übertragen.

"Wwi" erwirbt Waren von Lieferanten einschließlich Neuheit Spielzeug Hersteller und andere Neuheit Großhändler. Sie Kursdiagramme Waren in den "wwi" Warehouse und die neuanordnung von Lieferanten, nach Bedarf, um die kundenbestellungen zu erfüllen. Sie auch Verpackungsmaterial und große Datenmengen kaufen und verkaufen diese in kleinere Mengen zur Vereinfachung für den Kunden.

Erst kürzlich "wwi" um eine Vielzahl von genießbare Novelties wie z. B. Chilli Leben zu verkaufen.  Das Unternehmen zuvor keine gekühlt Elemente verarbeitet werden sollen. Nun müssen um Essen, die Verarbeitung von Anforderungen zu erfüllen, sie überwachen die Temperatur in ihre Chiller-Raum und alle ihre LKWs, die kältemaschine Abschnitte enthalten.

## <a name="workflow-for-warehouse-stock-items"></a>Workflow für die vorhandenen Warehouse-Elemente

Die typische Ablauf für bestückt und Verteilung wie Elemente lautet wie folgt aus:
- "Wwi" erstellt von Bestellungen und die Aufträge an den Lieferanten sendet.
- Lieferanten senden, die Elemente, "wwi" empfängt diese, und sie in ihrem Warehouse auf Lager hat.
- Kunden Auftragspositionen aus "wwi"
- "Wwi" füllt die kundenbestellung mit vorhandenen Elementen in das Warehouse und wenn sie nicht über ausreichende Stock verfügen, daher bestellen Sie die zusätzliche Aktie von den Lieferanten.
- Einige Kunden möchten nicht warten, dass der Elemente, die nicht auf Lager sind. Wenn sie z. B. fünf verschiedene bestellen vordefinierte Elemente und vier zur Verfügung stehen, werden die vier Elemente und der Rückstand den restlichen Artikel erhalten soll. Das Element würde sie weiter unten in einer separaten Lieferung gesendet werden.
- "Wwi" invoices Kunden für die vorhandenen Elemente in der Regel durch die Konvertierung von der Reihenfolge in eine Rechnung.
- Kunden können Elemente anordnen, die nicht auf Lager sind. Diese Elemente sind "nachgeliefert".
- "Wwi" bietet ein vorrätige Artikel entweder über ihre eigenen Lieferwagen oder über andere Kurieren oder der Freight-Methoden.
- Kunden bezahlen Rechnungen, um "wwi".
- In regelmäßigen Abständen zahlt "wwi" Lieferanten für Elemente, die auf Bestellungen wurden. Dies ist häufig einige Zeit nach dem Empfang der Wareneigentümers.

## <a name="data-warehouse-and-analysis-workflow"></a>Data Warehouses und Analysis-workflow

Während das Team bei "wwi" SQL Server Reporting Services verwenden, um die Berichte für operative aus der Datenbank "wideworldimporters" zu generieren, müssen sie auch zum Ausführen von Analysen für ihre Daten und strategische Berichte generieren müssen. Das Team haben ein dimensionales Data-Modell in einer Datenbank "wideworldimportersdw" erstellt. Diese Datenbank wird durch ein Integration Services-Paket aufgefüllt.

SQL Server Analysis Services wird verwendet, um analytische Datenmodelle aus den Daten im Modell Dimensionsdaten zu erstellen. SQL Server Reporting Services wird verwendet, um strategische Berichte direkt aus dem Modell Dimensionsdaten und auch aus dem analytischen Modell zu generieren. Powerbi wird verwendet, um Dashboards aus den Daten zu erstellen. Die Dashboards werden in Websites und auf Smartphones und Tablets verwendet. *Hinweis: Diese Datenmodelle und Berichte sind noch nicht verfügbar*

## <a name="additional-workflows"></a>Zusätzliche workflows

Hierbei handelt es sich um zusätzliche Workflows.
- "Wwi" Probleme-Gutschriften bei einem Kunden erhalten Sie keine der gut aus irgendeinem Grund oder die Waren fehlerhaft sind. Diese werden als negative Rechnungen behandelt.
- "Wwi" wird in regelmäßigen Abständen die verfügbaren Mengen der vordefinierten Elemente aus, um sicherzustellen, dass die vordefinierten Mengen als verfügbar angezeigt, auf ihrem System genau sind. (Der Prozess hierfür wird ein Stocktake bezeichnet).
- Kalte Zimmertemperatur. Perishable waren, werden in refrigeratedtransportation Räume gespeichert. Sensordaten in diese Räume werden in der Datenbank für die Überwachung und Analyse erfasst.
- Nachverfolgen von Fahrzeug-Speicherort. Fahrzeuge, die transport von Gütern für "wwi" enthalten, Sensoren, die den Speicherort nachzuverfolgen. Dieser Speicherort wird erneut in die Datenbank für die Überwachung und weitere Analyse erfasst.

## <a name="fiscal-year"></a>Geschäftsjahr

Das Unternehmen arbeitet mit einem Geschäftsjahr, die ab 1. November beginnt.

## <a name="terms-of-use"></a>Nutzungsbedingungen

Die Lizenz für die Beispieldatenbank und der Beispielcode wird hier beschrieben: [Dateien "License.txt"](https://github.com/Microsoft/sql-server-samples/blob/master/license.txt)

Die-Beispieldatenbank enthält öffentliche Daten, die aus der kriminalstatistik und natürliche EarthData geladen wurde. Die Nutzungsbedingungen sind hier: [https://www.naturalearthdata.com/about/terms-of-use/](https://www.naturalearthdata.com/about/terms-of-use/)
