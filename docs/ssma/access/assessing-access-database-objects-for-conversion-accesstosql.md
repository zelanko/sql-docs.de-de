---
title: Bewerten den Zugriff auf Datenbankobjekte für die Konvertierung (AccessToSQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- assessing SQL
- assessing syntax
- assessment reports
- creating assessment reports
- estimating migration effort
- reports
- SQL, assessing
- syntax, assessing
ms.assetid: 8b9e23d6-da62-437a-8c05-8ad2628b9441
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 7d265ea1bd3b2461219858d39fd0b9164999cc30
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62650978"
---
# <a name="assessing-access-database-objects-for-conversion-accesstosql"></a>Bewerten den Zugriff auf Datenbankobjekte für die Konvertierung (AccessToSQL)
Bevor Sie Objekte laden und Migrieren von Daten zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure, sollten Sie ermitteln, wie viel der Migration erfolgreich sein wird und wie lange die Konvertierung werden kann. SSMA kann ein Bewertungsbericht enthält, die den Prozentsatz von Objekten, der in konvertiert wurden erstellen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure-Syntax und die Uhrzeit schätzt, für die Migration durchführen. SSMA können Sie außerdem die spezifischen Probleme anzeigen, die Konvertierungsfehler verursacht hat.  
  
## <a name="creating-assessment-reports"></a>Erstellen Berichte zur Bewertung  
Wenn es sich um ein Bewertungsbericht erstellt, konvertiert SSMA der ausgewählten den Zugriff auf Datenbankobjekte, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure-Syntax, und klicken Sie dann die Ergebnisse werden angezeigt.  
  
**So erstellen Sie einen Assessment-Bericht**  
  
1.  Wählen Sie in der Access-Metadaten-Explorer Datenbanken, die Sie bewerten möchten.  
  
2.  Um einzelne Objekte zu unterdrücken, deaktivieren Sie die Kontrollkästchen neben den Objekten, die Sie nicht, um zu bewerten möchten.  
  
3.  Mit der rechten Maustaste **Datenbanken**, und wählen Sie dann **Bericht erstellen**.  
  
    Sie können auch einzelne Objekte analysieren, indem Sie mit der rechten Maustaste ein Objekt, und wählen Sie dann **Bericht erstellen**.  
  
    SSMA zeigt den Fortschritt in der Statusleiste am unteren Rand des Fensters. Wenn im Ausgabebereich angezeigt wird, werden auch Meldungen im Ausgabebereich angezeigt.  
  
Wenn die Bewertung abgeschlossen ist, wird die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Migration Assistant für Access: Fenster "Assessment" wird angezeigt.  
  
## <a name="using-assessment-reports"></a>Verwenden von Assessment-Berichten  
Das Fenster Bewertungsbericht enthält drei Bereiche: einen Explorer, ein Detailbereich und ein Bereich "Meldung".  
  
-   Explorer-Bereich können Sie die Objekte zu durchsuchen, die bewertet wurden. Sie können Elemente in diesem Bereich in einzelne Tabellen, Indizes und Schlüssel Drilldown klicken.  
  
-   Im Detailbereich werden die Konvertierungsstatistiken für das ausgewählte Objekt angezeigt.  
  
-   Der Bereich "Meldung" zeigt die Fehler, Warnungen und informationsmeldungen für die Konvertierung, und die geschätzte Dauer für die Durchführung der Migration und die einzelnen Fehler Korrektur Schritte.  
  
Sie sollten die Fehler beheben, bevor Sie den Bewertungsbericht erneut ausführen, oder Konvertieren von Schemas. Um Fehler zu finden, klicken Sie auf die **Fehler** im Meldungsbereich Schaltfläche, und erweitern Sie dann die einzelnen Fehler um eine Liste der Objekte anzuzeigen, in dem der Fehler aufgetreten ist. Wenn Sie ein Objekt im Meldungsbereich klicken, werden alle Fehler und Warnungen für dieses Objekt im Detailbereich angezeigt.  
  
## <a name="next-step"></a>Nächster Schritt  
[Converting Access Database Objects (Konvertieren von Access-Datenbankobjekten)](converting-access-database-objects-accesstosql.md)  
  
## <a name="see-also"></a>Siehe auch  
[Migrieren von Access-Datenbanken zu SQLServer](migrating-access-databases-to-sql-server-azure-sql-db-accesstosql.md)  
  
