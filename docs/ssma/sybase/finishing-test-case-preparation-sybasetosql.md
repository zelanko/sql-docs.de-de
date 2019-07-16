---
title: Abschluss der Vorbereitung für Testfälle (SybaseToSQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Tester Component,Test Case Settings
ms.assetid: 8b2a49b0-4296-4f3f-9e56-323aa6a6fa8e
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: c3085d17804866015a78e93556dd5373d3a1b8cd
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68029142"
---
# <a name="finishing-test-case-preparation-sybasetosql"></a>Beenden der Vorbereitung für Testfälle (SybaseToSQL)
Letzte Seite des Assistenten zeigt die testsituationsbeschreibung und Informationen zu Objekten, die am Test Beteiligter. Darüber hinaus können auf dieser Seite Sie den Test Ausführungsoptionen festlegen.  
  
Die **Testfall Informationen** Abschnitt wird gezeigt, Testfall-Name und Beschreibung.  
  
Die **Testobjekte** Abschnitt enthält eine benannte Liste getesteter Objekte, gruppiert nach Objekttyp.  
  
Die **betroffene Objekte zu analysierenden** Abschnitt zeigt die benannte Liste der Objekte, welche datenänderungen nach der Ausführung des getesteten Objekte verglichen werden soll.  
  
## <a name="test-case-settings"></a>Testfall-Einstellungen  
In der **Testfall Einstellungen** Abschnitt können Sie die Ausführung der folgenden Testoptionen festlegen:  
  
### <a name="stop-test-execution-after-first-failure"></a>Ausführung von Tests nach dem ersten Fehler beenden  
Gibt an, um den Test zu unterbrechen, wenn ein Fehler, während der testausführung auftritt.  
  
-   Auf Wunsch **Ja**, testen Sie die Ausführung wird ein, wenn ein Fehler auftritt.  
  
-   Auf Wunsch **keine**, testausführung wird nach einem Fehler fortgesetzt.  
  
### <a name="perform-data-rollback"></a>Ausführen von Rollbacks für Daten  
Aktivieren Sie automatische Rollback, nach der Ausführung des Tests.  
  
-   Auf Wunsch **Ja**, datenänderungen nach der Ausführung des Tests, verloren.  
  
-   Auf Wunsch **keine**, alle testausführung datenänderungen werden gespeichert.  
  
### <a name="auxiliary-tables-saving-mode"></a>Erweiterungstabellen Modus speichern  
Definiert den speichern für Hilfstabellen erstellt während der testausführung. Siehe die Beschreibung der Erweiterungstabellen in der [Ausführen von Testfällen &#40;SybaseToSQL&#41; ](../../ssma/sybase/running-test-cases-sybasetosql.md) Thema.  
  
-   Bei Auswahl von **immer speichern**, Erweiterungstabellen Daten immer zur späteren Verwendung gespeichert werden.  
  
-   Bei Auswahl von **speichern, wenn die Tabelle Vergleich fehlgeschlagen**, nur dann, wenn ein Fehler tritt auf, Erweiterungstabellen Daten gespeichert werden.  
  
-   Bei Auswahl von **immer löschen**, Erweiterungstabellen immer gelöscht werden, nach der Ausführung des Tests.  
  
-   Bei Auswahl von **Benutzer bitten, wenn Tabelle Vergleich fehlgeschlagen ist**, der Benutzer kann die erforderlichen Aktionen auswählen, wenn ein Fehler auftritt.  
  
Klicken Sie auf die **Fertig stellen** Schaltfläche zum Speichern des vorbereiteten Testfalls in [mithilfe von Test Repositories &#40;SybaseToSQL&#41;](../../ssma/sybase/using-test-repositories-sybasetosql.md).  
  
## <a name="see-also"></a>Siehe auch  
[Using Test Repositories &#40;SybaseToSQL&#41;](../../ssma/sybase/using-test-repositories-sybasetosql.md)  
[Ausführen von Testfällen &#40;SybaseToSQL&#41;](../../ssma/sybase/running-test-cases-sybasetosql.md)  
[Testen von migrierten Datenbankobjekten &#40;SybaseToSQL&#41;](../../ssma/sybase/testing-migrated-database-objects-sybasetosql.md)  
  
