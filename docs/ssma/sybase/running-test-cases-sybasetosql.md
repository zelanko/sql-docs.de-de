---
description: Ausführen von Testfällen (SybaseToSQL)
title: Ausführen von Test Fällen (sybaseto SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Tester Component,Execution Steps
ms.assetid: 195ffdef-cfde-4bf4-a3ae-e7402bb07972
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: ea2b250f59a29a16bc77ad23e28b0823461a8ace
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88468753"
---
# <a name="running-test-cases-sybasetosql"></a>Ausführen von Testfällen (SybaseToSQL)
Wenn der SSMA-Tester einen Testfall ausführt, führt er die für das Testen ausgewählten Objekte aus und erstellt einen Bericht über Überprüfungs Ergebnisse. Wenn die Ergebnisse auf beiden Plattformen identisch sind, war der Test erfolgreich. Die Entsprechung von Objekten zwischen Sybase und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wird anhand der Schema-Mapping-Einstellungen für das aktuelle SSMA-Projekt festgelegt.  
  
Eine erforderliche Anforderung für einen erfolgreichen Test besteht darin, dass alle Sybase-Objekte konvertiert und in die Zieldatenbank geladen werden. Außerdem sollten die Tabellendaten migriert werden, damit die Inhalte der Tabellen auf beiden Plattformen synchronisiert werden.  
  
## <a name="run-test-case"></a>Testfall ausführen  
So führen Sie den vorbereiteten Testfall aus  
  
1.  Klicken Sie auf die Schaltfläche **Ausführen**.  
  
2.  Geben Sie im Dialogfeld **mit Sybase verbinden** die Verbindungsinformationen ein, und klicken Sie dann auf **verbinden**.  
  
Wenn der Test fertig ist, wird der Test Fallbericht erstellt. Klicken Sie auf die Schaltfläche **Bericht** , um die [Anzeige der Test Fallberichte &#40;sybaseto SQL&#41;](../../ssma/sybase/viewing-test-case-reports-sybasetosql.md)anzuzeigen. Das Ergebnis des Tests (Test Fallbericht) wird automatisch in [mithilfe von tespositorys &#40;sybasedesql-&#41;](../../ssma/sybase/using-test-repositories-sybasetosql.md) zur späteren Verwendung gespeichert.  
  
## <a name="test-case-execution-steps"></a>Testfall-Ausführungs Schritte  
  
### <a name="prerequisites"></a>Voraussetzungen  
Der SSMA-Tester prüft, ob alle Voraussetzungen für die Testausführung vor dem Start des Tests erfüllt sind. Wenn einige Bedingungen nicht erfüllt sind, wird eine Fehlermeldung angezeigt.  
  
### <a name="initialization"></a>Initialisierung  
In diesem Schritt erstellt SSMA Tester Hilfsobjekte (Tabellen, Trigger und Sichten) sowohl bei Sybase als auch bei [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Sie ermöglichen das verfolgen **von Änderungen,** die in den betroffenen Tabellen vorgenommen werden, die für die Überprüfung ausgewählt wurden, wenn der Tabellen Vergleichs Modus  
  
Angenommen, die überprüfte Tabelle hat den Namen USER_TABLE. Für eine solche Tabelle werden die folgenden Hilfsobjekte in Sybase erstellt.  
  
Die folgenden Objekte werden bei Sybase in der SSMATESTER2005db-oder SSMATESTER2008db-Datenbank und in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] der ssmatesterdb_syb-Datenbank erstellt.  
  
|Name|type|Beschreibung|  
|--------|--------|---------------|  
|USER_TABLE $ trg|Trigger|Löst die Überprüfung der Änderungen in der verifizierten Tabelle aus.|  
|USER_TABLE $ AUD|Tabelle|Tabelle, in der gelöschte und über schriebene Zeilen gespeichert werden.|  
|USER_TABLE $ audid|Tabelle|Tabelle, in der neue und geänderte Zeilen gespeichert werden.|  
|USER_TABLE|Ansicht|Vereinfachte Darstellung der Tabellen Änderungen.|  
|USER_TABLE $ New|Ansicht|Vereinfachte Darstellung von eingefügten und über schriebenen Zeilen.|  
|USER_TABLE $ new_id|Ansicht|Identifizierung eingefügter und geänderter Zeilen.|  
|USER_TABLE $ Old|Ansicht|Vereinfachte Darstellung gelöschter und überschriebener Zeilen.|  
  
Das folgende Objekt wird in der Datenbank der verifizierten Tabelle unter Sybase und erstellt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
|Name|type|Beschreibung|  
|--------|--------|---------------|  
|USER_TABLE $ trg|Trigger|Löst die Überprüfung der Änderungen in der verifizierten Tabelle aus.|  
  
### <a name="test-object-calls"></a>Testen von Objekt aufrufen  
Bei diesem Schritt ruft der SSMA-Tester alle für die Tests ausgewählten Objekte auf, vergleicht die Ergebnisse und zeigt den Bericht an.  
  
### <a name="finalization"></a>Abschluss  
Während der Fertigstellung bereinigt SSMA Tester die Hilfsobjekte, die beim **Initialisierungs** Schritt erstellt wurden.  
  
## <a name="next-step"></a>Nächster Schritt  
[Anzeigen von Test Fall berichten &#40;sybaseto SQL&#41;](../../ssma/sybase/viewing-test-case-reports-sybasetosql.md)  
  
## <a name="see-also"></a>Weitere Informationen  
[Auswählen und Konfigurieren von zu testenden Objekten &#40;sybaseto SQL-&#41;](../../ssma/sybase/selecting-and-configuring-objects-to-test-sybasetosql.md)  
[Auswählen und konfigurieren betroffener Objekte &#40;Sybase&#41;](../../ssma/sybase/selecting-and-configuring-affected-objects-sybasetosql.md)  
[Testen von migrierten Datenbankobjekten &#40;sybaseto SQL&#41;](../../ssma/sybase/testing-migrated-database-objects-sybasetosql.md)  
  
