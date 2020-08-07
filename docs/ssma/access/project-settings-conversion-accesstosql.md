---
title: Projekteinstellungen (Konvertierung) (accesstosql) | Microsoft-Dokumentation
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
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: 8889e0d869960f8300194afe31fe87b7f0cf2346
ms.sourcegitcommit: e8f6c51d4702c0046aec1394109bc0503ca182f0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/07/2020
ms.locfileid: "87937805"
---
# <a name="project-settings-conversion-accesstosql"></a>Projekteinstellungen (Konvertierung) (accesstosql)
Mithilfe der Konvertierungs Projekteinstellungen können Sie konfigurieren, wie Objekte aus Access-Datenbankobjekten in- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbankobjekte konvertiert werden.  
  
Der Bereich Konvertierung ist in den Dialogfeldern **Projekteinstellungen** und **Standard Projekteinstellungen** verfügbar.  
  
-   Verwenden Sie das Dialogfeld **Projekteinstellungen** , um Konfigurationsoptionen für das aktuelle Projekt festzulegen. Um auf die Konvertierungs Einstellungen zuzugreifen, wählen Sie **im Menü Extras** die Option **Projekteinstellungen**aus, klicken Sie unten im linken Bereich auf **Allgemein** , und wählen Sie dann **Konvertierung**aus.  
  
-   Verwenden Sie das Dialogfeld **Standard Projekteinstellungen** , um Konfigurationsoptionen für alle Projekte festzulegen. Um auf die Konvertierungs Einstellungen zuzugreifen, wählen Sie **im Menü Extras** die Option **Standard Projekteinstellungen**aus, wählen Sie den Migrations Projekttyp, für den die Einstellungen angezeigt werden müssen/Changed in der Dropdown Liste **Migrations Ziel Version** aus, klicken Sie unten im linken Bereich auf **Allgemein** , und klicken Sie dann auf **Konvertierung**.  
  
## <a name="options"></a>Optionen  
**Primärschlüssel hinzufügen**  
Erstellt einen neuen Primärschlüssel in der- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder-SQL Azure Tabelle, wenn eine Zugriffs Tabelle keinen Primärschlüssel oder eindeutigen Index aufweist.  
  
-   **Standardmodus**: false  
  
-   **Optimistischer Modus**: false  
  
-   **Vollständiger Modus**: true  
  
Wenn eine Verbindung mit SQL Azure besteht, ist Sie standardmäßig "true". **Zeitstempel-Spalten hinzufügen**  
Gibt an, ob SSMA einen Zeitstempelwert erstellen soll, wenn dies erforderlich ist.  
  
-   **Standardmodus**: SSMA-Entscheidung zulassen  
  
-   **Optimistischer Modus**: nie  
  
-   **Vollständiger Modus**: SSMA entscheiden lassen  
  
**Einschließen eines Daten Bewertungsberichts mithilfe von Konvertierungs Bewertungsberichten**  
Schließt eine Daten Bewertung in den Bewertungsbericht ein.  
  
-   **Standardmodus**: true  
  
-   **Optimistischer Modus**: false  
  
-   **Vollständiger Modus**: true  
  
**Nachrichtentyp, wenn ein Primärschlüssel Spalten enthält, die Nullwerte zulassen**  
Gibt den Typ der Meldung (Warnung, Fehler oder nichts) an, die SSMA im Ausgabebereich anzeigt, wenn Primärschlüssel mit Spalten gefunden werden, die NULL-Werte zulassen.  
  
-   **Standardmodus**: Warnung  
  
-   **Optimistischer Modus**: keine Meldung  
  
-   **Vollmodus**: Fehler  
  
**Nachrichtentyp, wenn Fremdschlüssel Spalten unterschiedliche Größen haben**  
Gibt den Typ der Meldung (Warnung, Fehler oder nichts) an, die SSMA im Ausgabebereich anzeigt, wenn ein falscher Text Fremdschlüssel gefunden wird.  
  
-   **Standardmodus**: Warnung  
  
-   **Optimistischer Modus**: keine Meldung  
  
-   **Vollmodus**: Fehler  
  
**Nachrichtentyp, wenn Memo Spalten indiziert werden**  
Gibt den Typ der Meldung (Warnung, Fehler oder nichts) an, die SSMA im Ausgabebereich anzeigt, wenn ein Index gefunden wird, der eine **Memo** Spalte enthält.  
  
-   **Standardmodus**: Warnung  
  
-   **Optimistischer Modus**: keine Meldung  
  
-   **Vollmodus**: Fehler  
  
**Warnen, wenn eine komplexe Abfrage einen Platzhalter verwendet ( \& #42;)**  
Zeigt eine Warnung im Ausgabebereich an und Fehlerliste, wenn ein Spaltenname in einer SELECT-Anweisung ein Platzhalter (*) ist.  
  
-   **Standardmodus**: true  
  
-   **Optimistischer Modus**: false  
  
-   **Vollständiger Modus**: true  
  
**Beim Ändern des Bezeichnernamens warnen**  
Zeigt eine Meldung im Bewertungsbericht und im Ausgabebereich an, wenn ein objektbezeichnername von SSMA geändert wird.  
  
-   **Standardmodus**: true  
  
-   **Optimistischer Modus**: false  
  
-   **Vollständiger Modus**: true  
  
**Warnen, wenn Bezeichner in Anführungszeichen eingeschlossen wird**  
Zeigt eine Meldung im Bewertungsbericht und im Ausgabebereich an, wenn ein objektbezeichnername von SSMA angegeben wird. Anführungszeichen sind erforderlich, wenn der Name ein Schlüsselwort ist oder Sonderzeichen enthält.  
  
-   **Standardmodus**: true  
  
-   **Optimistischer Modus**: false  
  
-   **Vollständiger Modus**: true  
  
## <a name="see-also"></a>Weitere Informationen  
[Referenz zur Benutzeroberfläche (Zugriff)](https://msdn.microsoft.com/af24c303-4a41-449b-9c86-d6558a97e839)  
  
