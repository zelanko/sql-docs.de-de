---
description: Projekteinstellungen (Synchronisierung) (MySqlToSql)
title: Projekteinstellungen (Synchronisierung) (mysqlto SQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 42061ff7-e6e7-497b-a0d9-440b9cf5986c
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: 3ea89bcdf9b10fb50e74228a26bfcd5cead83aca
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88492383"
---
# <a name="project-settings-synchronization-mysqltosql"></a>Projekteinstellungen (Synchronisierung) (MySqlToSql)
Mithilfe der Synchronisierungs **Projekteinstellungen** können Sie konfigurieren, wie MySQL-Datenbankobjekte mit SQL Server-Datenbankobjekten synchronisiert werden.  
  
Die Standard Aktionen geben die Standardeinstellungen für die Aktualisierung von Objekten aus der MySQL-Datenbank und für die Synchronisierung von Objekten mit der SQL Server-Datenbank an. Weitere Informationen finden Sie unter [Aktualisieren von Datenbanken &#40;mysqltosql&#41;](../../ssma/mysql/refresh-from-database-mysqltosql.md)  
  
Sie können auf zwei verschiedene Synchronisierungs Seiten zugreifen, die die gleichen Einstellungen enthalten:  
  
-   Wenn Sie Einstellungen für alle zukünftigen SSMA-Projekte angeben möchten, klicken Sie **im Menü Extras** auf **defaultproject Settings**, und klicken Sie dann unten im linken Bereich auf **Synchronisieren** .  
  
-   Um Einstellungen für das aktuelle Projekt anzugeben, klicken Sie **im Menü Extras** auf **Projekteinstellungen**, und klicken Sie dann unten im linken Bereich auf **Synchronisierung** .  
  
## <a name="options"></a>Tastatur  
  
##### <a name="misc"></a>Sonstiges  
  
##### <a name="attempts"></a>Versuche  
Gibt Aufschluss über die Anzahl der Pass-Objekte, die in SQL Server geladen werden. Das Laden von Objekten in SQL Server erfolgt in der Regel in mehreren Durchläufen. Objekte, die im ersten Durchlauf nicht geladen werden können, z. b. Fremdschlüssel, können im nächsten Durchlauf erfolgreich geladen werden.  
  
Der Standardwert ist 2.  
  
## <a name="synchronization-for-mysql"></a>Synchronisierung für MySQL  
  
##### <a name="action-on-local-and-remote-object-change"></a>Aktion bei lokaler und Remote Objekt Änderung  
Gibt die Standardeinstellung im Dialogfeld "Synchronisierung" an, wenn die Objektdefinition in SSMA und auf dem Datenbankserver geändert wird.  
  
-   Wenn Sie aus Datenbank aktualisieren auswählen, lädt SSMA Daten Bank Definitionen in die Metadaten, wenn die Bedingung erfüllt ist.  
  
-   Wenn Sie Skip auswählen, führt SSMA keine Aktualisierungs Aktionen aus.  
  
##### <a name="action-on-local-object-change"></a>Aktion bei lokaler Objekt Änderung  
Gibt die Standardeinstellung im Dialogfeld "Synchronisierung" an, wenn das Objekt in SSMA geändert wird.  
  
-   Wenn Sie **aus Datenbank aktualisieren**auswählen, lädt SSMA Daten Bank Definitionen in die Metadaten, wenn die Bedingung erfüllt ist.  
  
-   Wenn Sie **Skip**auswählen, führt SSMA keine Aktualisierungs Aktionen aus.  
  
##### <a name="action-on-remote-object-change"></a>Aktion bei Remote Objekt Änderung  
Gibt die Standardeinstellung im Dialogfeld "Synchronisierung" an, wenn sich die Objekte auf dem Datenbankserver ändern.  
  
-   Wenn Sie **aus Datenbank aktualisieren**auswählen, lädt SSMA Daten Bank Definitionen in die Metadaten, wenn die Bedingung erfüllt ist.  
  
-   Wenn Sie **Skip**auswählen, führt SSMA keine Aktualisierungs Aktionen aus.  
  
##### <a name="action-when-local-object-metadata-is-missing"></a>Aktion, wenn lokale Objekt Metadaten fehlen  
Gibt die Standardeinstellung im Dialogfeld "Synchronisierung" an, wenn die lokalen Metadaten fehlen.  
  
-   Wenn Sie **aus Datenbank aktualisieren**auswählen, lädt SSMA Daten Bank Definitionen in die Metadaten, wenn die Bedingung erfüllt ist.  
  
-   Wenn Sie **Skip**auswählen, führt SSMA keine Aktualisierungs Aktionen aus.  
  
## <a name="synchronization-for-sql-server"></a>Synchronisierung für SQL Server  
  
##### <a name="action-on-local-and-remote-object-change"></a>Aktion bei lokaler und Remote Objekt Änderung  
Gibt die Standardeinstellung im Dialogfeld "Synchronisierung" an, wenn die Objektdefinition in SSMA und auf dem Datenbankserver geändert wird.  
  
-   Wenn Sie **aus Datenbank aktualisieren**auswählen, lädt SSMA Daten Bank Definitionen in die Metadaten, wenn die Bedingung erfüllt ist.  
  
-   Wenn Sie in **Datenbank schreiben**auswählen, werden die Objekte in der Datenbank von SSMA gemäß dem Inhalt der SSMA-Metadaten aktualisiert, wenn die Bedingung erfüllt ist.  
  
-   Wenn Sie **Skip**auswählen, führt SSMA keine Aktualisierungs Aktionen aus.  
  
##### <a name="action-on-local-object-change"></a>Aktion bei lokaler Objekt Änderung  
Gibt die Standardeinstellung im Dialogfeld "Synchronisierung" an, wenn das Objekt in SSMA geändert wird.  
  
-   Wenn Sie **aus Datenbank aktualisieren**auswählen, lädt SSMA Daten Bank Definitionen in die Metadaten, wenn die Bedingung erfüllt ist.  
  
-   Wenn Sie in **Datenbank schreiben**auswählen, wird das Objekt in der Datenbank von SSMA gemäß dem Inhalt der SSMA-Metadaten aktualisiert, wenn die Bedingung erfüllt ist.  
  
-   Wenn Sie **Skip**auswählen, führt SSMA keine Aktualisierungs Aktionen aus.  
  
##### <a name="action-on-remote-object-change"></a>Aktion bei Remote Objekt Änderung  
Gibt die Standardeinstellung im Dialogfeld "Synchronisierung" an, wenn sich die Objekte auf dem Datenbankserver ändern.  
  
-   Wenn Sie **aus Datenbank aktualisieren**auswählen, lädt SSMA Daten Bank Definitionen in die Metadaten, wenn die Bedingung erfüllt ist.  
  
-   Wenn Sie in **Datenbank schreiben**auswählen, wird das Objekt in der Datenbank von SSMA gemäß dem Inhalt der SSMA-Metadaten aktualisiert, wenn die Bedingung erfüllt ist.  
  
-   Wenn Sie **Skip**auswählen, führt SSMA keine Aktualisierungs Aktionen aus.  
  
##### <a name="action-when-local-object-metadata-is-missing"></a>Aktion, wenn lokale Objekt Metadaten fehlen  
Gibt die Standardeinstellung im Dialogfeld "Synchronisierung" an, wenn lokale Metadaten fehlen.  
  
-   Wenn Sie **aus Datenbank aktualisieren**auswählen, wählt SSMA die Option aus Datenbank aktualisieren aus, wenn die Bedingung erfüllt ist.  
  
-   Wenn Sie **in Datenbank schreiben**auswählen, wird das Objekt von SSMA aus der Datenbank gelöscht, wenn die Bedingung erfüllt ist.  
  
-   Wenn Sie **Skip**auswählen, führt SSMA keine Aktualisierungs Aktionen aus.  
  
