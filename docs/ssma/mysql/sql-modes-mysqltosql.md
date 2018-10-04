---
title: SQL Modes (MySQLToSQL)) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: d840ee51-b863-4e77-84aa-37d3f094bfed
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 46d91efa1451749d8d1cce2b1a8cf361cc30986a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47737308"
---
# <a name="sql-modes-mysqltosql"></a>SQL-Modi (MySqlToSql)
SSMA für MySQL kann in verschiedenen SQL-Modi betrieben werden, und diese Modi für verschiedene Clients unterschiedlich anwenden zu kann.  
  
Modi definieren, die SQL-Syntax, die MySQL unterstützen soll, und die Art der Validierung überprüft, dass ausgeführt werden muss. Dies erleichtert die Verwendung von MySQL in verschiedenen Umgebungen und MySQL mit SQL Server verwenden.  
  
## <a name="sql-modes-grid"></a>Raster für SQL-Modi:  
  
-   SQL Modes Raster auf Stammebene enthält die folgenden Spalten: **SQL Modusname**, **geladen SQL Modi**, und **effektiver SQL-Modi**.  
  
-   SQL Modes Raster Datenbanken Kategorie, Datenbank, Tabelle Kategorie, Anweisungen Kategorie, Ansichten Kategorie, Tabelle, Sicht, Funktionen, Prozeduren, UDF und Ereignisebene-Objekt enthält die folgenden Spalten: **SQL Modusname**,  **Geerbt von SQL-Modi**, und **effektiver SQL-Modi**.  
  
-   SQL Modes Raster auf gespeicherte Prozeduren, gespeichert-Funktion und Trigger-Ebene enthält die folgenden Spalten: **SQL Modusname**, **ursprünglichen SQL-Modi**, und **effektiver SQL-Modi**.  
  
> [!NOTE]  
> Gruppe Modi in angezeigt werden fett, unter der Spalte "SQL-Modus-Name".  
  
## <a name="loaded-sql-modes"></a>Laden von SQL-Modi  
Hierbei handelt es sich um die SQL-Modi, die auf der Sitzungs- oder Stamm festgelegt werden. Die SQL-Modi, die einmal geladen wird, in der Zieldatenbank kann nicht bearbeitet oder geändert werden.  
  
## <a name="inherited-sql-modes"></a>Geerbte SQL-Modi  
Hierbei handelt es sich um die SQL-Modi, die von den entsprechenden übergeordneten Knoten geerbt werden.  
  
Mit Ausnahme der Kategorie "Funktionen", Prozeduren Ereigniskategorie, Kategorie Ereignisse und Trigger sind diese SQL-Modi auf allen Ebenen (Datenbank, Tabelle Kategorie, Anweisungen Kategorie, Ansichten Kategorie, Tabelle, Sicht, Funktionen, Prozeduren, UDF und Ereignis-Objekt) vorhanden.  
  
> [!NOTE]  
> Durch Auswahl der **vom übergeordneten Projekt erben** Kontrollkästchen, geerbt von SQL-Modi kann vom übergeordneten Knoten geerbt werden. Standardmäßig bleibt das Kontrollkästchen ausgewählt.  
  
## <a name="original-sql-modes"></a>Ursprüngliche SQL-Modi  
Hierbei handelt es sich um die SQL-Modi vorhanden auf nur die Ebenen der Funktion, Prozeduren und Trigger.  
  
> [!NOTE]  
> Durch Auswahl der **Verwendung-ursprüngliche** überprüfen, die SQL-Modi, die ursprünglich in die entsprechende Funktion verwendet wurden oder Prozedur oder des Triggers verwendet werden kann. Standardmäßig bleibt das Kontrollkästchen ausgewählt.  
  
## <a name="effective-sql-modes"></a>Effektive SQL-Modi  
Effektive SQL-Modi können auf verschiedenen Ebenen auf folgende Weise definiert werden:  
  
-   **Auf Sitzungsebene:**  
  
    1.  Alles, was die SQL-Modi geladen aufgerufen werden kann, "Effektive SQL Modes".  
  
    2.  Auf dieser Ebene können die effektive SQL-Modi direkt und explizit geändert werden.  
  
    3.  Der effektive SQL-Modus, der explizit festgelegt wird nicht als SQL-Modus geladen wiedergegeben und schließlich auf das Objekt angewendet wird.  
  
-   **Auf Ebene der Funktion oder Prozedur oder eines Triggers:**  
  
    1.  Die ursprüngliche SQL-Modi aufgerufen werden kann, "Effektive SQL Modes".  
  
    2.  Auf dieser Ebene effektivere SQL-Modus kann explizit geändert werden nur dann, wenn die **Verwendung-ursprüngliche** Kontrollkästchen deaktiviert ist.  
  
    3.  Der effektive SQL-Modus, der explizit festgelegt ist als der ursprüngliche SQL-Modus nicht wiedergegeben und schließlich auf das Objekt angewendet wird.  
  
-   **Auf die Knoten als Funktion oder Prozedur oder des Triggers auf:**  
  
    1.  Alles, was die geerbte SQL-Modi aufgerufen werden kann, "Effektive SQL Modes".  
  
    2.  Auf dieser Ebene effektivere SQL-Modus kann explizit geändert werden nur dann, wenn die **vom übergeordneten Projekt erben** Kontrollkästchen deaktiviert ist.  
  
    3.  Der effektive SQL-Modus, der explizit festgelegt wird nicht als SQL-Modus geerbt wiedergegeben und schließlich auf das Objekt angewendet wird.  
  
