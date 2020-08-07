---
title: Globale Einstellungen (Tester) (sybasedesql) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 6f0b9cea-5a24-4e42-8bbf-c4516b00da23
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: f1ebf6d1122db6b28b13c33320dabef520a40f5a
ms.sourcegitcommit: e8f6c51d4702c0046aec1394109bc0503ca182f0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/07/2020
ms.locfileid: "87931287"
---
# <a name="global-settings-tester-sybasetosql"></a>Globale Einstellungen (Tester) (SybaseToSQL)
Verwenden Sie die Seite Tester des Dialog Felds **globale Einstellungen** , um Einstellungen für SSMA-Tester anzugeben.  
  
Um **auf die Tester** -Einstellungen zuzugreifen, wählen Sie im Menü Extras die Option **globale Einstellungen**aus, und klicken Sie unten im linken Bereich auf **Tester** .  
  
## <a name="options"></a>Optionen  
**Test fähige Objektanalyse**  
Diese Einstellung gibt an, ob die Analyse der Test fähigen Objekte durchgeführt werden soll. Wählen Sie **Ja** aus, wenn der SSMA-Tester die abhängigen Objekte analysieren und automatisch überprüfen soll. Der Standard Options Satz ist " **Ja**".  
  
Die folgenden Optionen sind für diese Einstellung verfügbar:  
  
1.  Ja  
  
2.  Nein  
  
**Speicher Modus für Hilfstabellen**  
Diese Einstellung gibt an, wie die internen Hilfstabellen gespeichert werden, die während der Test Fall Ausführung erstellt wurden. Für diese Einstellung können folgende Optionen festgelegt werden:  
  
1.  Immer löschen  
  
2.  Immer speichern  
  
3.  Beim Vergleichen der Tabelle speichern  
  
4.  Beim Tabellenvergleich den Benutzer Fragen  
  
Der Standard Options Satz lautet: **immer löschen**.  
  
**Ausführen eines Daten Rollbacks**  
Mit dieser Einstellung wird festgelegt, ob nach dem Ausführen der einzelnen Testfälle ein Rollback-Vorgang ausgeführt werden soll. Der Standard Options Satz ist " **Nein**".  
  
Die folgenden Optionen sind für diese Einstellung verfügbar:  
  
1.  Ja  
  
2.  Nein  
  
**Testausführung nach dem ersten Fehler beendet**  
Mit dieser Einstellung wird festgelegt, ob der aktuell aktive Testfall beendet werden soll, wenn während der Ausführung ein Fehler aufgetreten ist. Der Standard Options Satz ist " **Ja**".  
  
Die folgenden Optionen sind für diese Einstellung verfügbar:  
  
1.  Ja  
  
2.  Nein  
  
## <a name="see-also"></a>Weitere Informationen  
[Fertigstellung der Test Fall Vorbereitung &#40;Sybase-SQL-&#41;](../../ssma/sybase/finishing-test-case-preparation-sybasetosql.md)  
  
