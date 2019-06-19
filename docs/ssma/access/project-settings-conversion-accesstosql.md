---
title: Projekteinstellungen (Konvertierung) (AccessToSQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- conversion, options described
- Project Settings dialog box, Conversion
ms.assetid: bcebc635-c638-4ddb-924c-b9ccfef86388
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 2489442eb8de9d8d0ebfb5d8ed902dd2792e22f2
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63299145"
---
# <a name="project-settings-conversion-accesstosql"></a>Project Settings (Conversion) (AccessToSQL)
Die projekteinstellungen für die Konvertierung können Sie konfigurieren, wie die Objekte aus den Zugriff auf Datenbankobjekte, konvertiert werden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure-Datenbankobjekte.  
  
Im Bereich für die Konvertierung finden Sie in der **Projekteinstellungen** und **Projekt Standardeinstellungen** Dialogfelder.  
  
-   Verwenden der **Projekteinstellungen** Dialogfeld zum Festlegen von Konfigurationsoptionen für das aktuelle Projekt. Die Konvertierungseinstellungen für den Zugriff auf die **Tools** , wählen Sie im Menü **Projekteinstellungen**, klicken Sie auf **allgemeine** am unteren Rand der linken Seite, und wählen Sie dann  **Konvertierung**.  
  
-   Verwenden der **Projekt Standardeinstellungen** Dialogfeld zum Festlegen von Konfigurationsoptionen für alle Projekte. Die Konvertierungseinstellungen für den Zugriff auf die **Tools** , wählen Sie im Menü **Projekt Standardeinstellungen**, wählen Sie die Migration-Projekttyp, die für die Einstellungen erforderlich sind, angezeigt oder geändert werden,  **Migration Zielversion** Dropdown-Liste, klicken Sie auf **allgemeine** am unteren Rand der linken Seite, und wählen Sie dann **Konvertierung**.  
  
## <a name="options"></a>Optionen  
**Fügen Sie Primärschlüssel**  
Erstellt einen neuen primären Schlüssel in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure-Tabelle, wenn eine Access-Tabelle ohne Primärschlüssel oder eindeutigen Index verfügt.  
  
-   **Im Modus Standard**: False  
  
-   **Vollständige**: False  
  
-   **Vollständiger Modus**: Wahr  
  
Beim Verbinden mit SQL Azure, ist es standardmäßig "true". **Timestamp-Spalten hinzufügen**  
Gibt an, ob es sich bei SSMA einen Timestamp-Wert erstellen soll, wenn dies erforderlich ist.  
  
-   **Im Modus Standard**: Lassen Sie SSMA entscheiden  
  
-   **Vollständige**: Never  
  
-   **Vollständiger Modus**: Lassen Sie SSMA entscheiden  
  
**Ein Daten-Bewertungsbericht mit Konvertierung Bewertungsberichte einschließen**  
Enthält eine Bewertung von Daten in den Bewertungsbericht.  
  
-   **Im Modus Standard**: Wahr  
  
-   **Vollständige**: False  
  
-   **Vollständiger Modus**: Wahr  
  
**Nachrichtentyp, wenn ein Primärschlüssel auf NULL festlegbare Spalten enthalten**  
Gibt den Typ der Nachricht (Warnung, Fehler oder "Nothing"), die im Ausgabebereich SSMA anzeigt, wenn Primärschlüssel mit auf NULL festlegbare Spalten gefunden.  
  
-   **Im Modus Standard**: Warnung  
  
-   **Vollständige**: keine Meldung  
  
-   **Vollständiger Modus**: Fehler  
  
**Nachrichtentyp, wenn die foreign Key-Spalten mit verschiedenen Größen sind**  
Gibt den Typ der Nachricht (Warnung, Fehler oder "Nothing"), die im Ausgabebereich SSMA anzeigt, wenn ein Fremdschlüssel mit falscher TEXT gefunden.  
  
-   **Im Modus Standard**: Warnung  
  
-   **Vollständige**: keine Meldung  
  
-   **Vollständiger Modus**: Fehler  
  
**Nachrichtentyp beim Memospalten indiziert werden**  
Gibt den Typ der Meldung (Warnung, Fehler oder nichts) aus mit SSMA im Ausgabebereich angezeigt wird, wenn einen Index gefunden wird, die enthält eine **Memo** Spalte.  
  
-   **Im Modus Standard**: Warnung  
  
-   **Vollständige**: keine Meldung  
  
-   **Vollständiger Modus**: Fehler  
  
**Warnen, wenn eine komplexe Abfrage einen Platzhalter verwendet (\&#42;)**  
Wenn Sie ein Spaltennamen in einer SELECT-Anweisung ein Platzhalter (*) ist, wird eine Warnung im Bereich der Ausgabe und Fehlerliste angezeigt.  
  
-   **Im Modus Standard**: Wahr  
  
-   **Vollständige**: False  
  
-   **Vollständiger Modus**: Wahr  
  
**Warnen Sie, wenn Bezeichnername geändert wird.**  
Zeigt eine Meldung in den Bewertungsbericht und dem Ausgabebereich angezeigt, wenn ein Bezeichner von SSMA geändert wird.  
  
-   **Im Modus Standard**: Wahr  
  
-   **Vollständige**: False  
  
-   **Vollständiger Modus**: Wahr  
  
**Warnen Sie, wenn Bezeichner in Anführungszeichen eingeschlossen**  
Zeigt eine Meldung in den Bewertungsbericht und dem Ausgabebereich angezeigt, wenn ein Bezeichner von SSMA zitiert wird. Bezeichner ist erforderlich, wenn der Name ein Schlüsselwort ist oder Sonderzeichen enthält.  
  
-   **Im Modus Standard**: Wahr  
  
-   **Vollständige**: False  
  
-   **Vollständiger Modus**: Wahr  
  
## <a name="see-also"></a>Siehe auch  
[Benutzer-Schnittstelle Reference(Access)](https://msdn.microsoft.com/af24c303-4a41-449b-9c86-d6558a97e839)  
  
