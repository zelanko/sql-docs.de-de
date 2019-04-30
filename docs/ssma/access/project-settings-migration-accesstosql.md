---
title: Project Settings (Migration) (AccessToSQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Migration settings
- Project Settings dialog box, Migration
ms.assetid: 4caebc9c-8680-4b99-a8fa-89c43161c95d
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 441366208d2bfd886794dd7e50dca7e0aef7b3ff
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63299289"
---
# <a name="project-settings-migration-accesstosql"></a>Project Settings (Migration) (AccessToSQL)
Die projekteinstellungen für die Migration können Sie konfigurieren, wie Daten migriert werden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure.  
  
Der Bereich für die Migration finden Sie in der **Projekteinstellungen** und **Projekt Standardeinstellungen** Dialogfelder.  
  
-   Verwenden der **Projekteinstellungen** Dialogfeld zum Festlegen von Konfigurationsoptionen für das aktuelle Projekt. Um auf den migrationseinstellungen der **Tools** , wählen Sie im Menü **Projekteinstellungen**, klicken Sie auf **allgemeine** am unteren Rand der linken Bereich ein, und klicken Sie dann auf  **Migration**.  
  
-   Verwenden der **Projekt Standardeinstellungen** Dialogfeld zum Festlegen von Konfigurationsoptionen für alle Projekte. Um auf den migrationseinstellungen der **Tools** , wählen Sie im Menü **Projekt Standardeinstellungen**, wählen den Projekttyp in **Migration Zielversion** im Kombinationsfeld, von denen Sie die Einstellungen zuzugreifen, klicken Sie auf **allgemeine** am unteren Rand der linken Bereich ein, und klicken Sie dann auf **Migration**.  
  
## <a name="options"></a>Optionen  
**Check-Einschränkungen**  
Gibt an, ob SSMA Einschränkungen überprüft werden sollen, wenn sie Daten in Tabellen hinzufügt.  
  
-   **Im Modus Standard**: False  
  
-   **Vollständige**: Wahr  
  
-   **Vollständiger Modus**: False  
  
**Trigger auslösen**  
Gibt an, ob SSMA einfügen Trigger ausgelöst werden soll, wenn sie Daten hinzufügt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Tabellen.  
  
-   **Im Modus Standard**: False  
  
-   **Vollständige**: Wahr  
  
-   **Vollständiger Modus**: False  
  
**Identität beibehalten**  
Gibt an, ob SSMA Zugriff, Identity-Werte beibehalten, wenn sie Daten hinzufügt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Wenn dieser Wert "False" [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Identitätswerte zuweist.  
  
-   **Im Modus Standard**: Wahr  
  
-   **Vollständige**: Wahr  
  
-   **Vollständiger Modus**: False  
  
**NULL-Werte beibehalten**  
Gibt an, ob SSMA behält null-Werte in den Quelldaten aus, wenn sie Daten hinzufügt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], unabhängig davon, die im angegebenen Standardwerte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   **Im Modus Standard**: Wahr  
  
-   **Vollständige**: False  
  
-   **Vollständiger Modus**: Wahr  
  
**Tabellensperren**  
Gibt an, ob es sich bei SSMA Tabellen sperrt, wenn sie Daten in Tabellen während der Datenmigration hinzufügt. Wenn der Wert "false" ist, wird in SSMA Zeilensperren verwendet.  
  
-   **Im Modus Standard**: Wahr  
  
-   **Vollständige**: Wahr  
  
-   **Vollständiger Modus**: Wahr  
  
**Ersetzen Sie dies nicht unterstützte Datumswerte**  
Gibt an, ob SSMA Zugriffsdaten einwirken soll, die älter als Frühestes unterstütztes sind [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] "DateTime"-Datum (01 Januar 1753).  
  
-   Um das aktuelle Datum zu erhalten, wählen Sie **nichts**. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datumsangaben vor dem 01 Januar 1753 wird in eine Datetime-Spalte nicht akzeptiert werden. Wenn Sie ältere Daten verwenden, müssen Sie die Datums-/ Uhrzeitwerten in Zeichenwerten enthalten, die konvertieren.  
  
-   Wählen Sie zum Konvertieren von Datumsangaben vor dem 01 Januar 1753 auf NULL **durch NULL Ersetzen**.  
  
-   Um Datumsangaben vor dem 01 Januar 1753 mit einem unterstützten Datum ersetzen möchten, wählen Sie **ersetzen Sie dies durch nächste unterstützte Datum**. Bei Auswahl dieses Werts in der Standardeinstellung, die nächste werden unterstützte Datum als 01 Januar 1753 ausgewählt werden.  
  
**Batchgröße**  
Batchgröße, die während der Migration von Daten verwendet werden. Eine Transaktion wird nach jedem Batch protokolliert. Standardmäßig ist die Batchgröße für alle Schemas 10000.  
  
## <a name="see-also"></a>Siehe auch  
[Benutzer-Schnittstelle Reference(Access)](https://msdn.microsoft.com/af24c303-4a41-449b-9c86-d6558a97e839)  
  
