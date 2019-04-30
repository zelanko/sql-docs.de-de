---
title: Sperrverhalten - Parallel Data Warehouse | Microsoft-Dokumentation
description: Erfahren Sie, wie die Parallel Data Warehouse verwendet sperren, um die Integrität von Transaktionen sicherzustellen und die Konsistenz der Datenbanken beizubehalten, wenn mehrere Benutzer gleichzeitig auf Daten zugreifen.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 3f9862fed432036dcb4a3905fb3af1d3132349a5
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63280892"
---
# <a name="locking-behavior-in-parallel-data-warehouse"></a>Sperrverhalten in Parallel Data Warehouse
Erfahren Sie, wie die Parallel Data Warehouse verwendet sperren, um die Integrität von Transaktionen sicherzustellen und die Konsistenz der Datenbanken beizubehalten, wenn mehrere Benutzer gleichzeitig auf Daten zugreifen.  
  
## <a name="Basics"></a>Grundlagen der Sperren  
**Modi**  
  
SQL Server PDW unterstützt vier Sperren Modi:  
  
Exclusive  
Die exklusive Sperre verhindert, dass das Schreiben in oder Lesen des gesperrten Objekts, bis die Transaktion, die gedrückt halten, dass die exklusive Sperre abgeschlossen ist. Keine anderen Sperren von einem anderen Modus sind zulässig, während die exklusive Sperre aktiviert ist. Beispielsweise verwenden Sie DROP TABLE oder CREATE DATABASE eine exklusive Sperre.  
  
Shared  
Die gemeinsame Sperre verhindert die Initiierung von eine exklusive Sperre für das betroffene Objekt, aber Sie können von allen anderen Sperrmodi. Z. B. die SELECT-Anweisung eine gemeinsame Sperre, initiiert und aus diesem Grund kann mehrere Abfragen gleichzeitig auf die ausgewählten Daten allerdings wird verhindert, dass Updates auf die Datensätze gelesen wird, bis die SELECT-Anweisung abgeschlossen ist.  
  
ExclusiveUpdate  
Die ExclusiveUpdate-Sperre verhindert, dass das Schreiben in den gesperrten Objekts, lässt jedoch lesen, die über die freigegebene Sperre. Keine anderen Sperren sind zulässig, während die ExclusiveUpdate-Sperre aktiviert ist. Beispielsweise verwenden die Datenbank sichern und Wiederherstellen eines Datenbank eine exklusive updatesperre.  
  
SharedUpdate  
SharedUpdate-Sperre verhindert, dass exklusiver und ExclusiveUpdate Sperrmodi und kann freigegeben "und" SharedUpdate-Sperre-Modi für das Objekt. SharedUpdate ändert ein Objekt, jedoch nicht den Lesezugriff, während die Änderung. Beispielsweise INSERT und UPDATE verwendet eine SharedUpdate-Sperre.  
  
**Ressourcenklassen**  
  
Sperren werden auf die folgenden Objektklassen: Datenbank, SCHEMA, OBJEKTS (Tabelle, Sicht oder Prozedur), Anwendung (wird intern verwendet), EXTERNALDATASOURCE, EXTERNALFILEFORMAT und SCHEMARESOLUTION (eine Ebene Datenbanksperre beim Erstellen, ändern oder Löschen von Schemaobjekten oder Datenbankbenutzer). Diesen Objektklassen können angezeigt werden, in der Spalte Object_type [Sys. dm_pdw_waits](../relational-databases/system-dynamic-management-views/sys-dm-pdw-waits-transact-sql.md).  
  
## <a name="Remarks"></a>Allgemeine Hinweise  
Sperren können für Datenbanken, Tabellen oder Sichten angewendet werden.  
  
Alle konfigurierbaren Isolationsstufen werden von SQL Server PDW nicht implementiert. Wie in ANSI-standard definiert unterstützt die READ_UNCOMMITTED-Isolationsstufe. Allerdings seit lesen, die Vorgänge unter READ_UNCOMMITTED ausgeführt werden, nur sehr wenige blockierende Vorgänge tatsächlich auftreten oder zu Konflikten führen, in das System.  
  
SQL Server PDW ist abhängig von der zugrunde liegenden SQL Server-Engine, um Sperren und Parallelität Steuerelement zu implementieren. Wenn Operationen zu einer zugrunde liegenden SQL Server-Deadlock innerhalb desselben Knotens führen, wird SQL Server PDW nutzt die SQL Server-Deadlock-Erkennung-Funktion und eine der blockierenden Anweisungen beendet.  
  
> [!NOTE]  
> SQL Server lässt sich nicht auf Anweisungen aus, die für die durch neuere sperranforderungen blockiert werden mit Sperren warten. SQL Server PDW ist dieser Prozess nicht vollständig implementiert. In SQL Server-PDW können fortlaufende-Anforderungen für die neue freigegebene Sperren manchmal eine Anforderung vorherige (aber wartende), eine exklusive Sperre blockiert. Z. B. eine **UPDATE** Anweisung (und erfordert eine exklusive Sperre) kann durch freigegebene sperren, die für die Reihe von erteilt werden blockiert werden **wählen** Anweisungen. Einen blockierten Prozess auflösen (identifiziert durch Überprüfen der [Sys. dm_pdw_waits](../relational-databases/system-dynamic-management-views/sys-dm-pdw-waits-transact-sql.md) DVM), den neue Anforderungen senden, bis die exklusive Sperre erfüllt wurde.  
  
## <a name="lock-definition-table"></a>Lock-Definition (Tabelle)  
SQL Server unterstützt die folgenden Typen von Sperren. Nicht alle Typen von Sperren auf dem steuerknoten verfügbar sind, aber Sie können die auf den Computeknoten auftreten werden.  
  
-   Sch-S (Schemastabilität). Stellt sicher, dass ein Schemaelement, wie z. B. eine Tabelle oder ein Index, nicht gelöscht wird, während eine Sitzung eine Schemastabilitätssperre für das Schemaelement aufrechterhält.  
  
-   SCH-M (Schema Modification, schemaänderung). Muss von jeder Sitzung aufrechterhalten werden, die das Schema der angegebenen Ressource ändern möchte. Stellt sicher, dass keine anderen Sitzungen auf das angegebene Objekt verweisen.  
  
-   S (Shared). Der haltenden Sitzung wird der gemeinsame Zugriff auf die Ressource erteilt.  
  
-   U (Update). Zeigt eine Updatesperre an, die für Ressourcen ausgegeben wurde, die möglicherweise aktualisiert werden. Sie wird dazu verwendet, eine häufige Form von Deadlock zu verhindern, die auftritt, wenn mehrere Sitzungen Ressourcen sperren, um diese möglicherweise zu einem späteren Zeitpunkt zu aktualisieren.  
  
-   X (Exclusive, exklusiv). Der haltenden Sitzung wird exklusiver Zugriff auf die Ressource erteilt.  
  
-   (Ist Intent Shared). Gibt die Absicht an, S-Sperren für eine untergeordnete Ressource in der Sperrhierarchie zu platzieren.  
  
-   IU (Intent Update). Gibt die Absicht an, U-Sperren für eine untergeordnete Ressource in der Sperrhierarchie zu platzieren.  
  
-   IX (Intent Exclusive). Gibt die Absicht an, X-Sperren für eine untergeordnete Ressource in der Sperrhierarchie zu platzieren.  
  
-   SIU (Shared Intent Update). Zeigt den gemeinsamen Zugriff auf eine Ressource mit der Absicht an, Updatesperren für untergeordnete Ressourcen in der Sperrhierarchie zu erhalten.  
  
-   SECHS (Shared Intent Exclusive). Zeigt den gemeinsamen Zugriff auf eine Ressource mit der Absicht an, exklusive Sperren für untergeordnete Ressourcen in der Sperrhierarchie zu erhalten.  
  
-   UIX (Update Intent-exklusiv). Zeigt eine aufrechterhaltene Updatesperre für eine Ressource mit der Absicht an, exklusive Sperren für untergeordnete Ressourcen in der Sperrhierarchie zu erhalten.  
  
-   BU. Wird von Massenvorgängen verwendet.  
  
-   RangeS_S (freigegebener Schlüsselbereich und freigegebene Ressourcensperre). Zeigt serialisierbaren Bereichsscan an.  
  
-   RangeS_U (freigegebener Schlüsselbereich und Updatesperre für Ressource sperren). Zeigt serialisierbaren Updatescan an.  
  
-   RangeI_N (Schlüsselbereich einfügen und keine Ressourcensperre). Wird zum Testen von Bereichen verwendet, bevor ein neuer Schlüssel in einen Index eingefügt wird.  
  
-   RangeI_S. Konvertierungssperre für Schlüsselbereich, die durch eine Überschneidung von RangeI_N- und S-Sperren erzeugt wurde.  
  
-   RangeI_U. Konvertierungssperre für Schlüsselbereich, die durch eine Überschneidung von RangeI_N- und U-Sperren erzeugt wurde.  
  
-   RangeI_X. Konvertierungssperre für Schlüsselbereich, die durch eine Überschneidung von RangeI_N- und X-Sperren erzeugt wurde.  
  
-   RangeX_S. Konvertierungssperre für Schlüsselbereich, die durch eine Überschneidung von RangeI_N- und RangeS_S.-Sperren erzeugt wurde.  
  
-   RangeX_U. Konvertierungssperre für Schlüsselbereich, die durch eine Überschneidung von RangeI_N- und RangeS_U-Sperren erzeugt wurde.  
  
-   RangeX_X (exklusiver Schlüsselbereich und exklusive Ressourcensperre). Dies ist eine Konvertierungssperre, die für das Update eines Schlüssels in einem Bereich verwendet wird.  
  
## <a name="see-also"></a>Siehe auch  
<!-- MISSING LINKS 
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  
-->
[sys.dm_pdw_waits](../relational-databases/system-dynamic-management-views/sys-dm-pdw-waits-transact-sql.md)  
  
