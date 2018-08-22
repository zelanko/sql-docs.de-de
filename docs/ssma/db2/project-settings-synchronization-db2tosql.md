---
title: Project Settings(Synchronization) (DB2ToSQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: a5629a72-8c17-46a4-bb4d-19d51a0b98a2
caps.latest.revision: 4
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 0fe2dbcb60b4d01ed015c4ab272b17cc1e7a0252
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/14/2018
ms.locfileid: "40393637"
---
# <a name="project-settingssynchronization-db2tosql"></a>Project Settings(Synchronization) (DB2ToSQL)
Auf der Seite von der **Projekteinstellungen** Dialogfeld enthält Einstellungen, die anpassen, wie SSMA geladen und aktualisiert die Datenbank Objekte, z. B. Tabellen und gespeicherten Prozeduren in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
Die Aktionen Standardoptionen geben Standardeinstellungen für die Aktualisierung von Objekten aus der DB2-Datenbank und für die Synchronisierung von Objekten mit SQL Server-Datenbank. Weitere Informationen finden Sie unter [Refresh from Database aktualisieren &#40;DB2ToSQL&#41;](../../ssma/db2/refresh-from-database-db2tosql.md).  
  
Sie können zwei verschiedene Synchronisierung Seiten zugreifen, die die gleichen Einstellungen enthalten:  
  
-   Die Einstellungen für alle zukünftigen SSMA-Projekten, auf die **Tools** im Menü klicken Sie auf **Projekt Standardeinstellungen**, und klicken Sie dann auf **Synchronisierung** am unteren Rand im linken Bereich.  
  
-   Die Einstellungen für das aktuelle Projekt, auf die **Tools** Menü klicken Sie auf **Projekteinstellungen**, und klicken Sie dann auf **Synchronisierung** am unteren Rand im linken Bereich.  
  
## <a name="miscellaneous-options"></a>Sonstige Optionen  
**Versuche**  
Gibt die Anzahl der Versuche SSMA sollten, beim Laden von Objekten in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Objekte, die in nicht geladen werden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in der aktuellen Versuch erneut versucht, bis SSMA die maximale Anzahl von versuchen in die aktuelle Synchronisierung erreicht. Ist der Standardwert festgelegt **2**  
  
## <a name="synchronization-for-db2-options"></a>Synchronisierung für DB2-Optionen  
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
  
-   Bei Auswahl von **Refresh from Database aktualisieren**, SSMA SSMA werden Datenbankdefinitionen in die Metadaten geladen, wenn die Bedingung erfüllt ist.  
  
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
  
