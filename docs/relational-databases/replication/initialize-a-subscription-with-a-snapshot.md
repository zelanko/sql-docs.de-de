---
title: Initialisieren eines Abonnements mit einer Momentaufnahme
ms.custom: ''
ms.date: 03/23/2020
ms.prod: sql
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- snapshots [SQL Server replication], initializing subscriptions
- initializing subscriptions [SQL Server replication], snapshots
ms.assetid: 77a9ade2-cdc0-4ae9-a02d-6e29d7c2ada0
author: MashaMSFT
ms.author: mathoma
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: cb69f5c2033a515676587ddbef0cb3d14e3bc3d6
ms.sourcegitcommit: df1f0f2dfb9452f16471e740273cd1478ff3100c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/29/2020
ms.locfileid: "87396132"
---
# <a name="initialize-a-subscription-with-a-snapshot-for-a-new-publication"></a>Initialisieren eines Abonnements mit einer Momentaufnahme für eine neue Veröffentlichung

[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

In diesem Artikel werden die Prozesse beschrieben, die bei der Initialisierung der Veröffentlichung eines Replikats ablaufen. Auf die Abonnenten wird eine Anfangsmomentaufnahme angewendet.

## <a name="snapshot-for-a-new-publication"></a>Momentaufnahme für eine neue Veröffentlichung

Nach dem Erstellen einer Veröffentlichung wird automatisch eine Momentaufnahme erfasst.
Die Momentaufnahme wird in den Momentaufnahmeordner kopiert. Dieses Standardverhalten tritt bei Mergeveröffentlichungen auf, die mit dem Assistenten für neue Veröffentlichungen erstellt wurden.

### <a name="snapshot-is-applied-to-subscriber"></a>Anwenden der Momentaufnahme auf den Abonnenten

Die neue Momentaufnahme wird von einem Agent auf die Abonnenten angewendet. Der Vorgang erfolgt während der Erstsynchronisierung des Abonnements. Welcher Agent den Vorgang ausführt, hängt vom Typ der Veröffentlichung ab:

- Für _Transaktions-_ und _Momentaufnahmeveröffentlichungen_:
  - Der Verteilungs-Agent.

- Für _Mergeveröffentlichungen_:
  - Der Merge-Agent.

### <a name="type-of-publication"></a>Typ der Veröffentlichung

In der folgenden Tabelle wird der Inhalt der Momentaufnahme nach Veröffentlichungstyp aufgeschlüsselt.

&nbsp;

| Veröffentlichungstyp der Momentaufnahme | Inhalt der Momentaufnahme |
| :---------------------------------------- | :----------------------- |
| <ul> <li>Momentaufnahmeveröffentlichung</li> <li>Transaktionsveröffentlichung</li> <li>Mergeveröffentlichung ohne parametrisierte Filter</li> </ul> | <ul> <li>Schema</li> <li>Daten, in Dateien für das Massenkopierprogramm</li> <li>Einschränkungen</li> <li>Erweiterte Eigenschaften</li> <li>Indizes</li> <li>Trigger</li> <li>Systemtabellen, die für die Replikation erforderlich sind</li> </ul> <br/>Weitere Informationen finden Sie unter [Erstellen und Anwenden der Anfangsmomentaufnahme](../../relational-databases/replication/create-and-apply-the-initial-snapshot.md). |
| <ul> <li>Mergeveröffentlichung mit parametrisierten Filtern</li> </ul> | <ul> <li>Schemamomentaufnahmen (Replikationsskripts, veröffentlichte Objekte, jedoch keine Daten)</li> <li>Daten, die zur Partition des Abonnements gehören</li> </ul> <br/>Weitere Informationen finden Sie unter [Erstellen einer Momentaufnahme für eine Mergeveröffentlichung mit parametrisierten Filtern](../../relational-databases/replication/create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md). |
| | |

#### <a name="two-part-process-with-merge-publication-that-uses-parameterized-filters"></a>Zweistufiger Vorgang mit einer Mergeveröffentlichung mit parameterisierten Filtern

Für eine Mergeveröffentlichung mit parametrisierten Filtern wird die Momentaufnahme mithilfe des folgenden, zweiteiligen Vorgangs erstellt:

1. Eine Schemamomentaufnahme wird erstellt, die folgende Elemente enthält:
   - Replikationsskripts
   - Schema der veröffentlichten Objekte
   - _(jedoch keine Daten)_

2. Anschließend wird jedes Abonnement mit einer Momentaufnahme initialisiert. Die Momentaufnahme enthält folgende Elemente:
   - Skripts und ein Schema, die aus der Schemamomentaufnahme kopiert wurden
   - Daten, die zur Partition des Abonnements gehören

## <a name="type-of-replication"></a>Typ der Replikation

Die in der Momentaufnahme enthaltenen Dateitypen hängen vom Replikationstyp und den Artikeln in der Veröffentlichung ab.

&nbsp;

| Replikationstyp | Gemeinsame Momentaufnahmedateien |
| :------------------ | :-------------------- |
| Momentaufnahmereplikation oder<br/>Transaktionsreplikation | &bullet; Schema (.sch) <br/>&bullet; Daten (.bcp) <br/>&bullet; Einschränkungen und Indizes (.dri) <br/>&bullet; komprimierte Momentaufnahmedateien (.cab) <br/>&bullet; Trigger (.tag), nur zum Aktualisieren eines Abonnenten <br/><br/>&bullet; Einschränkungen (.idx) |
| Mergereplikation                                      | &bullet; Schema (.sch) <br/>&bullet; Daten (.bcp) <br/>&bullet; Einschränkungen und Indizes (.dri) <br/>&bullet; komprimierte Momentaufnahmedateien (.cab) <br/>&bullet; Trigger (.trg) <br/><br/>&bullet; Systemtabellendaten (.sys) <br/>&bullet; Konflikttabellen (.cft) |
| | |

### <a name="snapshot-folder"></a>Momentaufnahmeordner

Bei der Übertragung der Dateien werden diese in den standardmäßigen _Momentaufnahmeordner_ oder in einen _alternativen Ordner_ für Momentaufnahmen kopiert.

Der Momentaufnahmeordner wird beim Konfigurieren des Verteilers angegeben. Der alternative Ordner wird beim Erstellen der Veröffentlichung angegeben.

### <a name="resume-transfer-after-interruption"></a>Fortsetzen der Übertragung nach einer Unterbrechung

Die Dateiübertragung an einen Momentaufnahmeordner wird automatisch fortgesetzt, wenn diese aufgrund einer instabilen Verbindung unterbrochen wird.

Aus Effizienzgründen werden beim Fortsetzen keine Dateien noch einmal gesendet, die vor der Unterbrechung bereits gesendet wurden.

## <a name="snapshot-options"></a>Momentaufnahmeoptionen

Zum Initialisieren eines Abonnements mit einer Momentaufnahme stehen verschiedene Optionen zur Verfügung. Ihre Möglichkeiten:

- Geben Sie anstelle des oder zusätzlich zum Speicherort des Standardmomentaufnahmeordners einen alternativen Speicherort für den Momentaufnahmeordner an. Weitere Informationen finden Sie unter [Ändern von Momentaufnahmeoptionen](../../relational-databases/replication/snapshot-options.md).

- Komprimieren Sie Momentaufnahmen zum Speichern auf Wechselmedien oder zum Übertragen in einem langsamen Netzwerk. Weitere Informationen finden Sie unter [Compressed Snapshots](../../relational-databases/replication/snapshot-options.md#compressed-snapshots).

- Führen Sie vor oder nach dem Anwenden der Momentaufnahme Transact-SQL-Skripts aus. Weitere Informationen finden Sie unter [Ausführen von Skripts vor und nach dem Anwenden der Momentaufnahme](../../relational-databases/replication/snapshot-options.md#execute-scripts-before-and-after-snapshot-is-applied).

- Übertragen Sie Momentaufnahmedateien über FTP (File Transfer Protocol). Weitere Informationen finden Sie unter [Übertragen von Momentaufnahmen über FTP](../../relational-databases/replication/publish/deliver-a-snapshot-through-ftp.md).

## <a name="see-also"></a>Weitere Informationen

[Initialisieren eines Abonnements](../../relational-databases/replication/initialize-a-subscription.md)

[Sichern des Momentaufnahmeordners](../../relational-databases/replication/security/secure-the-snapshot-folder.md)
