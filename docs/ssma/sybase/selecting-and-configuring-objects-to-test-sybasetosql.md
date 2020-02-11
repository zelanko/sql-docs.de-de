---
title: Auswählen und Konfigurieren von zu testenden Objekten (sybaseto SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Tester Component,Parameter Comparision Setting
- Tester Component,Selecting Objects
ms.assetid: 89c23aad-bfee-4917-bc16-175288390ac0
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 2951d4c3bf1eae73ffd066d796b0e3dda4d28cf6
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68020963"
---
# <a name="selecting-and-configuring-objects-to-test-sybasetosql"></a>Auswählen und Konfigurieren von zu testenden Objekten (SybaseToSQL)
In diesem Schritt wählen Sie die zu testenden Objekte aus und konfigurieren die Einstellungen für den Vergleich der Ausgabeparameter der Prozeduren und Funktionen sowie die Rückgabewerte von Funktionen.  
  
## <a name="selection-of-objects-to-test"></a>Auswahl der zu testenden Objekte  
Überprüfen Sie in der Sybase-Objektstruktur, die sich auf der linken Seite des Fensters befindet, die Objekte, die Sie während des Testprozesses aufrufen möchten. Weitere Informationen finden Sie in der vollständigen Liste mit Test fähigen Objekten im Thema [Testen von migrierten Datenbankobjekten &#40;sybaseto SQL&#41;](../../ssma/sybase/testing-migrated-database-objects-sybasetosql.md) .  
  
Wenn SSMA Tester keines der für den Test ausgewählten Objekte unterstützt, wird der Link mit der Bezeichnung **einige ausgewählte Objekte enthält** unter der Struktur Objekte Fehler angezeigt. Klicken Sie auf diesen Link, um die Gründe anzuzeigen, warum diese Objekte nicht getestet werden können, und um die Auswahl falscher Objekte zu löschen.  
  
Auf der rechten Seite können Sie mehrere Seiten anzeigen. die **SQL** -Seite zeigt die Definition des aktuellen Objekts an. In den Seiten **Pre SQL** und **Post SQL** können Skripts angegeben werden, die vor und nach dem Aufruf des Testobjekts ausgeführt werden. Dies kann hilfreich sein, wenn das Objekt zusätzliche Objekte wie temporäre Tabellen oder Cursor benötigt. Die Seite **Parameter** listet die Parameter auf, wenn es sich bei dem Objekt um eine gespeicherte Prozedur oder eine Funktion handelt. Auf der Seite **Eigenschaften** werden zusätzliche Eigenschaften des Objekts angezeigt. Weitere Informationen finden Sie unter Beschreibung der **Parameter Vergleiche** und **aufrufswerte** unten.  
  
## <a name="parameter-comparison-settings"></a>Parameter Vergleichs Einstellungen  
Legen Sie die Vergleichs Regeln für Ausgabeparameter und Rückgabewerte auf der Seite **Parameter Vergleich** fest. Sie können die folgenden Einstellungen vornehmen.  
  
### <a name="use-during-comparisons"></a>Verwendung bei Vergleichen  
Aktiviert die Verwendung des ausgewählten Parameters im Vergleich mit Testergebnissen.  
  
-   Wenn Sie **true**auswählen, vergleicht SSMA den Ausgabewert dieses Parameters nach dem Ausführen der Prozedur auf Sybase mit dem entsprechenden Wert für.[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
-   Wenn Sie**false**auswählen, wird der Parameter von der Ergebnis Überprüfung ausgeschlossen.  
  
### <a name="use-custom-scale"></a>Benutzerdefinierte Skalierung verwenden  
Für Parameter des numerischen Datentyps "ungefähre Länge" und "mit fester Länge" können Sie für den Vergleich eine benutzerdefinierte Skala festlegen.  
  
-   Wenn Sie **true**auswählen, werden numerische Werte entsprechend dem **Vergleichs Skalierungs** Wert gerundet, bevor Sie verglichen werden.  
  
-   Wenn Sie**false**auswählen, ist der numerische Vergleich genau.  
  
### <a name="comparing-scale"></a>Vergleichen der Skala  
Nur verfügbar, wenn die Option **benutzerdefinierte Skalierung verwenden** auf **true**festgelegt ist. Dies ist die Genauigkeit für den numerischen Vergleich.  
  
### <a name="date-time-comparing"></a>Vergleichen von Datum und Uhrzeit  
Definiert, wie Datums-/Uhrzeitwerte verglichen werden.  
  
-   Wenn Sie die Option **gesamtes Datum vergleichen**auswählen, wird ein vollständiger Vergleich der Werte beider Plattformen ausgeführt.  
  
-   Wenn Sie **Datum nur vergleichen**auswählen, wird der Uhrzeit Teil ignoriert.  
  
-   Wenn Sie **nur die Zeit vergleichen**auswählen, wird der Datums Teil ignoriert.  
  
-   Wenn Sie die Option **Millisekunden ignorieren**auswählen, werden die Ergebnisse bis zu Sekunden verglichen.  
  
-   Wenn Sie **Datum und Millisekunden ignorieren**auswählen, wird das Ergebnis nur nach Zeit Teil verglichen, und die Sekundenbruchteile werden ignoriert.  
  
### <a name="ignore-strings-case"></a>Zeichen folgen ignorieren  
Steuert die Groß-/Kleinschreibung des Vergleichs.  
  
-   Wenn Sie **true**auswählen, wird beim Vergleich die Groß-/Kleinschreibung nicht beachtet.  
  
-   Wenn Sie **false**auswählen, wird beim Vergleich die Groß-/Kleinschreibung beachtet.  
  
### <a name="ignore-trailing-spaces"></a>Nachfolgende Leerzeichen ignorieren  
Steuert, wie nachfolgende Leerzeichen während des Vergleichs behandelt werden.  
  
-   Wenn Sie **true**auswählen, werden die verglichenen Zeichen folgen vor dem Vergleich mit der rechten Seite abgeschnitten.  
  
-   Wenn Sie **false**auswählen, werden nachfolgende Leerzeichen in den verglichenen Zeichen folgen beibehalten.  
  
## <a name="specify-input-values-for-procedures-and-functions-call-values"></a>Angeben von Eingabe Werten für Prozeduren und Funktionen (aufrufwerte)  
Sie können die Eingabeparameter Werte auf der Seite " **Werte aufrufen** " angeben. Mit der Schaltfläche " **aufrufen** " wird ein neuer-Befehl mit leeren Parameterwerten hinzugefügt. Mit der Schaltfläche " **Abrufen** " wird der aktuelle-Befehl entfernt.  
  
## <a name="next-step"></a>Nächster Schritt  
[Auswählen und konfigurieren betroffener Objekte &#40;Sybase&#41;](../../ssma/sybase/selecting-and-configuring-affected-objects-sybasetosql.md)  
  
## <a name="see-also"></a>Weitere Informationen  
[Testen von migrierten Datenbankobjekten &#40;sybaseto SQL&#41;](../../ssma/sybase/testing-migrated-database-objects-sybasetosql.md)  
  
