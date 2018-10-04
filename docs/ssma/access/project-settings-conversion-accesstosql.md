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
ms.openlocfilehash: df03cfe48fe66b359cb9ec054a82b24b4a8ce3dc
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47783779"
---
# <a name="project-settings-conversion-accesstosql"></a>Project Settings (Conversion) (AccessToSQL)
Die projekteinstellungen für die Konvertierung können Sie konfigurieren, wie die Objekte aus den Zugriff auf Datenbankobjekte, konvertiert werden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure-Datenbankobjekte.  
  
Im Bereich für die Konvertierung finden Sie in der **Projekteinstellungen** und **Projekt Standardeinstellungen** Dialogfelder.  
  
-   Verwenden der **Projekteinstellungen** Dialogfeld zum Festlegen von Konfigurationsoptionen für das aktuelle Projekt. Die Konvertierungseinstellungen für den Zugriff auf die **Tools** , wählen Sie im Menü **Projekteinstellungen**, klicken Sie auf **allgemeine** am unteren Rand der linken Seite, und wählen Sie dann  **Konvertierung**.  
  
-   Verwenden der **Projekt Standardeinstellungen** Dialogfeld zum Festlegen von Konfigurationsoptionen für alle Projekte. Die Konvertierungseinstellungen für den Zugriff auf die **Tools** , wählen Sie im Menü **Projekt Standardeinstellungen**, wählen Sie die Migration-Projekttyp, die für die Einstellungen erforderlich sind, angezeigt oder geändert werden,  **Migration Zielversion** Dropdown-Liste, klicken Sie auf **allgemeine** am unteren Rand der linken Seite, und wählen Sie dann **Konvertierung**.  
  
## <a name="options"></a>Tastatur  
**Fügen Sie Primärschlüssel**  
Erstellt einen neuen primären Schlüssel in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure-Tabelle, wenn eine Access-Tabelle ohne Primärschlüssel oder eindeutigen Index verfügt.  
  
-   **Im Modus Standard**: False  
  
-   **Vollständige**: False  
  
-   **Vollständiger Modus**: "true"  
  
Beim Verbinden mit SQL Azure, ist es standardmäßig "true". **Timestamp-Spalten hinzufügen**  
Gibt an, ob es sich bei SSMA einen Timestamp-Wert erstellen soll, wenn dies erforderlich ist.  
  
-   **Im Modus Standard**: lassen Sie SSMA entscheiden  
  
-   **Vollständige**: nie  
  
-   **Vollständiger Modus**: lassen Sie SSMA entscheiden  
  
**Ein Daten-Bewertungsbericht mit Konvertierung Bewertungsberichte einschließen**  
Enthält eine Bewertung von Daten in den Bewertungsbericht.  
  
-   **Im Modus Standard**: "true"  
  
-   **Vollständige**: False  
  
-   **Vollständiger Modus**: "true"  
  
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
  
-   **Im Modus Standard**: "true"  
  
-   **Vollständige**: False  
  
-   **Vollständiger Modus**: "true"  
  
**Warnen Sie, wenn Bezeichnername geändert wird.**  
Zeigt eine Meldung in den Bewertungsbericht und dem Ausgabebereich angezeigt, wenn ein Bezeichner von SSMA geändert wird.  
  
-   **Im Modus Standard**: "true"  
  
-   **Vollständige**: False  
  
-   **Vollständiger Modus**: "true"  
  
**Warnen Sie, wenn Bezeichner in Anführungszeichen eingeschlossen**  
Zeigt eine Meldung in den Bewertungsbericht und dem Ausgabebereich angezeigt, wenn ein Bezeichner von SSMA zitiert wird. Bezeichner ist erforderlich, wenn der Name ein Schlüsselwort ist oder Sonderzeichen enthält.  
  
-   **Im Modus Standard**: "true"  
  
-   **Vollständige**: False  
  
-   **Vollständiger Modus**: "true"  
  
## <a name="see-also"></a>Siehe auch  
[Benutzer-Schnittstelle Reference(Access)](http://msdn.microsoft.com/en-us/af24c303-4a41-449b-9c86-d6558a97e839)  
  
