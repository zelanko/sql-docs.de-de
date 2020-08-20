---
description: Projekteinstellungen (Migration) (accesstosql)
title: Projekteinstellungen (Migration) (accesstosql) | Microsoft-Dokumentation
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
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: 94bd5cc9a8cb0db9079db981ec50a5fa6af7b20c
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88480528"
---
# <a name="project-settings-migration-accesstosql"></a>Projekteinstellungen (Migration) (accesstosql)
Mit den Migrationsprojekt Einstellungen können Sie konfigurieren, wie Daten zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure migriert werden.  
  
Der Bereich Migration ist in den Dialogfeldern **Projekteinstellungen** und **Standard Projekteinstellungen** verfügbar.  
  
-   Verwenden Sie das Dialogfeld **Projekteinstellungen** , um Konfigurationsoptionen für das aktuelle Projekt festzulegen. Um auf die Migrations Einstellungen zuzugreifen, wählen **Sie im Menü Extras** die Option **Projekteinstellungen**aus, klicken Sie unten im linken Bereich auf **Allgemein** , und klicken Sie dann auf **Migration**.  
  
-   Verwenden Sie das Dialogfeld **Standard Projekteinstellungen** , um Konfigurationsoptionen für alle Projekte festzulegen. Um auf die Migrations Einstellungen zuzugreifen, wählen **Sie im Menü Extras die Option** **Standard Projekteinstellungen**aus, wählen Sie im Kombinations Feld **Migrations Ziel Version** den Projekttyp aus, für den Sie auf die Einstellungen zugreifen möchten, klicken Sie unten im linken Bereich auf **Allgemein** , und klicken Sie dann auf **Migration**.  
  
## <a name="options"></a>Tastatur  
**Check-Einschränkungen**  
Gibt an, ob SSMA Einschränkungen beim Hinzufügen von Daten zu Tabellen überprüfen soll.  
  
-   **Standardmodus**: false  
  
-   **Optimistischer Modus**: true  
  
-   **Vollständiger Modus**: false  
  
**Trigger auslösen**  
Gibt an, ob SSMA Einfügetrigger auslösen soll, wenn Daten zu Tabellen hinzugefügt werden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   **Standardmodus**: false  
  
-   **Optimistischer Modus**: true  
  
-   **Vollständiger Modus**: false  
  
**Identität beibehalten**  
Gibt an, ob SSMA beim Hinzufügen von Daten zu Zugriffs Identitäts Werte beibehält [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Wenn dieser Wert false ist, werden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Identitäts Werte zugewiesen.  
  
-   **Standardmodus**: true  
  
-   **Optimistischer Modus**: true  
  
-   **Vollständiger Modus**: false  
  
**NULL-Werte beibehalten**  
Gibt an, ob SSMA beim Hinzufügen von Daten zu NULL-Werte in den Quelldaten beibehält [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , unabhängig von den in angegebenen Standardwerten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   **Standardmodus**: true  
  
-   **Optimistischer Modus**: false  
  
-   **Vollständiger Modus**: true  
  
**Tabellensperren**  
Gibt an, ob SSMA Tabellen sperrt, wenn während der Datenmigration Daten zu Tabellen hinzugefügt werden. Wenn der Wert false ist, verwendet SSMA Zeilen sperren.  
  
-   **Standardmodus**: true  
  
-   **Optimistischer Modus**: true  
  
-   **Vollständiger Modus**: true  
  
**Nicht unterstützte Datumsangaben ersetzen**  
Gibt an, ob SSMA Zugriffsdaten korrigieren soll, die vor dem frühestmöglichen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datum (01. Januar 1753) liegen.  
  
-   Um die aktuellen Datumswerte beizubehalten, wählen Sie keine Aktion durch **führen**aus. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] akzeptiert keine Datumsangaben vor 01. Januar 1753 in einer datetime-Spalte. Wenn Sie ältere Datumsangaben verwenden, müssen Sie die DateTime-Werte in Zeichen Werte konvertieren.  
  
-   Um Datumsangaben vor 01. Januar 1753 in NULL zu konvertieren, wählen Sie **durch Null Ersetzen**aus.  
  
-   Um Datumsangaben vor 01. Januar 1753 durch ein unterstütztes Datum zu ersetzen, wählen Sie **durch das nächste unterstützte Datum ersetzen**aus. Wenn Sie diesen Wert auswählen, wird standardmäßig das nächste unterstützte Datum als 01. Januar 1753 ausgewählt.  
  
**Batchgröße**  
Batch Größe, die während der Datenmigration verwendet wird. Eine Transaktion wird nach jedem Batch protokolliert. Standardmäßig ist die Batch Größe für alle Schemas 10000.  
  
## <a name="see-also"></a>Weitere Informationen  
[Referenz zur Benutzeroberfläche (Zugriff)](https://msdn.microsoft.com/af24c303-4a41-449b-9c86-d6558a97e839)  
  
