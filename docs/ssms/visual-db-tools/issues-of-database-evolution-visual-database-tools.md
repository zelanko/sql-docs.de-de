---
title: Fragen zur Datenbankentwicklung (Visual Database Tools) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- compatibility [SQL Server], multuser database changes
- database evolution [SQL Server]
ms.assetid: 1ed6ae10-d212-4ec2-8569-1b94ab1cba6d
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 9b40aabf488f0d0c294638c43153e8f384187781
ms.sourcegitcommit: bb5484b08f2aed3319a7c9f6b32d26cff5591dae
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/06/2019
ms.locfileid: "65096685"
---
# <a name="issues-of-database-evolution-visual-database-tools"></a>Fragen zur Datenbankentwicklung (Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Wenn Sie die Struktur einer bereitgestellten Datenbank ändern, sollten Sie insbesondere darauf achten, dass die Änderungen mit den vorhandenen Daten und der vorhandenen Datenbankstruktur kompatibel sind. Besondere Vorkehrungen können bei den folgenden Änderungen erforderlich sein:  
  
-   **Hinzufügen einer Einschränkung**: Wenn Sie eine Einschränkung hinzufügen, können in der Datenbank bereits Daten vorhanden sein, die der Einschränkung nicht entsprechen. Wenn Sie versuchen, die neue Einschränkung zu speichern, werden Sie im [Benachrichtigung nach dem Speichervorgang (Dialogfeld) &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/post-save-notifications-dialog-box-visual-database-tools.md) darüber informiert, dass der Datenbankserver die Einschränkung nicht erstellen konnte. Um die Übernahme der neuen Einschränkung in die Datenbank zu erzwingen, können Sie das Kontrollkästchen **Vorhandene Daten bei Erstellung überprüfen** deaktivieren.  
  
-   **Hinzufügen einer Beziehung** : Wenn Sie eine Beziehung hinzufügen, können sich in der Datenbank bereits Zeilen der Fremdschlüsseltabelle befinden, für die es in der Primärschlüsseltabelle keine übereinstimmenden Zeilen gibt. Das bedeutet, dass die vorhandenen Daten die Forderung nach referenzieller Integrität nicht erfüllen. Wenn Sie versuchen, die neue Beziehung zu speichern, werden Sie im [Benachrichtigung nach dem Speichervorgang (Dialogfeld) &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/post-save-notifications-dialog-box-visual-database-tools.md) darüber informiert, dass der Datenbankserver die überarbeitete Fremdschlüsseltabelle nicht speichern konnte. Um die Übernahme der Änderung in die Datenbank zu erzwingen, können Sie das Kontrollkästchen **Vorhandene Daten bei Erstellung überprüfen** deaktivieren.  
  
-   **Ändern einer Tabelle, die zu einer indizierten Ansicht gehört** : Wenn Sie eine Tabelle ändern, die Teil einer mit Microsoft SQL Server indizierten Ansicht ist, gehen die zur Ansicht gehörenden Indizes verloren. Informationen über das Neuerstellen von Indizes finden Sie in SQL Server Books Online.  
  
-   **Objekt löschen** : Wenn Sie ein Objekt löschen, z. B. eine Spalte, Tabelle oder Ansicht, prüfen Sie zuerst, ob auf das Objekt nicht von einem anderen Objekt in der Datenbank verwiesen wird.  
  
Unabhängig davon, welche Arten von Änderungen Sie am Entwurf der Datenbank vornehmen, sollten Sie jede Änderung protokollieren. Eine Möglichkeit dafür ist das Aufbewahren der SQL-Skripts aller Änderungen, die Sie an der Produktionsdatenbank vornehmen.  
  
## <a name="see-also"></a>Weitere Informationen  
[Verwenden von Einschränkungen (Visual Database Tools)](https://msdn.microsoft.com/637098af-2567-48f8-90f4-b41df059833e)  
[Mehrbenutzerumgebungen &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/multiuser-environments-visual-database-tools.md)  
  
