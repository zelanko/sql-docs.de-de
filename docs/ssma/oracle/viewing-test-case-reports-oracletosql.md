---
title: Anzeigen von Test Fall berichten (oracleto SQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 8da14323-9dd6-4019-bf79-3e8b972a9bc0
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: 38097cda1a014c173f96657f5758a95b9d266f6a
ms.sourcegitcommit: e8f6c51d4702c0046aec1394109bc0503ca182f0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/07/2020
ms.locfileid: "87932531"
---
# <a name="viewing-test-case-reports-oracletosql"></a>Anzeigen von Testfallberichten (OracleToSQL)
Der Bericht "Test Fall" zeigt die Test Überprüfungs Ergebnisse und allgemeine Test Informationen an. Bei einem Test Fehler werden auch Informationen zu nicht übereinstimmenden Daten in verifizierten Objekten angezeigt.  
  
## <a name="report-structure"></a>Berichtsstruktur  
Im oberen Bereich des Berichts werden diese Statistiken angezeigt:  
  
-   Die Gesamtanzahl der getesteten Objekte und die Anzahl von Objekten, für die der Test erfolgreich war.  
  
-   Die Gesamtanzahl der überprüften Tabellen und Fremdschlüssel und die Anzahl der erfolgreich abgeglichen Tabellen und Fremdschlüssel.  
  
-   Die Startzeit, die Endzeit des Testfalls und die Gesamtzeit für die Ausführung.  
  
Im restlichen Bericht werden Informationen in vier Kategorien angezeigt:  
  
**Voraussetzungs Fehler**  
Zeigt alle Fehler an, die im **Schritt "Voraussetzungen** " aufgetreten sind. Normalerweise wird Sie übersprungen.  
  
**Initialisierung**  
Zeigt den Status der Ausführung als **Erfolg** oder **Fehler**an.  
  
**Test Objekte Ergebnis**  
Ein Vergleich der Ergebnisse (Erfolg oder Fehler) und der Konflikte, die der SSMA-Tester bei einem Fehler erkannt hat.  
  
**Abschluss**  
Zeigt den Status der Ausführung als **Erfolg** oder **Fehler**an.  
  
## <a name="see-also"></a>Weitere Informationen  
[Ausführen von Test Fällen &#40;oracleto SQL&#41;](../../ssma/oracle/running-test-cases-oracletosql.md)  
[Testen von migrierten Datenbankobjekten &#40;oracleto SQL&#41;](../../ssma/oracle/testing-migrated-database-objects-oracletosql.md)  
  
