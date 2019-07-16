---
title: Anzeigen von Test Case Reports (SybaseToSQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Tester Component,Test Case Reports
ms.assetid: cb75d281-43ef-4f4a-b754-2c4ee3b62ae7
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 8a6d45f7e621f9b6516d4cc1211a8627174ae9b3
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67944606"
---
# <a name="viewing-test-case-reports-sybasetosql"></a>Anzeigen von Testfallberichten (SybaseToSQL)
Der Testfall-Bericht zeigt die Testergebnisse für die Überprüfung und allgemeine Testinformationen. Im Fall eines Testfehlers wird auch Informationen zur nicht übereinstimmenden Daten in überprüften Objekten angezeigt.  
  
## <a name="report-structure"></a>Berichtsstruktur  
Der Anfang des Berichts zeigt diese Statistiken:  
  
-   Die Gesamtanzahl der getesteten Objekte und die Anzahl der Objekte, die für die der Test erfolgreich war.  
  
-   Die Gesamtzahl der überprüften Tabellen und Fremdschlüssel, und die Anzahl von Tabellen und Fremdschlüssel, die erfolgreich abgeglichen.  
  
-   Die Startzeit, Endzeit des Testfalls und die Gesamtzeit für die Ausführung.  
  
Der Rest des Berichts werden die Informationen in vier Kategorien:  
  
**Erforderliche Komponenten Fehler**  
Zeigt aufgetretene Fehler an die **Voraussetzungen** Schritt. In der Regel wird übersprungen.  
  
**Initialisierung**  
Zeigt den Status der Ausführung als **Erfolg** oder **Fehler**.  
  
**Testergebnis-Objekte**  
Einen Vergleich der Ergebnisse (Erfolg oder Fehler) und der stimmen nicht überein, die SSMA-Tester bei einem Ausfall erkannt werden soll.  
  
**Beendigung**  
Zeigt den Status der Ausführung als **Erfolg** oder **Fehler**.  
  
## <a name="see-also"></a>Siehe auch  
[Ausführen von Testfällen &#40;SybaseToSQL&#41;](../../ssma/sybase/running-test-cases-sybasetosql.md)  
[Testen von migrierten Datenbankobjekten &#40;SybaseToSQL&#41;](../../ssma/sybase/testing-migrated-database-objects-sybasetosql.md)  
  
