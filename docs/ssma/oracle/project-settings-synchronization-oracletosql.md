---
title: Project Settings(Synchronization) (OracleToSQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: e223fb7d-05ec-4fa5-8973-d845c33a23dd
author: Shamikg
ms.author: Shamikg
manager: shamikg
ms.openlocfilehash: 743ed010107c9557c84b1683f7a81b369ca7cf3c
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/16/2019
ms.locfileid: "68266589"
---
# <a name="project-settingssynchronization-oracletosql"></a>Projekteinstellungen (Synchronisierung) (OracleToSQL)
Auf der Seite von der **Projekteinstellungen** Dialogfeld enthält Einstellungen, die anpassen, wie SSMA geladen und aktualisiert die Datenbank Objekte, z. B. Tabellen und gespeicherten Prozeduren in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
Die Aktionen Standardoptionen geben Standardeinstellungen für die Aktualisierung von Objekten aus der Oracle-Datenbank und für die Synchronisierung von Objekten mit SQL Server-Datenbank. Weitere Informationen finden Sie unter [Aktualisieren von Oracle-Datenbank –](../../ssma/oracle/refresh-from-database-oracletosql.md).  
  
Sie können zwei verschiedene Synchronisierung Seiten zugreifen, die die gleichen Einstellungen enthalten:  
  
-   Die Einstellungen für alle zukünftigen SSMA-Projekten, auf die **Tools** im Menü klicken Sie auf **Projekt Standardeinstellungen**, und klicken Sie dann auf **Synchronisierung** am unteren Rand im linken Bereich.  
  
-   Die Einstellungen für das aktuelle Projekt, auf die **Tools** Menü klicken Sie auf **Projekteinstellungen**, und klicken Sie dann auf **Synchronisierung** am unteren Rand im linken Bereich.  
  
## <a name="miscellaneous-options"></a>Sonstige Optionen  
**Versuche**  
Gibt die Anzahl der Versuche SSMA sollten, beim Laden von Objekten in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Objekte, die in nicht geladen werden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in der aktuellen Versuch erneut versucht, bis SSMA die maximale Anzahl von versuchen in die aktuelle Synchronisierung erreicht. Ist der Standardwert festgelegt **2**  
  
## <a name="synchronization-for-oracle-options"></a>Synchronisierung für Oracle-Optionen  
**Aktion bei objektänderung der lokalen und remote**  
Gibt die Standardeinstellung im Dialogfeld für die Synchronisierung an, wenn sich die Objektdefinition in SSMA und auf dem Datenbankserver ändert. Ist der Standardwert festgelegt **Refresh from Database aktualisieren**.  
  
-   Bei Auswahl von **Refresh from Database aktualisieren**, SSMA werden Datenbankdefinitionen in die Metadaten geladen, wenn die Bedingung erfüllt ist.  
  
-   Bei Auswahl von **überspringen**, SSMA wird keine Aktualisierung Aktionen ausführen.  
  
**Aktion bei Änderung des lokalen Objekts**  
Gibt die Standardeinstellung im Dialogfeld für die Synchronisierung an, wenn sich das Objekt in SSMA ändern. Ist der Standardwert festgelegt **überspringen**.  
  
-   Bei Auswahl von **Refresh from Database aktualisieren**, SSMA werden Datenbankdefinitionen in die Metadaten geladen, wenn die Bedingung erfüllt ist.  
  
-   Bei Auswahl von **überspringen**, SSMA wird keine Aktualisierung Aktionen ausführen.  
  
**Aktion bei Änderung des remote-Objekt**  
Gibt die Standardeinstellung im Dialogfeld "Synchronisierung", wenn die Objekte auf dem Datenbankserver ändern. Ist der Standardwert festgelegt **Refresh from Database aktualisieren**.  
  
-   Bei Auswahl von **Refresh from Database aktualisieren**, SSMA werden Datenbankdefinitionen in die Metadaten geladen, wenn die Bedingung erfüllt ist.  
  
-   Bei Auswahl von **überspringen**, SSMA wird keine Aktualisierung Aktionen ausführen.  
  
**Aktion beim lokalen Metadaten nicht vorhanden ist.**  
Gibt die Standardeinstellung im Dialogfeld für die Synchronisierung, bei der lokalen Metadaten nicht vorhanden ist. Ist der Standardwert festgelegt **Refresh from Database aktualisieren**.  
  
-   Bei Auswahl von **Refresh from Database aktualisieren**, SSMA werden Datenbankdefinitionen in die Metadaten geladen, wenn die Bedingung erfüllt ist.  
  
-   Bei Auswahl von **überspringen**, SSMA wird keine Aktualisierung Aktionen ausführen.  
  
## <a name="synchronization-for-sql-server-options"></a>Synchronisierung für SQL Server-Optionen  
**Aktion bei objektänderung der lokalen und remote**  
Gibt die Standardeinstellung im Dialogfeld für die Synchronisierung an, wenn sich die Objektdefinition in SSMA und auf dem Datenbankserver ändert. Ist der Standardwert festgelegt **in Datenbank schreiben**.  
  
-   Bei Auswahl von **Refresh from Database aktualisieren**, SSMA werden Datenbankdefinitionen in die Metadaten geladen, wenn die Bedingung erfüllt ist.  
  
-   Bei Auswahl von **in Datenbank schreiben**, SSMA werden Objekte in der Datenbank gemäß den Inhalt der SSMA-Metadaten aktualisiert, wenn die Bedingung erfüllt ist.  
  
-   Bei Auswahl von **überspringen**, SSMA wird keine Aktualisierung Aktionen ausführen.  
  
**Aktion bei Änderung des lokalen Objekts**  
Gibt die Standardeinstellung im Dialogfeld für die Synchronisierung an, wenn sich das Objekt in SSMA ändern. Ist der Standardwert festgelegt **in Datenbank schreiben**.  
  
-   Bei Auswahl von **Refresh from Database aktualisieren**, SSMA werden Datenbankdefinitionen in die Metadaten geladen, wenn die Bedingung erfüllt ist.  
  
-   Bei Auswahl von **in Datenbank schreiben**, SSMA wird das Objekt in der Datenbank gemäß den Inhalt der SSMA-Metadaten aktualisiert, wenn die Bedingung erfüllt ist.  
  
-   Bei Auswahl von **überspringen**, SSMA wird keine Aktualisierung Aktionen ausführen.  
  
**Aktion bei Änderung des remote-Objekt**  
Gibt die Standardeinstellung im Dialogfeld "Synchronisierung", wenn die Objekte auf dem Datenbankserver ändern.  Ist der Standardwert festgelegt **Refresh from Database aktualisieren**.  
  
-   Bei Auswahl von **Refresh from Database aktualisieren**, SSMA werden Datenbankdefinitionen in die Metadaten geladen, wenn die Bedingung erfüllt ist.  
  
-   Bei Auswahl von **in Datenbank schreiben**, SSMA wird das Objekt in der Datenbank gemäß den Inhalt der SSMA-Metadaten aktualisiert, wenn die Bedingung erfüllt ist.  
  
-   Bei Auswahl von **überspringen**, SSMA wird keine Aktualisierung Aktionen ausführen.  
  
**Aktion beim lokalen Metadaten nicht vorhanden ist.**  
Gibt die Standardeinstellung im Dialogfeld für die Synchronisierung, bei der lokalen Metadaten nicht vorhanden ist. Ist der Standardwert festgelegt **Refresh from Database aktualisieren**.  
  
-   Bei Auswahl von **Refresh from Database aktualisieren**, SSMA wählt die **Refresh from Database aktualisieren** option, wenn die Bedingung erfüllt ist.  
  
-   Bei Auswahl von **in Datenbank schreiben**, SSMA wird das Objekt aus der Datenbank löschen, wenn die Bedingung erfüllt ist.  
  
-   Bei Auswahl von **überspringen**, SSMA wird keine Aktualisierung Aktionen ausführen.  
  
