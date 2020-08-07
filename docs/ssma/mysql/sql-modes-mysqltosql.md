---
title: SQL-Modi (mysqlto SQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: d840ee51-b863-4e77-84aa-37d3f094bfed
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: 4bc4b59984cc9e2e1f7a6c358f24e3fc0d2e86be
ms.sourcegitcommit: e8f6c51d4702c0046aec1394109bc0503ca182f0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/07/2020
ms.locfileid: "87935099"
---
# <a name="sql-modes-mysqltosql"></a>SQL-Modi (MySqlToSql)
SSMA für MySQL kann in verschiedenen SQL-Modi betrieben werden und kann diese Modi für verschiedene Clients unterschiedlich anwenden.  
  
Modi definieren die SQL-Syntax, die von MySQL unterstützt wird, sowie die Art der zu überprüfenden Daten Validierungs Prüfungen. Dies erleichtert die Verwendung von MySQL in verschiedenen Umgebungen und die Verwendung von MySQL mit SQL Server.  
  
## <a name="sql-modes-grid"></a>Raster für SQL-Modi:  
  
-   Das Raster SQL-Modi auf Stamm Ebene enthält die folgenden Spalten: **SQL-Modusname**, **geladene SQL-Modi**und **effektive SQL-Modi**.  
  
-   Das Raster SQL-Modi in der Kategorie Datenbanken, Datenbank, Tabellen Kategorie, Anweisungs Kategorie, Ansichts Kategorie, Tabelle, Sicht, Funktionen, Prozeduren, UDF und Ereignis Objektebene enthält die folgenden Spalten: **SQL-Modusname**, **geerbte SQL-Modi**und **effektive SQL-Modi**.  
  
-   Das Raster mit den SQL-Modi in gespeicherter Prozedur, gespeicherter Funktion und triggerebene enthält die folgenden Spalten: **SQL-Modusname**, **ursprüngliche SQL-Modi**und **effektive SQL-Modi**.  
  
> [!NOTE]  
> Die Gruppen Modi werden in der Spalte "SQL Mode Name" in Fett Schrift angezeigt.  
  
## <a name="loaded-sql-modes"></a>Geladene SQL-Modi  
Dabei handelt es sich um die SQL-Modi, die auf der Sitzungs-oder Stamm Ebene festgelegt werden. Die nach dem Laden in die Zieldatenbank geladenen SQL-Modi können nicht bearbeitet oder geändert werden.  
  
## <a name="inherited-sql-modes"></a>Geerbte SQL-Modi  
Dabei handelt es sich um die SQL-Modi, die vom entsprechenden übergeordneten Knoten geerbt werden.  
  
Mit Ausnahme der Funktionen Kategorie, der Prozeduren, der Ereignis Kategorie und der Trigger sind diese SQL-Modi auf allen Ebenen vorhanden (Datenbank, Tabellen Kategorie, Anweisungs Kategorie, Ansichts Kategorie, Tabelle, Sicht, Funktionen, Prozeduren, UDF und Ereignis Objekt).  
  
> [!NOTE]  
> Durch Aktivieren des Kontrollkästchens **vom übergeordneten Element erben** können geerbte SQL-Modi vom übergeordneten Knoten geerbt werden. Dieses Kontrollkästchen ist standardmäßig aktiviert.  
  
## <a name="original-sql-modes"></a>Ursprüngliche SQL-Modi  
Dies sind die SQL-Modi, die nur auf Funktions-, Prozedur-und triggerebene vorhanden sind.  
  
> [!NOTE]  
> Durch Aktivieren des Kontrollkästchens **ursprüngliches verwenden** können die SQL-Modi verwendet werden, die ursprünglich in der entsprechenden Funktion oder Prozedur bzw. dem entsprechenden Triggertyp verwendet wurden. Dieses Kontrollkästchen ist standardmäßig aktiviert.  
  
## <a name="effective-sql-modes"></a>Effektive SQL-Modi  
Effektive SQL-Modi können auf unterschiedlichen Ebenen folgendermaßen definiert werden:  
  
-   **Auf Sitzungs Ebene:**  
  
    1.  Alle geladenen SQL-Modi können als "effektive SQL-Modi" bezeichnet werden.  
  
    2.  Auf dieser Ebene können die effektiven SQL-Modi direkt und explizit geändert werden.  
  
    3.  Der effektive SQL-Modus, der explizit festgelegt wird, wird nicht als geladener SQL-Modus reflektiert und schließlich auf das Objekt angewendet.  
  
-   **Auf Funktions-, Prozedur-oder triggerebene:**  
  
    1.  Alle ursprünglichen SQL-Modi können als "effektive SQL-Modi" bezeichnet werden.  
  
    2.  Auf dieser Ebene kann der effektive SQL-Modus nur explizit geändert werden, wenn das Kontrollkästchen **ursprüngliches verwenden** deaktiviert ist.  
  
    3.  Der effektive SQL-Modus, der explizit festgelegt wird, wird nicht als ursprünglicher SQL-Modus reflektiert und schließlich auf das Objekt angewendet.  
  
-   **Auf anderen Knoten als Funktions-, Prozedur-oder triggerebene:**  
  
    1.  Alle geerbten SQL-Modi können als "effektive SQL-Modi" bezeichnet werden.  
  
    2.  Auf dieser Ebene kann der effektive SQL-Modus nur explizit geändert werden, wenn das Kontrollkästchen **vom übergeordneten Element erben** deaktiviert ist.  
  
    3.  Der effektive SQL-Modus, der explizit festgelegt wird, wird nicht als geerbte SQL-Modus reflektiert und schließlich auf das Objekt angewendet.  
  
