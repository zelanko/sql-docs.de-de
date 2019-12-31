---
title: Sperrverhalten
description: Erfahren Sie, wie parallele Data Warehouse Sperren verwendet, um die Integrität von Transaktionen sicherzustellen und die Konsistenz der Datenbanken beizubehalten, wenn mehrere Benutzer gleichzeitig auf Daten zugreifen.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: f3ecf5cf783b707b75c90dfa70d502e3c81d28c3
ms.sourcegitcommit: d587a141351e59782c31229bccaa0bff2e869580
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/22/2019
ms.locfileid: "74400998"
---
# <a name="locking-behavior-in-parallel-data-warehouse"></a>Sperr Verhalten parallel Data Warehouse
Erfahren Sie, wie parallele Data Warehouse Sperren verwendet, um die Integrität von Transaktionen sicherzustellen und die Konsistenz der Datenbanken beizubehalten, wenn mehrere Benutzer gleichzeitig auf Daten zugreifen.  
  
## <a name="Basics"></a>Grundlagen zu sperren  
**Spiel**  
  
SQL Server PDW unterstützt vier Sperr Modi:  
  
Exklusiv  
Die exklusive Sperre verhindert das Schreiben oder Lesen aus dem gesperrten Objekt, bis die Transaktion, die die exklusive Sperre aufrecht erhält, abgeschlossen ist. Wenn die exklusive Sperre wirksam ist, sind keine anderen Sperren eines Modus zulässig. Beispielsweise verwenden DROP TABLE und Create Database eine exklusive Sperre.  
  
Shared  
Die freigegebene Sperre verhindert die Initiierung einer exklusiven Sperre für das betroffene Objekt, lässt jedoch alle anderen Sperrmodi zu. Beispielsweise initiiert die SELECT-Anweisung eine gemeinsame Sperre und ermöglicht es mehreren Abfragen, gleichzeitig auf die ausgewählten Daten zuzugreifen. es wird jedoch verhindert, dass Aktualisierungen an den gelesenen Datensätzen ausgeführt werden, bis die SELECT-Anweisung abgeschlossen ist.  
  
Exclusiveupdate  
Die exclusiveupdate-Sperre verhindert das Schreiben in das gesperrte Objekt, ermöglicht aber das Lesen über die freigegebene Sperre. Es sind keine anderen Sperren zulässig, während die exclusiveupdate-Sperre wirksam ist. Beispielsweise verwenden Backup Database und RESTORE DATABASE eine exklusive Update Sperre.  
  
SharedUpdate  
Die sharedupdate-Sperre verhindert exklusive und exclusiveupdate-Sperr Modi und ermöglicht den freigegebenen und den Share Dupdate-Sperrmodus für das Objekt. Sharedupdate ändert ein Objekt, schränkt den Lesezugriff jedoch während der Änderung nicht ein. Beispielsweise verwenden INSERT und Update eine sharedupdate-Sperre.  
  
**Ressourcen Klassen**  
  
Sperren werden für die folgenden Objektklassen gespeichert: Datenbank, Schema, Objekt (eine Tabelle, Sicht oder Prozedur), Anwendung (intern verwendet), externaldatasource, externalfileformat und schemaresolution (eine Sperre auf Datenbankebene, die beim Erstellen, ändern oder Löschen von Schema Objekten oder Datenbankbenutzern). Diese Objektklassen können in der object_type-Spalte von [sys. dm_pdw_waits](../relational-databases/system-dynamic-management-views/sys-dm-pdw-waits-transact-sql.md)angezeigt werden.  
  
## <a name="Remarks"></a>Allgemeine Hinweise  
Sperren können auf Datenbanken, Tabellen oder Sichten angewendet werden.  
  
SQL Server PDW implementiert keine konfigurierbaren Isolations Stufen. Sie unterstützt die vom ANSI-Standard definierte read_uncommitted Isolationsstufe. Da Lesevorgänge jedoch unter read_uncommitted ausgeführt werden, treten nur wenige blockierende Vorgänge auf oder führen zu Konflikten im System.  
  
SQL Server PDW die die zugrunde liegende SQL Server-Engine zum Implementieren von Sperren und der Parallelitäts Steuerung unterstützt. Wenn Vorgänge zu einem zugrunde liegenden SQL Server Deadlock innerhalb desselben Knotens führen, nutzt SQL Server PDW die Funktion zur Erkennung von SQL Server Deadlocks und beendet eine der blockierenden Anweisungen.  
  
> [!NOTE]  
> SQL Server lässt keine Anweisungen zu, die darauf warten, dass Sperren durch neuere Sperr Anforderungen blockiert werden. SQL Server PDW hat diesen Prozess nicht vollständig implementiert. In SQL Server PDW können kontinuierliche Anforderungen für neue freigegebene Sperren manchmal eine vorherige (aber wartende) Anforderung für eine exklusive Sperre blockieren. Beispielsweise kann eine **Update** -Anweisung (die eine exklusive Sperre erfordert) durch freigegebene Sperren blockiert werden, die für eine Reihe von **Select** -Anweisungen erteilt werden. Um einen blockierten Prozess aufzulösen (identifiziert durch Überprüfen der [sys. dm_pdw_waits](../relational-databases/system-dynamic-management-views/sys-dm-pdw-waits-transact-sql.md) DVM), können Sie die Übermittlung neuer Anforderungen erst abbrechen, wenn die exklusive Sperre erfüllt ist.  
  
## <a name="lock-definition-table"></a>Definitions Tabelle sperren  
SQL Server unterstützt die folgenden Arten von Sperren. Nicht alle Sperr Typen sind auf dem Steuer Knoten verfügbar, können jedoch auf den Computeknoten auftreten.  
  
-   Sch-S (Schema Stabilität). Stellt sicher, dass ein Schemaelement, wie z. B. eine Tabelle oder ein Index, nicht gelöscht wird, während eine Sitzung eine Schemastabilitätssperre für das Schemaelement aufrechterhält.  
  
-   Sch-M (Schema Änderung). Muss von jeder Sitzung aufrechterhalten werden, die das Schema der angegebenen Ressource ändern möchte. Stellt sicher, dass keine anderen Sitzungen auf das angegebene Objekt verweisen.  
  
-   S (freigegeben). Der haltenden Sitzung wird der gemeinsame Zugriff auf die Ressource erteilt.  
  
-   U (aktualisieren). Zeigt eine Updatesperre an, die für Ressourcen ausgegeben wurde, die möglicherweise aktualisiert werden. Sie wird dazu verwendet, eine häufige Form von Deadlock zu verhindern, die auftritt, wenn mehrere Sitzungen Ressourcen sperren, um diese möglicherweise zu einem späteren Zeitpunkt zu aktualisieren.  
  
-   X (exklusiv). Der haltenden Sitzung wird exklusiver Zugriff auf die Ressource erteilt.  
  
-   Ist (beabsichtigt freigegeben). Gibt die Absicht an, S-Sperren für eine untergeordnete Ressource in der Sperrhierarchie zu platzieren.  
  
-   IU (Intent Update). Gibt die Absicht an, U-Sperren für eine untergeordnete Ressource in der Sperrhierarchie zu platzieren.  
  
-   IX (beabsichtigt exklusiv). Gibt die Absicht an, X-Sperren für eine untergeordnete Ressource in der Sperrhierarchie zu platzieren.  
  
-   SIU (Shared Intent Update). Zeigt den gemeinsamen Zugriff auf eine Ressource mit der Absicht an, Updatesperren für untergeordnete Ressourcen in der Sperrhierarchie zu erhalten.  
  
-   Sechs (gemeinsame Absicht exklusiv). Zeigt den gemeinsamen Zugriff auf eine Ressource mit der Absicht an, exklusive Sperren für untergeordnete Ressourcen in der Sperrhierarchie zu erhalten.  
  
-   Uix (Update Absicht exklusiv). Zeigt eine aufrechterhaltene Updatesperre für eine Ressource mit der Absicht an, exklusive Sperren für untergeordnete Ressourcen in der Sperrhierarchie zu erhalten.  
  
-   ECM. Wird von Massenvorgängen verwendet.  
  
-   RangeS_S (frei gegebener Schlüsselbereich und freigegebene Ressourcen Sperre). Zeigt serialisierbaren Bereichsscan an.  
  
-   RangeS_U (Shared Key-Range und Update Resource Lock). Zeigt serialisierbaren Updatescan an.  
  
-   RangeI_N (Einfügen von Schlüsselbereich und NULL-Ressourcen Sperre). Wird zum Testen von Bereichen verwendet, bevor ein neuer Schlüssel in einen Index eingefügt wird.  
  
-   RangeI_S. Konvertierungssperre für Schlüsselbereich, die durch eine Überschneidung von RangeI_N- und S-Sperren erzeugt wurde.  
  
-   RangeI_U. Konvertierungssperre für Schlüsselbereich, die durch eine Überschneidung von RangeI_N- und U-Sperren erzeugt wurde.  
  
-   RangeI_X. Konvertierungssperre für Schlüsselbereich, die durch eine Überschneidung von RangeI_N- und X-Sperren erzeugt wurde.  
  
-   RangeX_S. Konvertierungssperre für Schlüsselbereich, die durch eine Überschneidung von RangeI_N- und RangeS_S.-Sperren erzeugt wurde.  
  
-   RangeX_U. Konvertierungssperre für Schlüsselbereich, die durch eine Überschneidung von RangeI_N- und RangeS_U-Sperren erzeugt wurde.  
  
-   RangeX_X (exklusive Schlüsselbereich und exklusive Ressourcen Sperre). Dies ist eine Konvertierungssperre, die für das Update eines Schlüssels in einem Bereich verwendet wird.  
  
## <a name="see-also"></a>Weitere Informationen  
<!-- MISSING LINKS 
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  
-->
[sys. dm_pdw_waits](../relational-databases/system-dynamic-management-views/sys-dm-pdw-waits-transact-sql.md)  
  
