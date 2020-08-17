---
description: Anzeigen von Testfallberichten (SybaseToSQL)
title: Anzeigen von Test Fall berichten (sybaseto SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Tester Component,Test Case Reports
ms.assetid: cb75d281-43ef-4f4a-b754-2c4ee3b62ae7
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: ef72ea67b28aae674a1ae4b51dc52d9875e3b0e0
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88319876"
---
# <a name="viewing-test-case-reports-sybasetosql"></a>Anzeigen von Testfallberichten (SybaseToSQL)
Der Bericht "Test Fall" zeigt die Test Überprüfungs Ergebnisse und allgemeine Test Informationen an. Bei einem Test Fehler werden auch Informationen zu nicht übereinstimmenden Daten in verifizierten Objekten angezeigt.  
  
## <a name="report-structure"></a>Berichtsstruktur  
Im oberen Bereich des Berichts werden diese Statistiken angezeigt:  
  
-   Die Gesamtanzahl der getesteten Objekte und die Anzahl von Objekten, für die der Test erfolgreich war.  
  
-   Die Gesamtanzahl der überprüften Tabellen und Fremdschlüssel und die Anzahl der erfolgreich abgeglichen Tabellen und Fremdschlüssel.  
  
-   Die Startzeit, die Endzeit des Testfalls und die Gesamtzeit für die Ausführung.  
  
Im restlichen Bericht werden Informationen in vier Kategorien angezeigt:  
  
**Voraussetzungs Fehler**  
Zeigt alle Fehler an, die im Schritt " **Voraussetzungen** " aufgetreten sind. Normalerweise wird Sie übersprungen.  
  
**Initialisierung**  
Zeigt den Status der Ausführung als **Erfolg** oder **Fehler**an.  
  
**Test Objekte Ergebnis**  
Ein Vergleich der Ergebnisse (Erfolg oder Fehler) und der Konflikte, die der SSMA-Tester bei einem Fehler erkannt hat.  
  
**Abschluss**  
Zeigt den Status der Ausführung als **Erfolg** oder **Fehler**an.  
  
## <a name="see-also"></a>Weitere Informationen  
[Ausführen von Test Fällen &#40;sybaseto SQL-&#41;](../../ssma/sybase/running-test-cases-sybasetosql.md)  
[Testen von migrierten Datenbankobjekten &#40;sybaseto SQL&#41;](../../ssma/sybase/testing-migrated-database-objects-sybasetosql.md)  
  
