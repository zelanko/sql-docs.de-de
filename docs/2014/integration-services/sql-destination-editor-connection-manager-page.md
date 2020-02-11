---
title: Ziel-Editor für SQL (Seite Verbindungs-Manager) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.sqlserverdestadapter.connection.f1
helpviewer_keywords:
- SQL Server Destination Editor
ms.assetid: 423e1654-54af-47c6-ab6f-98670534557d
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: d3bffc98a14c1a8bc672e9f15a4bad8b6f5a7dbe
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66055411"
---
# <a name="sql-destination-editor-connection-manager-page"></a>Ziel-Editor für SQL (Seite Verbindungs-Manager)
  Mithilfe der Seite **Verbindungs-Manager** des Dialogfelds **Ziel-Editor für SQL** können Sie Informationen zur Datenquelle angeben und eine Vorschau der Ergebnisse anzeigen. Das [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Ziel lädt Daten in Tabellen oder Sichten in einer [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Datenbank.  
  
 Weitere Informationen zum SQL Server-Ziel finden Sie unter [SQL Server Destination](data-flow/sql-server-destination.md).  
  
## <a name="options"></a>Tastatur  
 **OLE DB Verbindungs-Manager**  
 Wählen Sie eine vorhandene Verbindung aus der Liste aus, oder erstellen Sie eine neue Verbindung, indem Sie auf **Neu**klicken.  
  
 **Neu**  
 Erstellen Sie mithilfe des Dialogfelds **OLE DB-Verbindungs-Manager konfigurieren** eine neue Verbindung.  
  
 **Tabelle oder Sicht verwenden**  
 Wählen Sie eine vorhandene Tabelle oder Sicht aus der Liste aus, oder erstellen Sie eine neue Verbindung, indem Sie auf **Neu**klicken.  
  
 **Neu**  
 Erstellen Sie mithilfe des Dialogfelds **Tabelle erstellen** eine neue Tabelle.  
  
> [!NOTE]  
>  Wenn Sie auf **neu**klicken [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , generiert eine standardmäßige CREATE TABLE-Anweisung, die auf der verbundenen Datenquelle basiert. Diese Standard-CREATE TABLE-Anweisung enthält nicht das FILESTREAM-Attribut, selbst wenn die Quelltabelle eine Spalte mit der Erklärung des FILESTREAM-Attributs enthält. Um eine [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Komponente mit dem FILESTREAM-Attribut auszuführen, implementieren Sie zunächst die FILESTREAM-Speicherung in der Zieldatenbank. Fügen Sie dann das FILESTREAM-Attribut der CREATE TABLE-Anweisung im Dialogfeld **Tabelle erstellen** hinzu. Weitere Informationen finden Sie unter [Blob-Daten &#40;Binary Large Object, SQL Server&#41;](../relational-databases/blob/binary-large-object-blob-data-sql-server.md).  
  
 **Vorschau**  
 Zeigen Sie mithilfe des Dialogfelds **Vorschau der Abfrageergebnisse anzeigen** eine Vorschau der Ergebnisse an. In der Vorschau können bis zu 200 Zeilen angezeigt werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Fehler- und Meldungsreferenz von Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Ziel-Editor für SQL &#40;Seite "Zuordnungen"&#41;](../../2014/integration-services/sql-destination-editor-mappings-page.md)   
 [Ziel-Editor für SQL &#40;Seite "Erweitert"&#41;](../../2014/integration-services/sql-destination-editor-advanced-page.md)   
 [Massenladen von Daten mithilfe des SQL Server-Ziels](data-flow/bulk-load-data-by-using-the-sql-server-destination.md)  
  
  
