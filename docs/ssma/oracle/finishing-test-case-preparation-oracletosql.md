---
title: Abschluss der Vorbereitung für Testfälle (OracleToSQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 32f38713-7ae4-48d3-980d-74cadc8545a0
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.openlocfilehash: 1bdbe8616f5f2c3252f813e6e2636966ff16ec16
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "51662279"
---
# <a name="finishing-test-case-preparation-oracletosql"></a>Beenden der Vorbereitung für Testfälle (OracleToSQL)
Letzte Seite des Assistenten zeigt die testsituationsbeschreibung und Informationen zu Objekten, die am Test Beteiligter. Darüber hinaus können auf dieser Seite Sie den Test Ausführungsoptionen festlegen.  
  
Die **Testfall Informationen** Abschnitt wird gezeigt, Testfall-Name und Beschreibung.  
  
Die **Objekte aktiviert zu werden getestet** Abschnitt enthält eine benannte Liste getesteter Objekte, gruppiert nach Objekttyp.  
  
Die **Objekte betroffen von Tests, dass analysiert** Abschnitt zeigt die benannte Liste der Objekte, welche datenänderungen nach der Ausführung des getesteten Objekte verglichen werden soll.  
  
## <a name="test-case-settings"></a>Testfall-Einstellungen  
In der **Testfall Einstellungen** Abschnitt können Sie die Ausführung der folgenden Testoptionen festlegen:  
  
### <a name="stop-test-execution-after-first-failure"></a>Ausführung von Tests nach dem ersten Fehler beenden  
Gibt an, um den Test zu unterbrechen, wenn ein Fehler, während der testausführung auftritt.  
  
-   Auf Wunsch **Ja**, testen Sie die Ausführung wird ein, wenn ein Fehler auftritt.  
  
-   Auf Wunsch **keine**, testausführung wird nach einem Fehler fortgesetzt.  
  
### <a name="perform-data-rollback"></a>Ausführen von Rollbacks für Daten  
Ermöglicht die automatische Rollback nach Ausführung des Tests.  
  
-   Auf Wunsch **Ja**, datenänderungen nach der Ausführung des Tests, verloren.  
  
-   Auf Wunsch **keine**, alle testausführung datenänderungen werden gespeichert.  
  
### <a name="auxiliary-tables-saving-mode"></a>Erweiterungstabellen Modus speichern  
Definiert den speichern für Hilfstabellen erstellt während der testausführung. Siehe die Beschreibung der Erweiterungstabellen in der [Ausführen von Testfällen &#40;OracleToSQL&#41; ](../../ssma/oracle/running-test-cases-oracletosql.md) Thema.  
  
-   Bei Auswahl von **immer speichern**, Erweiterungstabellen Daten immer zur späteren Verwendung gespeichert werden.  
  
-   Bei Auswahl von **speichern, wenn die Tabelle Vergleich fehlgeschlagen**, nur dann, wenn ein Fehler tritt auf, Erweiterungstabellen Daten gespeichert werden.  
  
-   Bei Auswahl von **immer löschen**, Erweiterungstabellen immer gelöscht werden, nach der Ausführung des Tests.  
  
-   Bei Auswahl von **Benutzer bitten, wenn Tabelle Vergleich fehlgeschlagen ist**, der Benutzer kann die erforderlichen Aktionen auswählen, wenn ein Fehler auftritt.  
  
Klicken Sie auf die **Fertig stellen** Schaltfläche zum Speichern des vorbereiteten Testfalls in [mithilfe von Test Repositories (OracleToSQL)](https://msdn.microsoft.com/f941cce4-d3e3-4aeb-a88a-4f101a97a9f4).  
  
## <a name="see-also"></a>Siehe auch  
[Using Test Repositories &#40;OracleToSQL&#41;](../../ssma/oracle/using-test-repositories-oracletosql.md)  
[Ausführen von Testfällen &#40;OracleToSQL&#41;](../../ssma/oracle/running-test-cases-oracletosql.md)  
[Testen von migrierten Datenbankobjekten &#40;OracleToSQL&#41;](../../ssma/oracle/testing-migrated-database-objects-oracletosql.md)  
  
