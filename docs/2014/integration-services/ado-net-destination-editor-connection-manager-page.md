---
title: ADO.NET-Ziel-Editor (Seite Verbindungs-Manager) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.adonetdest.connection.f1
ms.assetid: a3b11286-32c8-40e1-8ae7-090e2590345a
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 887f881ad6a4cefec80620ebedb2ac210692ce5d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48090097"
---
# <a name="ado-net-destination-editor-connection-manager-page"></a>ADO.NET-Ziel-Editor (Seite 'Verbindungs-Manager')
  Mithilfe der Seite **Verbindungs-Manager** des Dialogfelds **ADO.NET-Ziel-Editor** können Sie die [!INCLUDE[vstecado](../includes/vstecado-md.md)] -Verbindung für das Ziel auswählen. Außerdem können Sie auf dieser Seite eine Tabelle oder Sicht aus der Datenbank auswählen.  
  
 Weitere Informationen zum ADO NET-Ziel finden Sie unter [ADO NET Destination](data-flow/ado-net-destination.md).  
  
 **So öffnen Sie die Seite "Verbindungs-Manager"**  
  
1.  Öffnen Sie in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]das [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Paket, das ADO.NET als Ziel hat.  
  
2.  Doppelklicken Sie auf der Registerkarte **Datenfluss** auf das ADO NET-Ziel.  
  
3.  Klicken Sie im **ADO.NET-Ziel-Editor**auf **Verbindungs-Manager**.  
  
## <a name="static-options"></a>Statische Optionen  
 **Connection manager**  
 Wählen Sie in der Liste einen vorhandenen Verbindungs-Manager aus, oder erstellen Sie eine neue Verbindung, indem Sie auf **Neu**klicken.  
  
 **Neu**  
 Erstellen Sie mithilfe des Dialogfelds **ADO.NET-Verbindungs-Manager konfigurieren** einen neuen Verbindungs-Manager.  
  
 **Tabelle oder Sicht verwenden**  
 Wählen Sie eine vorhandene Tabelle oder Sicht aus der Liste aus, oder erstellen Sie eine neue Tabelle, indem Sie auf **Neu**klicken.  
  
 **Neu**  
 Erstellen Sie mithilfe des Dialogfelds **Tabelle erstellen** eine neue Tabelle oder Sicht.  
  
> [!NOTE]  
>  Wenn Sie auf **Neu**klicken, generiert [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] eine Standard-CREATE TABLE-Anweisung auf Grundlage der verbundenen Datenquelle. Diese Standard-CREATE TABLE-Anweisung enthält nicht das FILESTREAM-Attribut, selbst wenn die Quelltabelle eine Spalte mit der Erklärung des FILESTREAM-Attributs enthält. Um eine [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Komponente mit dem FILESTREAM-Attribut auszuführen, implementieren Sie zunächst die FILESTREAM-Speicherung in der Zieldatenbank. Fügen Sie dann das FILESTREAM-Attribut der CREATE TABLE-Anweisung im Dialogfeld **Tabelle erstellen** hinzu. Weitere Informationen finden Sie unter [Blob-Daten &#40;Binary Large Object, SQL Server&#41;](../relational-databases/blob/binary-large-object-blob-data-sql-server.md).  
  
 **Vorschau**  
 Zeigen Sie mithilfe des Dialogfelds **Vorschau der Abfrageergebnisse anzeigen** eine Vorschau der Ergebnisse an. In der Vorschau können bis zu 200 Zeilen angezeigt werden.  
  
 **Masseneinfügung verwenden, falls verfügbar**  
 Geben Sie an, ob die Schnittstelle <xref:System.Data.SqlClient.SqlBulkCopy> verwendet werden soll, um die Leistung von Masseneinfügungsvorgängen zu verbessern.  
  
 Nur ADO.NET-Anbieter, die ein <xref:System.Data.SqlClient.SqlConnection> -Objekt zurückgeben, unterstützen die Verwendung der <xref:System.Data.SqlClient.SqlBulkCopy> -Schnittstelle. Der .NET-Datenanbieter für SQL Server (SqlClient) gibt ein <xref:System.Data.SqlClient.SqlConnection> -Objekt zurück, und ein benutzerdefinierter Anbieter gibt möglicherweise ein <xref:System.Data.SqlClient.SqlConnection> -Objekt zurück.  
  
 Sie können .NET-Datenanbieter für SQL Server (SqlClient) verwenden, für die Verbindung [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssSDSfull](../includes/sssdsfull-md.md)].  
  
 Wenn Sie **Masseneinfügung verwenden, falls verfügbar**auswählen und für **Zeile umleiten** die Option **Fehler**festlegen, enthält der Datenbatch, der vom Ziel an die Fehlerausgabe umgeleitet wird, möglicherweise intakte Zeilen. Weitere Informationen zur Behandlung von Fehlern in Massenvorgängen finden Sie unter [Fehlerbehandlung in Daten](data-flow/error-handling-in-data.md). Weitere Informationen zu den **Fehler** finden Sie unter [ADO.NET-Ziel-Editor &#40;Seite "Fehlerausgabe"&#41;](../../2014/integration-services/ado-net-destination-editor-error-output-page.md).  
  
> [!NOTE]  
>  Wenn eine [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] - oder Sybase-Quelltabelle eine Identitätsspalte enthält, müssen Sie SQL ausführen-Tasks zum Ausführen einer SET IDENTITY_INSERT-Anweisung vor und nach dem ADO NET-Ziel verwenden. Die Identitätsspalteneigenschaft gibt einen inkrementellen Wert für die Spalte an. Die SET IDENTITY_INSERT-Anweisung ermöglicht, dass explizite Werte in die Identitätsspalte eingefügt werden können. Legen Sie zum Ausführen der CREATE TABLE- und SET IDENTITY-Anweisungen für die Verbindung mit der gleichen Datenbank den `RetainSameConnection` Eigenschaft der [!INCLUDE[vstecado](../includes/vstecado-md.md)] Verbindungs-Manager `True`. Verwenden Sie den gleichen [!INCLUDE[vstecado](../includes/vstecado-md.md)] -Verbindungs-Manager auch für die "SQL ausführen"-Tasks und das ADO.NET-Ziel.  
>   
>  Weitere Informationen finden Sie unter [SET IDENTITY_INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-identity-insert-transact-sql) und [IDENTITY &#40;Eigenschaft&#41; &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql-identity-property).  
  
## <a name="external-resources"></a>Externe Ressourcen  
 Technischer Artikel [Schnelles Laden von Daten in eine Windows Azure SQL-Datenbank](http://go.microsoft.com/fwlink/?LinkId=244333)auf sqlcat.com  
  
## <a name="see-also"></a>Siehe auch  
 [ADO.NET-Ziel-Editor &#40;Seite "Zuordnungen"&#41;](../../2014/integration-services/ado-net-destination-editor-mappings-page.md)   
 [ADO.NET-Ziel-Editor &#40;Seite "Fehlerausgabe"&#41;](../../2014/integration-services/ado-net-destination-editor-error-output-page.md)   
 [ADO.NET-Verbindungs-Manager](connection-manager/ado-net-connection-manager.md)   
 [SQL ausführen (Task)](control-flow/execute-sql-task.md)  
  
  
