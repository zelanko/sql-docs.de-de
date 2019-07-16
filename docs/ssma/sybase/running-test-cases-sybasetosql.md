---
title: Ausführen von Testfällen (SybaseToSQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Tester Component,Execution Steps
ms.assetid: 195ffdef-cfde-4bf4-a3ae-e7402bb07972
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 73047e0741d4dee12ecec3e83df308e3f7abd343
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68021018"
---
# <a name="running-test-cases-sybasetosql"></a>Ausführen von Testfällen (SybaseToSQL)
Wenn SSMA Tester einen Testfall ausgeführt wird, führt die Objekte, die zu Testzwecken ausgewählt, und erstellt einen Bericht über die Ergebnisse der Überprüfung. Wenn die Ergebnisse auf beiden Plattformen identisch sind, war der Test erfolgreich. Die Entsprechung von Objekten zwischen Sybase und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] richtet sich danach die schemazuordnung Einstellungen für das aktuelle SSMA-Projekt.  
  
Eine unerlässliche Anforderung für der Test erfolgreich ist, dass alle Sybase-Objekte konvertiert und in die Zieldatenbank geladen werden. Darüber hinaus sollten die Daten der migriert werden, damit der Inhalt der Tabellen auf beiden Plattformen synchronisiert werden.  
  
## <a name="run-test-case"></a>Testfall ausführen  
So führen Sie die vorbereiteten Testfall aus:  
  
1.  Klicken Sie auf die **ausführen** Schaltfläche.  
  
2.  In der **Herstellen einer Verbindung mit Sybase** Dialogfeld Geben Sie die Verbindungsinformationen, und klicken Sie dann auf **Connect**.  
  
Wenn der Test abgeschlossen ist, wird der Testfall-Bericht erstellt. Klicken Sie auf die **Bericht** Schaltfläche zum Anzeigen der [Viewing Test Case Reports &#40;SybaseToSQL&#41;](../../ssma/sybase/viewing-test-case-reports-sybasetosql.md). Das Ergebnis des Tests (Bericht "Testfall") wird automatisch gespeichert, der [mithilfe von Test Repositories &#40;SybaseToSQL&#41; ](../../ssma/sybase/using-test-repositories-sybasetosql.md) für die spätere Verwendung.  
  
## <a name="test-case-execution-steps"></a>Testfall-Ausführungsschritte  
  
### <a name="prerequisites"></a>Vorraussetzungen  
SSMA-Tester wird überprüft, ob alle Voraussetzungen, für die testausführung vor Beginn des Tests erfüllt sind. Wenn bestimmte Bedingungen nicht erfüllt sind, wird eine Fehlermeldung angezeigt.  
  
### <a name="initialization"></a>Initialisierung  
In diesem Schritt SSMA-Tester, die zusätzlichen Objekte (Tabellen, Trigger und Sichten) sowohl auf die Sybase erstellt und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Nachverfolgen von Änderungen vorgenommen, die in den betroffenen Tabellen, die für die Überprüfung ausgewählt werden, wenn Tabelle Vergleiche Modus ist ermöglichen **ändert sich nur**.  
  
Wird davon ausgegangen Sie, dass die überprüfte Tabelle USER_TABLE heißt. Für eine Tabelle werden die folgenden zusätzlichen Objekte in Sybase erstellt.  
  
Die folgenden Objekte werden an Sybase erstellt, in der Datenbank SSMATESTER2005db oder SSMATESTER2008db und zur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in der Datenbank Ssmatesterdb_syb.  
  
|Name|Typ|Beschreibung|  
|--------|--------|---------------|  
|USER_TABLE$Trg|Trigger|Trigger, die Überwachung der Änderungen in der Tabelle überprüft werden.|  
|USER_TABLE$ Aud|Tabelle|Die Tabelle, in dem Zeilen gelöschte und überschriebene gespeichert werden.|  
|USER_TABLE$ AudID|Tabelle|Die Tabelle, in dem ein neue und geänderte Zeilen gespeichert werden.|  
|USER_TABLE|Ansicht|Vereinfachte Darstellung der tabellenänderungen.|  
|USER_TABLE$new|Ansicht|Vereinfachte Darstellung von Zeilen eingefügt und überschrieben.|  
|USER_TABLE$new_id|Ansicht|ID des eingefügten und geänderter Zeilen.|  
|USER_TABLE$old|Ansicht|Vereinfachte Darstellung von Zeilen gelöscht und überschrieben.|  
  
Das folgende Objekt ist in der Datenbank der überprüften Tabelle in Sybase erstellt und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
|Name|Typ|Beschreibung|  
|--------|--------|---------------|  
|USER_TABLE$Trg|Trigger|Trigger, die Überwachung der Änderungen in der Tabelle überprüft werden.|  
  
### <a name="test-object-calls"></a>Testen der Aufrufe  
SSMA-Tester an dieser Stelle ruft jedes Objekt, das für die Tests ausgewählt haben, werden die Ergebnisse verglichen und zeigt den Bericht.  
  
### <a name="finalization"></a>Beendigung  
Während der Finalisierung bereinigt SSMA Tester die zusätzlichen Objekte, erstellt die **Initialisierung** Schritt.  
  
## <a name="next-step"></a>Nächster Schritt  
[Anzeigen von Berichten für Testfall &#40;SybaseToSQL&#41;](../../ssma/sybase/viewing-test-case-reports-sybasetosql.md)  
  
## <a name="see-also"></a>Siehe auch  
[Auswählen und Konfigurieren von Objekten mit Test &#40;SybaseToSQL&#41;](../../ssma/sybase/selecting-and-configuring-objects-to-test-sybasetosql.md)  
[Auswählen und Konfigurieren von betroffenen Objekten &#40;SybaseToSQL&#41;](../../ssma/sybase/selecting-and-configuring-affected-objects-sybasetosql.md)  
[Testen von migrierten Datenbankobjekten &#40;SybaseToSQL&#41;](../../ssma/sybase/testing-migrated-database-objects-sybasetosql.md)  
  
