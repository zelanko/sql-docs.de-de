---
title: Fragen zur Datenbankentwicklung (Visual Database Tools) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- compatibility [SQL Server], multuser database changes
- database evolution [SQL Server]
ms.assetid: 1ed6ae10-d212-4ec2-8569-1b94ab1cba6d
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d3a1f10ae77061983a5cf64ddd5a3462bb4be49b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "63035589"
---
# <a name="issues-of-database-evolution-visual-database-tools"></a>Fragen zur Datenbankentwicklung (Visual Database Tools)
  Wenn Sie die Struktur einer bereitgestellten Datenbank ändern, sollten Sie insbesondere darauf achten, dass die Änderungen mit den vorhandenen Daten und der vorhandenen Datenbankstruktur kompatibel sind. Besondere Vorkehrungen können bei den folgenden Änderungen erforderlich sein:  
  
-   **Hinzufügen einer Einschränkung** Wenn Sie eine Einschränkung hinzufügen, enthält die Datenbank möglicherweise bereits Daten, die Sie nicht erfüllen. Wenn Sie versuchen, die neue Einschränkung zu speichern, werden Sie im [Benachrichtigung nach dem Speichervorgang (Dialogfeld) &#40;Visual Database Tools&#41;](visual-database-tools.md) darüber informiert, dass der Datenbankserver die Einschränkung nicht erstellen konnte. Um die Übernahme der neuen Einschränkung in die Datenbank zu erzwingen, können Sie das Kontrollkästchen **Vorhandene Daten bei Erstellung überprüfen** deaktivieren.  
  
-   **Hinzufügen einer Beziehung** Wenn Sie eine Beziehung hinzufügen, enthält die Datenbank möglicherweise bereits Zeilen der Fremdschlüssel Tabelle, die keine entsprechenden Zeilen in der Primärschlüssel Tabelle enthalten. Das bedeutet, dass die vorhandenen Daten die Forderung nach referenzieller Integrität nicht erfüllen. Wenn Sie versuchen, die neue Beziehung zu speichern, werden Sie im [Benachrichtigung nach dem Speichervorgang (Dialogfeld) &#40;Visual Database Tools&#41;](visual-database-tools.md) darüber informiert, dass der Datenbankserver die überarbeitete Fremdschlüsseltabelle nicht speichern konnte. Um die Übernahme der Änderung in die Datenbank zu erzwingen, können Sie das Kontrollkästchen **Vorhandene Daten bei Erstellung überprüfen** deaktivieren.  
  
-   **Ändern einer Tabelle, die zu einer indizierten Sicht beiträgt** Wenn Sie eine Tabelle ändern, die zu einer Microsoft SQL Server indizierten Sicht beiträgt, gehen die Indizes der Sicht verloren. Informationen über das Neuerstellen von Indizes finden Sie in SQL Server Books Online.  
  
-   **Löschen eines Objekts** Wenn Sie ein Objekt löschen, z. b. eine Spalte, Tabelle oder Sicht, überprüfen Sie zunächst, um sicherzustellen, dass auf das Objekt nicht von einem anderen Objekt in der Datenbank verwiesen wird.  
  
 Unabhängig davon, welche Arten von Änderungen Sie am Entwurf der Datenbank vornehmen, sollten Sie jede Änderung protokollieren. Eine Möglichkeit dafür ist das Aufbewahren der SQL-Skripts aller Änderungen, die Sie an der Produktionsdatenbank vornehmen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Unique-Einschränkungen und Check-Einschränkungen](../../relational-databases/tables/unique-constraints-and-check-constraints.md)   
 [Mehrbenutzerumgebungen &#40;Visual Database Tools&#41;](multiuser-environments-visual-database-tools.md)  
  
  
