---
title: Zuordnung von Quell-und Ziel Datentypen (accesstosql) | Microsoft-Dokumentation
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
ms.openlocfilehash: e0600778b938a7736ab1112f31bbe4828605cdaf
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "67907159"
---
# <a name="mapping-source-and-target-data-types-accesstosql"></a>Zuordnung von Quell-und Ziel Datentypen (accesstosql)
Zugriffsdaten Bank Typen unter [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] scheiden sich von Datenbanktypen. Wenn Sie Access-Datenbankobjekte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in-Objekte konvertieren, müssen Sie angeben, wie Datentypen aus [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]dem Zugriff zugeordnet werden sollen. Sie können die standardmäßigen Datentyp Zuordnungen akzeptieren, oder Sie können die Zuordnungen anpassen, wie in den folgenden Prozeduren gezeigt.  
  
## <a name="default-mappings"></a>Standardzuordnungen  
SSMA verfügt über einen Standardsatz von Datentyp Zuordnungen. Die Liste der Standard Zuordnungen finden Sie unter [Projekteinstellungen (Typzuordnung)](https://msdn.microsoft.com/b87b9683-abed-4677-8c50-18bdba704655).  
  
## <a name="customizing-data-type-mappings"></a>Anpassen von Datentyp Zuordnungen  
Mit dem Dialogfeld **Projekteinstellungen** können Sie anpassen, wie Typen für alle Datenbanken und Datenbankobjekte in einem Projekt zugeordnet werden. Die Typzuordnungen für ein Projekt gelten für alle Datenbanken und Datenbankobjekte, die keine benutzerdefinierten Typzuordnungen aufweisen.  
  
Sie können auch die Datentyp Zuordnung auf Datenbank-oder Tabellenebene anpassen.  
  
Im folgenden Verfahren wird gezeigt, wie Datentypen auf der Projekt-, Datenbank-oder Datenbankobjekt Ebene zugeordnet werden.  
  
**So ordnen Sie Datentypen zu**  
  
1.  Um die Datentyp Zuordnung für das gesamte Projekt anzupassen, öffnen Sie das Dialogfeld **Projekteinstellungen** :  
  
    1.  Wählen Sie **im Menü Extras** die Option **Projekteinstellungen**aus.  
  
    2.  Wählen Sie im linken Bereich **Typzuordnung**aus.  
  
        Das Typmapping-Diagramm und die Schaltflächen werden im rechten Bereich angezeigt.  
  
    Wenn Sie die Datentyp Zuordnung auf Datenbank-oder Tabellenebene anpassen möchten, wählen Sie im Bereich Access Metadata Explorer die Datenbank oder Tabelle aus:  
  
    1.  Erweitern Sie im Bereich Access Metadata Explorer den Eintrag **Access-Metabase**, und erweitern Sie dann **Datenbanken**.  
  
    2.  Wählen Sie die Datenbank oder Tabelle aus, für die Sie die Datentyp Zuordnung anpassen möchten.  
  
    3.  Klicken Sie im rechten Bereich auf **Typzuordnung**.  
  
2.  Gehen Sie folgendermaßen vor, um eine neue Zuordnung hinzuzufügen:  
  
    1.  Klicken Sie im Bereich Typzuordnung auf **Hinzufügen**.  
  
    2.  Wählen Sie im Dialogfeld **neue Typzuordnung** unter **Quelltyp**den zuzuordnenden Zuordnungs Datentyp aus.  
  
    3.  Wenn der Typ eine Länge erfordert, geben Sie die minimalen und maximalen Daten Längen für die Zuordnung an, indem Sie die Kontrollkästchen **aus** und **auf** aktivieren und dann die Werte eingeben.  
  
        Auf diese Weise können Sie die Datenzuordnung für kleinere und größere Werte desselben Datentyps anpassen.  
  
    4.  Wählen Sie unter **Zieltyp**den Ziel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datentyp aus.  
  
        Einige Typen erfordern eine Länge des Ziel Datentyps. Wenn dies erforderlich ist, geben Sie die neue Daten Länge im Feld **Ersetzen durch** ein, und klicken Sie dann auf **OK**.  
  
3.  Gehen Sie folgendermaßen vor, um eine Datentyp Zuordnung zu bearbeiten:  
  
    1.  Klicken Sie im Bereich Typzuordnung auf **Bearbeiten**.  
  
    2.  Wählen Sie im Dialogfeld **typzuordnungs Liste** unter **Quelltyp**den zuzuordnenden Zuordnungs Datentyp aus.  
  
    3.  Wenn der Typ eine Länge erfordert, geben Sie die minimalen und maximalen Daten Längen für die Zuordnung an, indem Sie die Kontrollkästchen **aus** und **auf** aktivieren und dann die Werte eingeben.  
  
        Auf diese Weise können Sie die Datenzuordnung für kleinere und größere Werte desselben Datentyps anpassen.  
  
    4.  Wählen Sie unter **Zieltyp**den Ziel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datentyp aus.  
  
        Einige Typen erfordern eine Länge des Ziel Datentyps. Wenn dies erforderlich ist, geben Sie die neue Daten Länge im Feld **Ersetzen durch** ein, und klicken Sie dann auf **OK**.  
  
4.  Gehen Sie folgendermaßen vor, um eine Datentyp Zuordnung zu entfernen:  
  
    1.  Wählen Sie im Bereich Typzuordnung die Zeile in der Liste Typzuordnung aus, die die Datentyp Zuordnung enthält, die Sie entfernen möchten.  
  
    2.  Klicken Sie auf **Entfernen**.  
  
## <a name="next-steps"></a>Nächste Schritte  
Der nächste Schritt des Migrations Vorgangs ist das [Konvertieren des Zugriffs auf Datenbankobjekte in SQL Server Objekte](converting-access-database-objects-accesstosql.md) .  
  
## <a name="see-also"></a>Weitere Informationen  
[Migration von Access-Datenbanken zu SQL Server](migrating-access-databases-to-sql-server-azure-sql-db-accesstosql.md)  
  
