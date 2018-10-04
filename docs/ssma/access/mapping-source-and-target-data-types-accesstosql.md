---
title: Zuordnen von Quell- und Ziel-Datentypen (AccessToSQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- customizing data type mappings
- data types, mapping
- mapping, data types
- source data types
- target data types
ms.assetid: b362a075-16e7-423f-b63f-e1e9f02844a9
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 075cb0870d7fa3f4cbddaef60c2de4d1aa0683c3
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47668705"
---
# <a name="mapping-source-and-target-data-types-accesstosql"></a>Zuordnen von Quell- und Ziel-Datentypen (AccessToSQL)
Access-Datenbank unterscheiden sich von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbank-Datentypen. Wenn Sie den Zugriff auf Datenbankobjekte zu konvertieren, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Objekte aufweist, müssen Sie angeben, wie Sie Datentypen aus den Zugriff auf zuordnen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Sie können die standardmäßigen datentypzuordnungen übernehmen und die Zuordnungen können angepasst werden, wie in den folgenden Verfahren dargestellt.  
  
## <a name="default-mappings"></a>Standardzuordnungen  
SSMA ist einen Standardsatz von datentypzuordnungen. Die Liste der standardzuordnungen, finden Sie unter [Project Settings (Type Mapping)](http://msdn.microsoft.com/b87b9683-abed-4677-8c50-18bdba704655).  
  
## <a name="customizing-data-type-mappings"></a>Anpassen von Datentypzuordnungen  
Mithilfe der **Projekteinstellungen** im Dialogfeld können Sie anpassen, wie Typen für alle Datenbanken und Datenbankobjekte in einem Projekt zugeordnet sind. Die datentypzuordnungen für ein Projekt gelten für alle Datenbanken und Datenbankobjekte, die nicht über benutzerdefinierte Zuordnungen verfügen.  
  
Sie können auch die Zuordnung von Datentypen auf der Datenbank- oder Tabellenebene anpassen.  
  
Das folgende Verfahren zeigt, wie Datentypen auf das Projekt, Datenbank oder Datenbankebene-Objekt zugeordnet wird.  
  
**Zuordnen von Datentypen**  
  
1.  Öffnen Sie zum Zuordnen von Datentypen für das gesamte Projekt anpassen, die **Projekteinstellungen** Dialogfeld:  
  
    1.  Auf der **Tools** , wählen Sie im Menü **Projekteinstellungen**.  
  
    2.  Wählen Sie im linken Bereich **Type Mapping**.  
  
        Das Diagramm für Typ-Zuordnung und die Schaltflächen werden im rechten Bereich angezeigt.  
  
    Oder wählen Sie zum Zuordnen von Datentypen auf der Datenbank oder Tabelle anpassen, die Datenbank oder Tabelle im Bereich Metadaten-Explorer für den Zugriff:  
  
    1.  Erweitern Sie im Bereich Metadaten-Explorer für den Zugriff **Access-Metabase**, und erweitern Sie dann **Datenbanken**.  
  
    2.  Wählen Sie die Datenbank oder Tabelle, für die Sie die datentypzuordnung anpassen möchten.  
  
    3.  Klicken Sie im rechten Bereich auf **Type Mapping**.  
  
2.  Wenn eine neue Zuordnung hinzufügen möchten, führen Sie folgende Schritte aus:  
  
    1.  Klicken Sie im Bereich Type Mapping auf **hinzufügen**.  
  
    2.  In der **neue Type Mapping** Dialogfeld **Quelltyp**, wählen Sie die Access-Datentyp zugeordnet.  
  
    3.  Wenn der Typ eine Länge erfordert, geben Sie die minimalen und maximalen Länge für die Zuordnung durch Auswahl der **aus** und **zu** Kontrollkästchen und klicken Sie dann die Werte eingeben.  
  
        Dadurch können Sie das Anpassen der datenzuordnung für kleinere und größere Werte den gleichen Datentyp.  
  
    4.  Klicken Sie unter **Zieltyp**, wählen Sie das Ziel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datentyp.  
  
        Einige Datentypen erfordern eine Ziel-Datentyplänge. Wenn dies erforderlich ist, geben Sie die neue Datenlänge in die **ersetzen durch** ein, und klicken Sie dann auf **OK**.  
  
3.  Führen Sie folgende Schritte aus, um eine datentypzuordnung zu bearbeiten:  
  
    1.  Klicken Sie im Bereich Type Mapping auf **bearbeiten**.  
  
    2.  In der **Typliste Zuordnung** Dialogfeld **Quelltyp**, wählen Sie die Access-Datentyp zugeordnet.  
  
    3.  Wenn der Typ eine Länge erfordert, geben Sie die minimalen und maximalen Länge für die Zuordnung durch Auswahl der **aus** und **zu** Kontrollkästchen und klicken Sie dann die Werte eingeben.  
  
        Dadurch können Sie das Anpassen der datenzuordnung für kleinere und größere Werte den gleichen Datentyp.  
  
    4.  Klicken Sie unter **Zieltyp**, wählen Sie das Ziel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datentyp.  
  
        Einige Datentypen erfordern eine Ziel-Datentyplänge. Wenn dies erforderlich ist, geben Sie die neue Datenlänge in die **ersetzen durch** ein, und klicken Sie dann auf **OK**.  
  
4.  Um eine datentypzuordnung zu entfernen, führen Sie folgende Schritte aus:  
  
    1.  Wählen Sie die Zeile in der Liste ' datentypzuordnung ', die die Zuordnung von Datentypen enthält, die Sie entfernen möchten, klicken Sie im Bereich "Zuordnung".  
  
    2.  Klicken Sie auf **Entfernen**.  
  
## <a name="next-steps"></a>Nächste Schritte  
Im nächsten Schritt des Migrationsvorgangs [konvertieren Sie den Zugriff auf Datenbankobjekte in SQL Server-Objekte](converting-access-database-objects-accesstosql.md)  
  
## <a name="see-also"></a>Siehe auch  
[Migrieren von Access-Datenbanken zu SQLServer](migrating-access-databases-to-sql-server-azure-sql-db-accesstosql.md)  
  
