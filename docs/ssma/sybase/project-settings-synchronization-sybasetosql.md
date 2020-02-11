---
title: Projekteinstellungen (Synchronisierung) (sybasedesql) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 2cd6bc01-b8e5-4312-83a4-eac66dc1d460
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 663a4b1e49d1f81ce040254a2c8f39a1a1f84b38
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68028686"
---
# <a name="project-settings-synchronization-sybasetosql"></a>Projekteinstellungen (Synchronisierung) (SybaseToSQL)
Die Seite Synchronisierung des Dialog Felds **Projekteinstellungen** enthält Einstellungen, die anpassen, wie SSMA Datenbankobjekte, z. b. Tabellen und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gespeicherte Prozeduren, in oder SQL Azure lädt.  
  
Sie können auf zwei verschiedene Synchronisierungs Seiten zugreifen, die die gleichen Einstellungen enthalten:  
  
-   Wenn Sie Einstellungen für alle zukünftigen SSMA-Projekte angeben möchten, wählen Sie **im Menü Extras** die Option **Standard Projekteinstellungen**aus, wählen Sie den Migrations Projekttyp aus, für den die Einstellungen in der Dropdown Liste **Migrations Ziel Version** angezeigt oder geändert werden müssen, und wählen Sie dann unten im linken Bereich die Option **Synchronisierung** aus.  
  
-   Um Einstellungen für das aktuelle Projekt anzugeben, wählen Sie **im Menü Extras** die Option **Projekteinstellungen**aus, und wählen Sie dann unten im linken Bereich die Option **Synchronisierung** aus.  
  
## <a name="options"></a>Tastatur  
**Unternommen**  
Gibt die Anzahl der Versuche an, die SSMA beim Laden von Objekten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]in durchführen soll. Objekte, die im aktuellen Versuch [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nicht in geladen werden, werden wiederholt, bis SSMA die maximale Anzahl von versuchen im aktuellen Synchronisierungs Vorgang erreicht.  
  
## <a name="synchronization-for-sql-server"></a>Synchronisierung für SQL Server  
**Lokales Objekt bei lokaler und Remote Objekt Änderung aktualisieren**  
Gibt an, ob SSMA die Metadaten des lokalen Objekts durch Remote Objekt Metadaten ersetzen soll, wenn sich sowohl das lokale als auch das Remote Objekt ändern.  
Wenn Sie **aus Datenbank aktualisieren**auswählen, lädt SSMA Daten Bank Definitionen in die Metadaten, wenn die Bedingung erfüllt ist.  
Wenn Sie in **Datenbank schreiben**auswählen, werden die Objekte in der Datenbank von SSMA gemäß dem Inhalt der SSMA-Metadaten aktualisiert, wenn die Bedingung erfüllt ist.  
Wenn Sie **Skip**auswählen, führt SSMA keine Aktualisierungs Aktionen aus.   
Der Standard Options Satz ist " **in Datenbank schreiben".**  
  
**Lokales Objekt bei Änderung des lokalen Objekts aktualisieren**  
Gibt an, ob SSMA die Metadaten des lokalen Objekts durch Remote Objekt Metadaten ersetzen soll, wenn sich das Remote Objekt ändert.  
Wenn Sie **aus Datenbank aktualisieren**auswählen, lädt SSMA Daten Bank Definitionen in die Metadaten, wenn die Bedingung erfüllt ist.  
Wenn Sie in **Datenbank schreiben**auswählen, wird das Objekt in der Datenbank von SSMA gemäß dem Inhalt der SSMA-Metadaten aktualisiert, wenn die Bedingung erfüllt ist.  
Wenn Sie **Skip**auswählen, führt SSMA keine Aktualisierungs Aktionen aus.   
Der Standard Options Satz ist " **in Datenbank schreiben**".  
  
**Lokales Objekt bei Remote Objekt Änderung aktualisieren**  
Gibt an, ob SSMA die Metadaten des lokalen Objekts durch Remote Objekt Metadaten ersetzen soll, wenn sich das Remote Objekt ändert.  
Wenn Sie **aus Datenbank aktualisieren**auswählen, lädt SSMA Daten Bank Definitionen in die Metadaten, wenn die Bedingung erfüllt ist.  
Wenn Sie in **Datenbank schreiben**auswählen, wird das Objekt in der Datenbank von SSMA gemäß dem Inhalt der SSMA-Metadaten aktualisiert, wenn die Bedingung erfüllt ist.  
Wenn Sie **Skip**auswählen, führt SSMA keine Aktualisierungs Aktionen aus.   
Der Standard Options Satz ist **Aktualisieren von der Datenbank**.  
  
**Aktualisieren, wenn Metadaten des lokalen Objekts fehlen**  
Gibt an, ob SSMA lokale Metadaten erstellen soll, wenn ein Objekt in der Zieldatenbank vorhanden ist, jedoch nicht lokal.  
Wenn Sie **aus Datenbank aktualisieren**auswählen, wählt SSMA die Option aus Datenbank aktualisieren aus, wenn die Bedingung erfüllt ist.  
Wenn Sie **in Datenbank schreiben**auswählen, wird das Objekt von SSMA aus der Datenbank gelöscht, wenn die Bedingung erfüllt ist.  
Wenn Sie **Skip**auswählen, führt SSMA keine Aktualisierungs Aktionen aus.   
Der Standard Options Satz ist **Aktualisieren von der Datenbank**.  
  
