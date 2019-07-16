---
title: Projekteinstellungen (Synchronisierung) (MySQLToSQL)) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 42061ff7-e6e7-497b-a0d9-440b9cf5986c
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: c4437f76a926e84ffe3592042f9d29b50f3eabf9
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67908839"
---
# <a name="project-settings-synchronization-mysqltosql"></a>Projekteinstellungen (Synchronisierung) (MySqlToSql)
Die Synchronisierung **projekteinstellungen** können Sie konfigurieren, wie Objekte von MySQL-Datenbank mit SQL Server-Datenbankobjekte synchronisiert werden.  
  
Die Standardaktionen geben Standardeinstellungen für die Aktualisierung von Objekten aus der MySQL-Datenbank und für die Synchronisierung von Objekten mit SQL Server-Datenbank. Weitere Informationen finden Sie unter [Refresh from Database aktualisieren &#40;MySQLToSQL&#41;](../../ssma/mysql/refresh-from-database-mysqltosql.md)  
  
Sie können zwei verschiedene Synchronisierung Seiten zugreifen, die die gleichen Einstellungen enthalten:  
  
-   Die Einstellungen für alle zukünftigen SSMA-Projekten, auf die **Tools** Menü klicken Sie auf **DefaultProject Einstellungen**, und klicken Sie dann auf **Synchronisierung** am unteren Rand im linken Bereich.  
  
-   Die Einstellungen für das aktuelle Projekt, auf die **Tools** Menü klicken Sie auf **Projekteinstellungen**, und klicken Sie dann auf **Synchronisierung** am unteren Rand im linken Bereich.  
  
## <a name="options"></a>Optionen  
  
##### <a name="misc"></a>Sonstiges  
  
##### <a name="attempts"></a>Versuche  
Enthält die Informationen über die Anzahl von Durchläufen Objekte zum Laden in SQL Server in Anspruch nehmen. Laden von Objekten in SQL Server erfolgt in der Regel in mehreren Durchläufen. Objekte, die Fehler beim Laden der im ersten Schritt, wie foreign key, möglicherweise im nächsten Schritt erfolgreich geladen.  
  
Standardmäßig ist der Wert 2.  
  
## <a name="synchronization-for-mysql"></a>Synchronisierung für MySQL  
  
##### <a name="action-on-local-and-remote-object-change"></a>Aktion bei objektänderung der lokalen und remote  
Gibt die Standardeinstellung im Dialogfeld für die Synchronisierung an, wenn sich die Objektdefinition in SSMA und auf dem Datenbankserver ändert.  
  
-   Wenn Sie eine Aktualisierung aus Datenbank auswählen, wird von SSMA Datenbankdefinitionen in die Metadaten geladen, wenn die Bedingung erfüllt ist.  
  
-   Wenn Sie auf "Überspringen" auswählen, wird SSMA keine Aktualisierung Aktionen ausführen.  
  
##### <a name="action-on-local-object-change"></a>Aktion bei Änderung des lokalen Objekts  
Gibt die Standardeinstellung im Dialogfeld für die Synchronisierung an, wenn sich das Objekt in SSMA ändern.  
  
-   Bei Auswahl von **Refresh from Database aktualisieren**, SSMA werden Datenbankdefinitionen in die Metadaten geladen, wenn die Bedingung erfüllt ist.  
  
-   Bei Auswahl von **überspringen**, SSMA wird keine Aktualisierung Aktionen ausführen.  
  
##### <a name="action-on-remote-object-change"></a>Aktion bei Änderung des Remote-Objekt  
Gibt die Standardeinstellung im Dialogfeld "Synchronisierung", wenn die Objekte auf dem Datenbankserver ändern.  
  
-   Bei Auswahl von **Refresh from Database aktualisieren**, SSMA werden Datenbankdefinitionen in die Metadaten geladen, wenn die Bedingung erfüllt ist.  
  
-   Bei Auswahl von **überspringen**, SSMA wird keine Aktualisierung Aktionen ausführen.  
  
##### <a name="action-when-local-object-metadata-is-missing"></a>Aktion beim lokalen Metadaten nicht vorhanden ist.  
Gibt die Standardeinstellung im Dialogfeld für die Synchronisierung an, wenn die lokale Metadaten nicht vorhanden ist.  
  
-   Bei Auswahl von **Refresh from Database aktualisieren**, SSMA werden Datenbankdefinitionen in die Metadaten geladen, wenn die Bedingung erfüllt ist.  
  
-   Bei Auswahl von **überspringen**, SSMA wird keine Aktualisierung Aktionen ausführen  
  
## <a name="synchronization-for-sql-server"></a>Synchronisierung für SQLServer  
  
##### <a name="action-on-local-and-remote-object-change"></a>Aktion bei Änderung von lokal und Remote-Objekt  
Gibt die Standardeinstellung im Dialogfeld für die Synchronisierung an, wenn sich die Objektdefinition in SSMA und auf dem Datenbankserver ändert.  
  
-   Bei Auswahl von **Refresh from Database aktualisieren**, SSMA werden Datenbankdefinitionen in die Metadaten geladen, wenn die Bedingung erfüllt ist.  
  
-   Bei Auswahl von **in Datenbank schreiben**, SSMA werden Objekte in der Datenbank gemäß den Inhalt der SSMA-Metadaten aktualisiert, wenn die Bedingung erfüllt ist.  
  
-   Bei Auswahl von **überspringen**, SSMA wird keine Aktualisierung Aktionen ausführen.  
  
##### <a name="action-on-local-object-change"></a>Aktion bei Änderung des lokalen Objekts  
Gibt die Standardeinstellung im Dialogfeld für die Synchronisierung an, wenn sich das Objekt in SSMA ändern.  
  
-   Bei Auswahl von **Refresh from Database aktualisieren**, SSMA werden Datenbankdefinitionen in die Metadaten geladen, wenn die Bedingung erfüllt ist.  
  
-   Bei Auswahl von **in Datenbank schreiben**, SSMA wird das Objekt in der Datenbank gemäß den Inhalt der SSMA-Metadaten aktualisiert, wenn die Bedingung erfüllt ist.  
  
-   Bei Auswahl von **überspringen**, SSMA wird keine Aktualisierung Aktionen ausführen.  
  
##### <a name="action-on-remote-object-change"></a>Aktion bei Änderung des remote-Objekt  
Gibt die Standardeinstellung im Dialogfeld "Synchronisierung", wenn die Objekte auf dem Datenbankserver ändern.  
  
-   Bei Auswahl von **Refresh from Database aktualisieren**, SSMA werden Datenbankdefinitionen in die Metadaten geladen, wenn die Bedingung erfüllt ist.  
  
-   Bei Auswahl von **in Datenbank schreiben**, SSMA wird das Objekt in der Datenbank gemäß den Inhalt der SSMA-Metadaten aktualisiert, wenn die Bedingung erfüllt ist.  
  
-   Bei Auswahl von **überspringen**, SSMA wird keine Aktualisierung Aktionen ausführen.  
  
##### <a name="action-when-local-object-metadata-is-missing"></a>Aktion beim lokalen Metadaten nicht vorhanden ist.  
Gibt die Standardeinstellung im Dialogfeld für die Synchronisierung, bei der lokalen Metadaten nicht vorhanden ist.  
  
-   Bei Auswahl von **Refresh from Database aktualisieren**, SSMA wählt die Aktualisierung über die Option "Datenbank" aus, wenn die Bedingung erfüllt ist.  
  
-   Bei Auswahl von **in Datenbank schreiben**, SSMA wird das Objekt aus der Datenbank löschen, wenn die Bedingung erfüllt ist.  
  
-   Bei Auswahl von **überspringen**, SSMA wird keine Aktualisierung Aktionen ausführen.  
  
