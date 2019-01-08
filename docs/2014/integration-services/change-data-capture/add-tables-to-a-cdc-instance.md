---
title: Hinzufügen von Tabellen zu einer CDC-Instanz | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- addTabs
ms.assetid: ad260e19-c021-4035-9311-c02fc96ceaea
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: f82b6f68d7186d35fd1657cd56c4aa23fcf82b3e
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52769052"
---
# <a name="add-tables-to-a-cdc-instance"></a>Hinzufügen von Tabellen zu einer CDC-Instanz
  Verwenden Sie das Dialogfeld Tabellenauswahl, um der CDC-Instanz weitere Tabellen der Oracle-Quelle hinzuzufügen. Die ausgewählten Tabellen werden im Eigenschaften-Editor der Liste auf der Registerkarte **Tabellen** hinzugefügt.  
  
 Standardmäßig sind in diesem Dialogfeld in der Tabellenliste keine Tabellen enthalten. Sie können das Kontrollkästchen **(Alles auswählen)** aktivieren oder nach bestimmten Tabellen suchen.  
  
 **So suchen Sie nach bestimmten Tabellen**  
 Geben Sie die Suchkriterien wie folgt ein, und klicken Sie dann auf **Suchen**:  
  
-   **Schema**: Wählen Sie aus der Liste ein Datenbankschema. In der Liste werden nur Tabellen aufgeführt, die über dieses Schema verfügen.  
  
-   **Table Name Pattern**: Geben Sie eine beliebige Zeichenfolge von Zeichen ein. Es werden nur Tabellen angezeigt, die die eingegebene Zeichenfolge enthalten.  
  
> [!NOTE]  
>  Sie können Kriterien in eines der Felder oder beide Felder eingeben.  
  
-   **Zeigen Sie die ersten 1000 übereinstimmenden Tabellen**: Standardmäßig ist dieses Kontrollkästchen aktiviert. Diese Option beschränkt die Anzeige auf die ersten 1000 übereinstimmenden Tabellen. Wenn Sie das Kontrollkästchen deaktivieren, werden alle Tabellen angezeigt, die zu einer Übereinstimmung führen. Falls eine große Anzahl von Tabellen vorhanden ist, kann es relativ lange dauern, bis die Liste angezeigt wird.  
  
 **So wählen Sie die Tabellen aus, die in die CDC-Instanz eingeschlossen werden sollen**  
 Aktivieren Sie das Kontrollkästchen neben einer beliebigen Tabelle, die Sie einschließen möchten, und klicken Sie dann auf **Hinzufügen**. Die Tabellen werden im Assistenten für neue Instanzen der Liste auf der Seite **Select Tables and Columns** hinzugefügt.  
  
 Klicken Sie auf **Schließen** , um das Dialogfeld zu schließen, ohne Tabellen hinzuzufügen.  
  
> [!NOTE]  
>  Wenn Sie eine Tabelle auswählen, die einen nicht unterstützten Datentyp enthält, wird eine Fehlermeldung angezeigt, und die Tabelle wird nicht eingeschlossen.  
  
> [!NOTE]  
>  Sie können die Liste der Tabellen im Viewer anzeigen. Beim Verwenden des Viewers sind die Informationen schreibgeschützt. Der Viewer enthält auch eine Liste der aufgezeichneten Spalten in der Tabelle. Informationen zum Zugriff auf den Viewer finden Sie unter [How to Manage a CDC Instance](manage-a-cdc-instance.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Bearbeiten der CDC-Instanzeigenschaften](how-to-edit-the-cdc-instance-properties.md)   
 [How to Manage a CDC Instance](manage-a-cdc-instance.md)   
 [Auswählen von Oracle-Tabellen zum Aufzeichnen von Änderungen](select-oracle-tables-for-capturing-changes.md)  
  
  
