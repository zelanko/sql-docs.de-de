---
title: Einrichten des Datenbankdiagramm-Designers (Visual Database Tools) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.diagnostic.InstallSqlDiagramSupport
helpviewer_keywords:
- Database Diagram Designer
- database diagrams [SQL Server], Database Diagram Designer
- diagrams [SQL Server], Database Diagram Designer
ms.assetid: 927321ee-b459-4f5b-9719-4a7a95639143
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 5275b35b7a6b8af51e677523afa3bc612e3ea4f1
ms.sourcegitcommit: 50b60ea99551b688caf0aa2d897029b95e5c01f3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "51700418"
---
# <a name="set-up-database-diagram-designer-visual-database-tools"></a>Einrichten des Datenbankdiagramm-Designers (Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Der Datenbankdiagramm-Designer kann erst verwendet werden, nachdem er von einem Mitglied der **db_owner** -Rolle für den Zugriff auf Diagramme eingerichtet wurde.  
  
### <a name="to-set-up-database-diagramming"></a>So richten Sie das Erstellen von Datenbankdiagrammen ein  
  
1.  Erweitern Sie im Objekt-Explorer einen Datenbankknoten.  
  
2.  Erweitern Sie den Knoten Datenbankdiagramme unter der Datenbankverbindung.  
  
3.  Wählen Sie an der entsprechenden Aufforderung **Ja** aus, wenn Sie das Erstellen von Datenbankdiagrammen einrichten möchten.  
  
    > [!NOTE]  
    > Damit werden die Datenbankdiagrammtabelle, gespeicherte Systemprozeduren und eine Systemfunktion in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbank erstellt.  
  
4.  Visual Studio erstellt die folgenden Objekte für die Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
    1.  sysdiagrams-Tabelle  
  
    2.  Gespeicherte Prozedur sp_alterdiagram  
  
    3.  Gespeicherte Prozedur sp_creatediagram  
  
    4.  Gespeicherte Prozedur sp_dropdiagram  
  
    5.  Gespeicherte Prozedur sp_renamediagram  
  
    6.  fn_diagramobjects-Funktion  
  
    7.  Gespeicherte Prozedur sp_helpdiagrams  
  
    8.  Gespeicherte Prozedur sp_helpdiagramsdefinition  
  
    9. Gespeicherte Prozedur sp_upgraddiagrams  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
[Grundlagen des Besitzes von Datenbankdiagrammen &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/understand-database-diagram-ownership-visual-database-tools.md)  
[Aktualisieren von Datenbankdiagrammen aus älteren Versionen &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/upgrade-database-diagrams-from-previous-editions-visual-database-tools.md)  
[ALTER AUTHORIZATION (Transact-SQL)](https://msdn.microsoft.com/8c805ae2-91ed-4133-96f6-9835c908f373)  
  
