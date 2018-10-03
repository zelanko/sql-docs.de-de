---
title: Project Settings (Loading Objects) (AccessToSQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 9ec1c1e8-a3e1-4e81-bf49-631f87daa209
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 90a47a7586d0f3c6b5bd0fee28ed01f3b292a92e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47803628"
---
# <a name="project-settings-loading-objects-accesstosql"></a>Project Settings (Loading Objects) (AccessToSQL)
Die projekteinstellungen Laden von Objekten können Sie konfigurieren, wie den Zugriff auf Datenbankobjekte mit SQL Server-Datenbankobjekte synchronisiert werden.  
  
Die Standardaktionen geben Standardeinstellungen für die Aktualisierung von Objekten aus der Access-Datenbank und für die Synchronisierung von Objekten mit SQL Server-Datenbank. Weitere Informationen finden Sie unter [Refresh from Database aktualisieren &#40;AccessToSQL&#41;](../../ssma/access/refresh-from-database-accesstosql.md)  
  
Sie können zwei verschiedene Synchronisierung Seiten zugreifen, die die gleichen Einstellungen enthalten:  
  
-   Die Einstellungen für alle zukünftigen SSMA-Projekten, auf die **Tools** im Menü klicken Sie auf **DefaultProject Einstellungen**, und klicken Sie dann auf **Objekte laden** am unteren Rand im linken Bereich.  
  
-   Die Einstellungen für das aktuelle Projekt, auf die **Tools** im Menü klicken Sie auf **Projekteinstellungen**, und klicken Sie dann auf **Objekte laden** am unteren Rand im linken Bereich.  
  
## <a name="options"></a>Tastatur  
  
##### <a name="misc"></a>Sonstiges  
  
##### <a name="attempts"></a>Versuche  
Enthält die Informationen über die Anzahl von Durchläufen Objekte zum Laden in SQL Server in Anspruch nehmen. Laden von Objekten in SQL Server erfolgt in der Regel in mehreren Durchläufen. Objekte, die Fehler beim Laden der im ersten Schritt, wie foreign key, möglicherweise im nächsten Schritt erfolgreich geladen.  
  
Standardmäßig ist der Wert 2.  
  
## <a name="synchronization-for-sql-server"></a>Synchronisierung für SQLServer  
  
##### <a name="default-action-on-local-and-remote-object-change"></a>Standardaktion für lokale und Remote ändern  
Gibt die Standardeinstellung im Dialogfeld für die Synchronisierung an, wenn sich die Objektdefinition in SSMA und auf dem Datenbankserver ändert.  
  
-   Bei Auswahl von **Refresh from Database aktualisieren**, SSMA werden Datenbankdefinitionen in die Metadaten geladen, wenn die Bedingung erfüllt ist.  
  
-   Bei Auswahl von **in Datenbank schreiben**, SSMA werden Objekte in der Datenbank gemäß den Inhalt der SSMA-Metadaten aktualisiert, wenn die Bedingung erfüllt ist.  
  
-   Bei Auswahl von **überspringen**, SSMA wird keine Aktualisierung Aktionen ausführen.  
  
##### <a name="default-action-on-local-object-change"></a>Default-Aktion bei Änderung des lokalen Objekts  
Gibt die Standardeinstellung im Dialogfeld für die Synchronisierung an, wenn sich das Objekt in SSMA ändern.  
  
-   Bei Auswahl von **Refresh from Database aktualisieren**, SSMA werden Datenbankdefinitionen in die Metadaten geladen, wenn die Bedingung erfüllt ist.  
  
-   Bei Auswahl von **in Datenbank schreiben**, SSMA wird das Objekt in der Datenbank gemäß den Inhalt der SSMA-Metadaten aktualisiert, wenn die Bedingung erfüllt ist.  
  
-   Bei Auswahl von **überspringen**, SSMA wird keine Aktualisierung Aktionen ausführen.  
  
##### <a name="default-action-on-remote-object-change"></a>Default-Aktion bei Änderung des remote-Objekt  
Gibt die Standardeinstellung im Dialogfeld "Synchronisierung", wenn die Objekte auf dem Datenbankserver ändern.  
  
-   Bei Auswahl von **Refresh from Database aktualisieren**, SSMA werden Datenbankdefinitionen in die Metadaten geladen, wenn die Bedingung erfüllt ist.  
  
-   Bei Auswahl von **in Datenbank schreiben**, SSMA wird das Objekt in der Datenbank gemäß den Inhalt der SSMA-Metadaten aktualisiert, wenn die Bedingung erfüllt ist.  
  
-   Bei Auswahl von **überspringen**, SSMA wird keine Aktualisierung Aktionen ausführen.  
  
##### <a name="default-action-when-local-object-metadata-is-missing"></a>Standardaktion beim lokalen Metadaten nicht vorhanden ist.  
Gibt die Standardeinstellung im Dialogfeld für die Synchronisierung, bei der lokalen Metadaten nicht vorhanden ist.  
  
-   Bei Auswahl von **Refresh from Database aktualisieren**, SSMA wählt die Aktualisierung über die Option "Datenbank" aus, wenn die Bedingung erfüllt ist.  
  
-   Bei Auswahl von **in Datenbank schreiben**, SSMA wird das Objekt aus der Datenbank löschen, wenn die Bedingung erfüllt ist.  
  
-   Bei Auswahl von **überspringen**, SSMA wird keine Aktualisierung Aktionen ausführen.  
  
