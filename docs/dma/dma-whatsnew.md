---
title: Neues in den Data Migration Assistant (SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/28/2018
ms.prod: sql
ms.prod_service: dma
ms.reviewer: ''
ms.suite: sql
ms.technology: dma
ms.tgt_pltfrm: ''
ms.topic: conceptual
keywords: ''
helpviewer_keywords:
- Data Migration Assistant, new features
ms.assetid: ''
caps.latest.revision: ''
author: HJToland3
ms.author: rajpo
manager: craigg
ms.openlocfilehash: 188c19f173e8c53995d84a74ecc04d1cac9eae92
ms.sourcegitcommit: e4e9f02b5c14f3bb66e19dec98f38c012275b92c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/28/2018
ms.locfileid: "43118328"
---
# <a name="whats-new-in-data-migration-assistant"></a>Neuerungen im Datenmigrations-Assistenten
Dieser Artikel beschreibt die Ergänzungen in jeder Version von Data Migration Assistant (DMA).

## <a name="dma-v40"></a>DMA v4. 0
Die v4. 0-Version von DMA wird eingeführt, die Azure SQL-Datenbank-SKU-Empfehlungen-Funktion, die Benutzern ermöglicht, identifizieren Sie die empfohlenen Azure SQL-Datenbank-SKU basierend auf Leistungsindikatoren erfasst, die von den Computern, auf dem Ihre Datenbanken gehostet werden. Dieses Feature bietet Empfehlungen in Bezug auf Preise, Ebenen, computeebene, maximale Datengröße, sowie und geschätzte Kosten pro Monat. Darüber hinaus die Möglichkeit, alle Datenbanken in Azure in einer Massenoperation bereitzustellen.

> [!NOTE]
> Diese Funktion ist derzeit nur über die Befehlszeilenschnittstelle (CLI) verfügbar sein. Unterstützung für dieses Feature über die DMA-Benutzeroberfläche ist für die Übermittlung später in diesem Jahr geplant.

Weitere Informationen finden Sie im Artikel [identifizieren Sie die richtige Azure SQL-Datenbank-SKU für Ihre lokale Datenbank](dma-sku-recommend-sql-db.md).

## <a name="dma-v36"></a>DMA-Version 3.6
Die Version 3.6 der DMA führt "Automatisch korrigieren" für die Schemaobjekte, die von der am häufigsten verwendeten migrationsblocker betroffen sind.

Diese Version bietet automatische-Fix für die folgenden migrationsblockierung und Probleme Verhalten zu ändern:
- Die Schemaobjekte, die nicht qualifizierte Join-Syntax verwenden.
- Die Schemaobjekte, die die ältere RAISEERROR-Anweisung verwenden.
- SQL-Anweisungen, die vom ganzzahligen Literal Reihenfolge verwenden.

DMA führt automatische Schema-Konvertierung für die Objekte, die durch die aufgeführten Probleme beeinträchtigt, und fordert den Benutzer zur Bestätigung vor dem Fortfahren mit der schemakonvertierung. Benutzer können alle Konvertierungen, die für ein beliebiges Datenbankobjekt des angegebenen überprüfen Sie die Änderungen der vorgeschlagene Code, und klicken Sie dann entweder annehmen oder ablehnen.

DMA verwendet Microsoft Programm Sprachsynthese (Text)-Technologie wird empfohlen, dass der Code repariert. Erfahren Sie mehr über [PROSE](https://microsoft.github.io/prose/).

## <a name="dma-v35"></a>DMA v3. 5
Die v3. 5-Version von DMA umfasst die folgenden Ergänzungen:
- Beträchtliche Leistungssteigerungen für die Migration zu Azure SQL-Datenbank (Benchmark-Tests anzugeben, dass der Vorgang viermal schneller als mit früheren Versionen der DMA ist).
- Der Speicherbedarf wird weiter optimiert, um die Stabilität des Workflow bei der Migration zu verbessern.
- Die Fähigkeit, Bewertungen bei den Migrationen Schema und Daten zu überspringen, (Wenn Sie bereits die Bewertung ausgeführt und behandelt wichtige Schemaobjekte vor der Migration haben).
- Eine Lösung zur Beseitigung eines Problems mit dem Tool stürzt ab, wenn eine ungültige Netzwerk-Freigabepfad für Sicherungsdateien, bereitgestellt wird, beim Durchführen eines Upgrades von einer älteren Version von SQL Server auf eine höhere Version oder SQL Server auf Azure Virtual Machines lokalen.

## <a name="dma-v34"></a>DMA-Version 3.4
Die Version 3.4-Version von DMA umfasst die folgenden Ergänzungen:
- Unterstützung für SQL Server 2017 als Quelle für Migrationen zu Azure SQL-Datenbank.
- Verbesserungen an Stabilität, Leistung und Bewertung der Regel auf Richtigkeit.

## <a name="dma-v33"></a>DMA-Version 3.3
Die Version 3.3-Version von DMA ermöglicht die Migration einer lokalen SQL Server-Instanz, auf die neue Version von SQL Server 2017 unter Windows und Linux. Während der gesamten Migrationsworkflow für Windows und Linux identisch ist, sind die Umstellung auf SQL Server 2017 für Linux einige zusätzliche Überlegungen erforderlich.

### <a name="specifying-the-back-up-path"></a>Angeben des Pfads sichern
Verwenden anderen Pfad-Formate, Linux und Windows. Migrieren zu SQL Server 2017 unter Linux erfordert daher, dass der Benutzer sowohl die Windows und Linux-Versionen des Pfads zum Speicherort der physischen Datei angeben. Sie können beide Versionen des Pfads unterschiedlich, je nachdem, wo die physische Datei angeben.
Wenn Sie die physische Datei für die Sicherung auf einem Computer ausgeführt wird:
- Linux, verwenden Teilen eine "Samba", um die Datei mit anderen Computern im Netzwerk freigeben.
- Windows, verwenden Sie den Befehl "Mnt" zum Einbinden der Dateifreigabe auf dem Computer, auf dem Linux ausgeführt wird.

> [!NOTE]
> Details der Verwendung einer Freigabe 'Samba' oder den Befehl "Mnt" sprengen den Rahmen dieses Artikels aus.

### <a name="migrating-windows-logins"></a>Migrieren von Windows-Anmeldungen
Während die Migration von Active Directory (AD) Anmeldenamen offiziell von SQL Server 2017 unter Linux unterstützt wird, erfordert es eine zusätzliche Konfiguration erfolgreich ausgeführt. Finden Sie im Artikel [Active Directory-Authentifizierung mit SQL Server unter Linux](https://docs.microsoft.com/sql/linux/sql-server-linux-active-directory-authentication) ausführliche Informationen über das Einrichten von Active Directory-Anmeldungen in SQL Server 2017 unter Linux. Nach dem Ausführen der erforderlichen Konfigurations an, das Setup abgeschlossen ist, und können Sie die Active Directory-Anmeldung wie gewohnt migrieren. Standard-SQL-Authentifizierung funktioniert wie erwartet, ohne eine zusätzliche einzurichten.

## <a name="dma-v32"></a>DMA v3. 2
Die v3. 2-Version von DMA umfasst die folgenden Ergänzungen:

- Schema- und Datenmigration aktiviert aus einem lokalen SQL Server-Datenbanken in Azure SQL-Datenbank ein neuer Migrationsworkflow für die.
- Während der schemamigration zu Azure SQL-Datenbank DMA Skripts Datenbankobjekte für die Quelle enthält Anleitungen, potenzielle Kompatibilitätsprobleme zu beheben, und klicken Sie dann Ihr Schema in Azure bereitgestellt.

## <a name="dma-v31"></a>DMA v3. 1
Die v3. 1-Version von DMA umfasst die folgenden Ergänzungen:

- Verbesserte Assessment-Empfehlungen für Azure SQL-Datenbanken in Bezug auf die datenbanksortierungen verwenden, der nicht unterstützten gespeicherten Systemprozeduren und CLR-Objekte.
- Assessment-Leitfaden für Kompatibilitätsgrad 130, 120, 110 zu 100 bei der Migration zu Azure SQL-Datenbanken.

## <a name="dma-v30"></a>DMA v3. 0
Die v3. 0-Version von DMA erweitert die Azure SQL-datenbankbewertung durch, um umfassende Empfehlungen zum Beheben von Problemen im Zusammenhang mit:

- Migration von Blockierungsproblemen.
- Teilweise oder nicht unterstützte Features und Funktionen.

## <a name="dma-v21"></a>DMA v2. 1
Die v2. 1-Version von DMA umfasst die folgenden Ergänzungen:
- Befehlszeilenunterstützung für das Ausführen von Bewertungen in einem unbeaufsichtigten Modus aus, die Ihnen hilft, Bewertungen ausgeführt und skaliert. Weitere Informationen finden Sie im Artikel [ausführen Data Migration Assistant über die Befehlszeile](dma-commandline.md).
- Leistungsverbesserungen beim Starten von Benutzern und DMA schließen.
- Die Fähigkeit zum Konfigurieren von SQL-Verbindungstimeout. Weitere Informationen finden Sie im Artikel [Konfigurationseinstellungen für den Data Migration Assistant](dma-configurationsettings.md).

## <a name="dma-v20"></a>DMA v2. 0
Die v2. 0-Version von DMA enthält verbesserte Stretch-Datenbank featureempfehlungen ordnungsgemäße priorisierte Tabellen angeben, die die Storage-einsparungen zu maximieren.

## <a name="dma-v10"></a>DMA-v1. 0
Die v1. 0-Version von DMA ist die erste Version, und bietet für:
- Ermittlung von Problemen, die ein Upgrade auf eine lokale Version von SQL Server auswirken können. Alle Ergebnisse werden als Kompatibilitätsprobleme beschrieben, und sie können die folgenden Bereiche unterteilt:
    - Wichtige Änderungen
    - Verhaltensänderungen
    - Veraltete Features
- Ermittlung von neuen Funktionen in der SQL Server-Zielplattform, die ein Upgrade die Datenbank profitieren kann. Alle Ergebnisse werden als Vorschläge zu Features beschrieben, und sie können die folgenden Bereiche unterteilt:
    - Leistung
    - Security
    - Speicherung
-   Moderne Benutzeroberfläche zum Ausführen von Bewertungen.

## <a name="see-also"></a>Siehe auch
[Übersicht über Data Migration Assistant](../dma/dma-overview.md)
