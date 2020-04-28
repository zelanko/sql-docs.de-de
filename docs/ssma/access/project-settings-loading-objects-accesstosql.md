---
title: Projekteinstellungen (Objekte werden geladen) (accesstosql) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 9ec1c1e8-a3e1-4e81-bf49-631f87daa209
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: c8aebc643d3d313dcf97bbe69044ee795649ba46
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "67929425"
---
# <a name="project-settings-loading-objects-accesstosql"></a>Projekteinstellungen (Objekte werden geladen) (accesstosql)
Mit den Projekteinstellungen zum Laden von Objekten können Sie konfigurieren, wie Access-Datenbankobjekte mit SQL Server-Datenbankobjekten synchronisiert werden.  
  
Mit den Standard Aktionen werden die Standardeinstellungen zum Aktualisieren von Objekten aus der Access-Datenbank und zum Synchronisieren von Objekten mit der SQL Server Datenbank angegeben. Weitere Informationen finden Sie unter [Aktualisieren aus der Datenbank &#40;Access Token&#41;](../../ssma/access/refresh-from-database-accesstosql.md)  
  
Sie können auf zwei verschiedene Synchronisierungs Seiten zugreifen, die die gleichen Einstellungen enthalten:  
  
-   Wenn Sie Einstellungen für alle zukünftigen SSMA-Projekte angeben möchten, klicken Sie **im Menü Extras** auf **defaultproject Settings**, und klicken Sie dann unten im linken Bereich auf **Objekte laden** .  
  
-   Um Einstellungen für das aktuelle Projekt anzugeben, klicken Sie **im Menü Extras** auf **Projekteinstellungen**, und klicken Sie dann unten im linken Bereich auf **Objekte laden** .  
  
## <a name="options"></a>Optionen  
  
##### <a name="misc"></a>Sonstiges  
  
##### <a name="attempts"></a>Versuche  
Gibt Aufschluss über die Anzahl der Pass-Objekte, die in SQL Server geladen werden. Das Laden von Objekten in SQL Server erfolgt in der Regel in mehreren Durchläufen. Objekte, die im ersten Durchlauf nicht geladen werden können, z. b. Fremdschlüssel, können im nächsten Durchlauf erfolgreich geladen werden.  
  
Der Standardwert ist 2.  
  
## <a name="synchronization-for-sql-server"></a>Synchronisierung für SQL Server  
  
##### <a name="default-action-on-local-and-remote-object-change"></a>Standardaktion für lokale und Remote Objekt Änderung  
Gibt die Standardeinstellung im Dialogfeld "Synchronisierung" an, wenn die Objektdefinition in SSMA und auf dem Datenbankserver geändert wird.  
  
-   Wenn Sie **aus Datenbank aktualisieren**auswählen, lädt SSMA Daten Bank Definitionen in die Metadaten, wenn die Bedingung erfüllt ist.  
  
-   Wenn Sie in **Datenbank schreiben**auswählen, werden die Objekte in der Datenbank von SSMA gemäß dem Inhalt der SSMA-Metadaten aktualisiert, wenn die Bedingung erfüllt ist.  
  
-   Wenn Sie **Skip**auswählen, führt SSMA keine Aktualisierungs Aktionen aus.  
  
##### <a name="default-action-on-local-object-change"></a>Standardaktion für lokale Objekt Änderung  
Gibt die Standardeinstellung im Dialogfeld "Synchronisierung" an, wenn das Objekt in SSMA geändert wird.  
  
-   Wenn Sie **aus Datenbank aktualisieren**auswählen, lädt SSMA Daten Bank Definitionen in die Metadaten, wenn die Bedingung erfüllt ist.  
  
-   Wenn Sie in **Datenbank schreiben**auswählen, wird das Objekt in der Datenbank von SSMA gemäß dem Inhalt der SSMA-Metadaten aktualisiert, wenn die Bedingung erfüllt ist.  
  
-   Wenn Sie **Skip**auswählen, führt SSMA keine Aktualisierungs Aktionen aus.  
  
##### <a name="default-action-on-remote-object-change"></a>Standardaktion für Remote Objekt Änderung  
Gibt die Standardeinstellung im Dialogfeld "Synchronisierung" an, wenn sich die Objekte auf dem Datenbankserver ändern.  
  
-   Wenn Sie **aus Datenbank aktualisieren**auswählen, lädt SSMA Daten Bank Definitionen in die Metadaten, wenn die Bedingung erfüllt ist.  
  
-   Wenn Sie in **Datenbank schreiben**auswählen, wird das Objekt in der Datenbank von SSMA gemäß dem Inhalt der SSMA-Metadaten aktualisiert, wenn die Bedingung erfüllt ist.  
  
-   Wenn Sie **Skip**auswählen, führt SSMA keine Aktualisierungs Aktionen aus.  
  
##### <a name="default-action-when-local-object-metadata-is-missing"></a>Standardaktion, wenn Metadaten des lokalen Objekts fehlen  
Gibt die Standardeinstellung im Dialogfeld "Synchronisierung" an, wenn lokale Metadaten fehlen.  
  
-   Wenn Sie **aus Datenbank aktualisieren**auswählen, wählt SSMA die Option aus Datenbank aktualisieren aus, wenn die Bedingung erfüllt ist.  
  
-   Wenn Sie **in Datenbank schreiben**auswählen, wird das Objekt von SSMA aus der Datenbank gelöscht, wenn die Bedingung erfüllt ist.  
  
-   Wenn Sie **Skip**auswählen, führt SSMA keine Aktualisierungs Aktionen aus.  
  
