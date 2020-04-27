---
title: MSSQLSERVER_208 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 208 (Database Engine error)
ms.assetid: 4b1895f5-3197-4da1-af86-954c93507956
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: b87a950c29cf202124e27b319eb56fb6a6e1857d
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62914915"
---
# <a name="mssqlserver_208"></a>MSSQLSERVER_208
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|208|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|SQ_BADOBJECT|  
|Meldungstext|Ungültiger Objektname '%.*ls'.|  
  
## <a name="explanation"></a>Erklärung  
 Das angegebene Objekt wurde nicht gefunden.  
  
### <a name="possible-causes"></a>Mögliche Ursachen  
 Dieser Fehler kann durch eines der folgenden Probleme verursacht werden:  
  
-   Das Objekt ist nicht richtig angegeben.  
  
-   Das Objekt ist in der aktuellen Datenbank oder der angegebenen Datenbank nicht vorhanden.  
  
-   Das Objekt ist vorhanden, es konnte jedoch nicht für den Benutzer verfügbar gemacht werden. Es ist z. B. möglich, dass der Benutzer keine Berechtigungen für das Objekt besitzt oder dass das Objekt in einer EXECUTE-Anweisung erstellt ist, aber von außerhalb des Gültigkeitsbereichs der EXECUTE-Anweisung darauf zugegriffen wird.  
  
## <a name="user-action"></a>Benutzeraktion  
 Überprüfen Sie die folgenden Informationen, und korrigieren Sie die Anweisung entsprechend.  
  
-   Der Objektname wurde richtig geschrieben.  
  
-   Der aktuelle Datenbankkontext ist richtig. Wenn kein Datnbankname für das Objekt angegeben ist, muss das Objekt in der aktuellen Datenbank vorhanden sein. Weitere Informationen zum Festlegen des Datenbankkontexts finden Sie unter [USE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/use-transact-sql).  
  
-   Das Objekt ist in den Systemtabellen vorhanden. Wenn Sie überprüfen möchten, ob eine Tabelle oder ein anderes schemabezogenes Objekt vorhanden ist, fragen Sie die **sys.objects**-Katalogsicht ab. Wenn das Objekt in den Systemtabellen nicht vorhanden ist, wurde das Objekt gelöscht, oder der Benutzer besitzt keine Berechtigungen zum Anzeigen der Objektmetadaten. Weitere Informationen zu Berechtigungen zum Anzeigen von Objektmetadaten finden Sie unter [Konfiguration der Sichtbarkeit von Metadaten](../security/metadata-visibility-configuration.md).  
  
-   Das Objekt ist im Standardschema des Benutzers enthalten. Andernfalls muss das Objekt im zweiteiligen Format *schema_name.object_name* angegeben werden. Beachten Sie, dass Skalarwertfunktionen immer mindestens mit dem zweiteiligen Namen aufgerufen werden müssen.  
  
-   Die Unterscheidung nach Groß-/Kleinschreibung der Datenbanksortierung.  
  
     Wenn eine Datenbank eine Sortierung verwendet, die nach Groß-/Kleinschreibung unterscheidet, muss der Objektname der Schreibung des Objekts in der Datenbank entsprechen. Wenn ein Objekt z.B. als **MyTable** in einer Datenbank mit Sortierung, die nach Groß-/Kleinschreibung unterscheidet, angegeben ist, geben Abfragen, die auf das Objekt als **mytable** oder **Mytable** verweisen, den Fehler 208 zurück, weil die Objektnamen nicht übereinstimmen.  
  
     Sie können die Datenbanksortierung überprüfen, indem Sie die folgende Anweisung ausführen.  
  
    ```  
    SELECT collation_name FROM sys.databases WHERE name = 'database_name';  
    ```  
  
     Die Abkürzung CS im Sortierungsnamen gibt an, dass bei der Sortierung nach Groß-/Kleinschreibung unterschieden wird. Beispiel: Latin1_General_CS_AS ist eine Sortierung, bei der nach Groß-/Kleinschreibung und nach Akzent unterschieden wird. CI gibt an, dass bei der Sortierung nicht nach Groß-/Kleinschreibung unterschieden wird.  
  
-   Der Benutzer besitzt die Berechtigung zum Zugreifen auf das Objekt. Mit der Systemfunktion **Has_Perms_By_Name** können Sie die Berechtigungen des Benutzers für das Objekt überprüfen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwenden Sie &#40;Transact-SQL-&#41;](/sql/t-sql/language-elements/use-transact-sql)   
 [Konfiguration der metadatensicht](../security/metadata-visibility-configuration.md)   
 [HAS_PERMS_BY_NAME &#40;Transact-SQL&#41;](/sql/t-sql/functions/has-perms-by-name-transact-sql)  
  
  
