---
description: Konvertierungseinstellungen (MySqlToSql)
title: Konvertierungs Einstellungen (mysqltoisql) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: f551cf6e-1575-4206-9cca-975b5b43a6b8
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: 7547984e97bb47a640c162743fe0b069b38f7dff
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88418466"
---
# <a name="conversion-settings-mysqltosql"></a>Konvertierungseinstellungen (MySqlToSql)
Auf der Registerkarte **"Einstellungen"** können Benutzereinstellungen auf Knotenebene festlegen. Die Registerkarte wird auf den folgenden Metabasisknoten verfügbar sein:  
  
-   Datenbankknoten  
  
-   Functions-Kategorie  
  
-   Funktionsknoten  
  
-   Tabellen Kategorie  
  
-   Tabellen Knoten  
  
## <a name="specifications"></a>Spezifikationen  
Die Registerkarte **Einstellungen** verfügt über zwei Benutzereinstellungen:  
  
1.  Funktions Konvertierung  
  
2.  Tabellen Konvertierung  
  
Diese Einstellungen werden basierend auf dem Typ der Metabasisknoten verfügbar. Beispielsweise ist die Einstellung für die Funktions Konvertierung im Tabellen Knoten nicht verfügbar.  
  
> [!NOTE]  
> -   Die vom Benutzer vorgenommenen Änderungen werden im Projekt Arbeitsbereich als separate Einstellungsdatei gespeichert.  
> -   Die Erweiterung dieser Datei wird **ccprefs**sein.  
  
1.  **Einstellung für Funktions Konvertierung:**  
  
    1.  Diese Registerkarte enthält **die Option "Funktions Konvertierung erzwingen"** . Die Option kann einen der folgenden vier Werte aufweisen:  
  
        -   Gemäß Projekteinstellungen konvertieren [geerbt]  
  
        -   Immer in eine Funktion konvertieren  
  
        -   Immer in eine Prozedur konvertieren  
  
        -   Gemäß Projekteinstellungen konvertieren  
  
    2.  Basierend auf den Einstellungen wird die Funktion entweder in eine Funktion oder in eine gespeicherte Prozedur konvertiert.  
  
    3.  Die vom Benutzer vorgenommenen Einstellungen werden in der Datei mit den kaskadierenden Einstellungen gespeichert, wenn Sie auf **die Schaltfläche Übernehmen klicken.**  
  
2.  **Einstellung für Tabellen Konvertierung:**  
  
    1.  Diese Registerkarte enthält **die Option "ROWID-Hilfsspalten Generierung unterdrücken"** . Die Option kann einen der folgenden vier Werte aufweisen:  
  
        -   Gemäß Projekteinstellungen konvertieren [geerbt]  
  
        -   Ja  
  
        -   Nein  
  
        -   Gemäß Projekteinstellungen konvertieren  
  
    2.  Wenn **"Ja"** festgelegt ist, wird durch diese Einstellung die Erstellung der Erstellung von ROWID-Erweiterungs Spalten in Ziel Tabellen untersagt.  
  
    3.  Die vom Benutzer vorgenommenen Einstellungen werden in der Datei mit der überlappenden Einstellungen gespeichert, wenn Sie auf die Schaltfläche **anwenden** klicken.  
  
## <a name="see-also"></a>Weitere Informationen  
[Projekteinstellungen (Konvertierung) (MySQL in SQL)](https://msdn.microsoft.com/7ad5fe44-6445-4ba8-a457-5af792631f11)  
  
