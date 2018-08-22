---
title: Projekteinstellungen (Synchronisierung) (SybaseToSQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 2cd6bc01-b8e5-4312-83a4-eac66dc1d460
caps.latest.revision: 3
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: fcdcfc8d113bca42a9f042e8e6196d3de55b8e7e
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/14/2018
ms.locfileid: "40393177"
---
# <a name="project-settings-synchronization-sybasetosql"></a>Projekteinstellungen (Synchronisierung) (SybaseToSQL)
Auf der Seite von der **Projekteinstellungen** Dialogfeld enthält Einstellungen, die anpassen, wie der SSMA-Datenbankobjekte wie Tabellen und gespeicherten Prozeduren in lädt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure.  
  
Sie können zwei verschiedene Synchronisierung Seiten zugreifen, die die gleichen Einstellungen enthalten:  
  
-   Wenn Sie möchten die Einstellungen für alle zukünftigen SSMA-Projekten, auf die **Tools** , wählen Sie im Menü **Projekt Standardeinstellungen**, wählen Sie die Migration-Projekttyp, die für die Einstellungen sind erforderlich, angezeigt oder geändert werden von **Migration Zielversion** Dropdownliste aus, und wählen Sie dann **Synchronisierung** am unteren Rand im linken Bereich.  
  
-   Die Einstellungen für das aktuelle Projekt, auf die **Tools** , wählen Sie im Menü **Projekteinstellungen**, und wählen Sie dann **Synchronisierung** am unteren Rand im linken Bereich.  
  
## <a name="options"></a>Tastatur  
**Versuche**  
Gibt die Anzahl der Versuche SSMA sollten, beim Laden von Objekten in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Objekte, die in nicht geladen werden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in der aktuellen Versuch erneut versucht, bis SSMA die maximale Anzahl von versuchen in die aktuelle Synchronisierung erreicht.  
  
## <a name="synchronization-for-sql-server"></a>Synchronisierung für SQLServer  
**Aktualisieren von lokalen objektänderung, die lokal und remote-Objekt**  
Gibt an, ob es sich bei SSMA der lokalen Metadaten mit den Metadaten des Remoteobjekts ersetzen soll, falls die lokale und remote-Objekte ändern.  
Bei Auswahl von **Refresh from Database aktualisieren**, SSMA werden Datenbankdefinitionen in die Metadaten geladen, wenn die Bedingung erfüllt ist.  
Bei Auswahl von **in Datenbank schreiben**, SSMA werden Objekte in der Datenbank gemäß den Inhalt der SSMA-Metadaten aktualisiert, wenn die Bedingung erfüllt ist.  
Bei Auswahl von **überspringen**, SSMA wird keine Aktualisierung Aktionen ausführen.   
Ist der Standardsatz der Option **in Datenbank schreiben.**  
  
**Lokales Objekt bei Änderung des lokalen Objekts aktualisieren**  
Gibt an, ob es sich bei SSMA der lokalen Metadaten mit den Metadaten des Remoteobjekts ersetzen soll, falls das Remoteobjekt ändert.  
Bei Auswahl von **Refresh from Database aktualisieren**, SSMA werden Datenbankdefinitionen in die Metadaten geladen, wenn die Bedingung erfüllt ist.  
Bei Auswahl von **in Datenbank schreiben**, SSMA wird das Objekt in der Datenbank gemäß den Inhalt der SSMA-Metadaten aktualisiert, wenn die Bedingung erfüllt ist.  
Bei Auswahl von **überspringen**, SSMA wird keine Aktualisierung Aktionen ausführen.   
Ist der Standardsatz der Option **in Datenbank schreiben**.  
  
**Aktualisieren Sie Lokales Objekt bei Änderung des Remote-Objekt**  
Gibt an, ob es sich bei SSMA der lokalen Metadaten mit den Metadaten des Remoteobjekts ersetzen soll, falls das Remoteobjekt ändert.  
Bei Auswahl von **Refresh from Database aktualisieren**, SSMA werden Datenbankdefinitionen in die Metadaten geladen, wenn die Bedingung erfüllt ist.  
Bei Auswahl von **in Datenbank schreiben**, SSMA wird das Objekt in der Datenbank gemäß den Inhalt der SSMA-Metadaten aktualisiert, wenn die Bedingung erfüllt ist.  
Bei Auswahl von **überspringen**, SSMA wird keine Aktualisierung Aktionen ausführen.   
Ist der Standardsatz der Option **Refresh from Database aktualisieren**.  
  
**Aktualisieren Sie bei der lokalen Metadaten nicht vorhanden ist**  
Gibt an, ob SSMA lokalen Metadaten erstellen soll, wenn ein Objekt in der Zieldatenbank, aber nicht lokal vorhanden ist.  
Bei Auswahl von **Refresh from Database aktualisieren**, SSMA wählt die Aktualisierung über die Option "Datenbank" aus, wenn die Bedingung erfüllt ist.  
Bei Auswahl von **in Datenbank schreiben**, SSMA wird das Objekt aus der Datenbank löschen, wenn die Bedingung erfüllt ist.  
Bei Auswahl von **überspringen**, SSMA wird keine Aktualisierung Aktionen ausführen.   
Ist der Standardsatz der Option **Refresh from Database aktualisieren**.  
  
