---
title: Editor für den Task ' SQL Server Objekte übertragen ' (Seite Objekte) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transfersqlserverobjects.objects.f1
helpviewer_keywords:
- Transfer SQL Server Objects Task Editor
ms.assetid: 8cc09118-70ac-4013-8308-d87f8411ca0c
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 3ae231e933e30613d45fe00eaa99d6a2d5c9c772
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66054868"
---
# <a name="transfer-sql-server-objects-task-editor-objects-page"></a>Editor für den Task 'SQL Server-Objekte übertragen' (Seite Objekte)
  Verwenden Sie die Seite **Objekte** des Dialogfelds **Editor für den Task 'SQL Server-Objekte übertragen'** , um die Eigenschaften für das Kopieren eines oder mehrerer [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Objekte von einer Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] in eine andere anzugeben. Tabellen, Sichten, gespeicherte Prozeduren und benutzerdefinierte Funktionen sind beispielsweise [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Objekte, die Sie kopieren können. Weitere Informationen zu diesem Task finden Sie unter [Transfer SQL Server Objects Task](control-flow/transfer-sql-server-objects-task.md).  
  
> [!NOTE]  
>  Der Benutzer, der den Task „ [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Objekte übertragen“ erstellt, benötigt die entsprechende Berechtigung, die Quellserverobjekte zum Kopieren auszuwählen, sowie die Berechtigung, auf die Datenbank des Zielservers zuzugreifen, auf den die Objekte übertragen werden.  
  
## <a name="static-options"></a>Statische Optionen  
 **SourceConnection**  
 Wählen Sie in der Liste einen SMO-Verbindungs-Manager aus, oder klicken Sie ** \<auf neue Verbindung... #b0** , um eine neue Verbindung mit dem Quell Server herzustellen.  
  
 **SourceDatabase**  
 Wählen Sie eine Datenbank auf dem Quellserver aus, aus der die Objekte kopiert werden sollen.  
  
 **DestinationConnection**  
 Wählen Sie in der Liste einen SMO-Verbindungs-Manager aus, oder klicken Sie ** \<auf neue Verbindung... #b0** , um eine neue Verbindung mit dem Zielserver zu erstellen.  
  
 **DestinationDatabase**  
 Wählen Sie eine Datenbank auf dem Zielserver aus, auf den die Objekte kopiert werden sollen.  
  
 **Dropobjectfirst**  
 Bestimmen Sie, ob die ausgewählten Objekte vor dem Kopieren zuerst auf dem Zielserver gelöscht werden sollen.  
  
 **Includeextendedproperties**  
 Bestimmen Sie, ob erweiterte Eigenschaften beim Kopieren von Objekten vom Quellserver auf den Zielserver beibehalten werden sollen.  
  
 **CopyData**  
 Bestimmen Sie, ob beim Kopieren von Objekten vom Quellserver auf den Zielserver Daten beinhaltet werden sollen.  
  
 **ExistingData**  
 Bestimmen Sie, wie die Daten auf den Zielserver kopiert werden sollen. Für diese Eigenschaft sind die in der folgenden Tabelle aufgeführten Optionen verfügbar:  
  
|value|BESCHREIBUNG|  
|-----------|-----------------|  
|**Stelle**|Daten auf dem Zielserver werden überschrieben.|  
|**Anfügen**|Die vom Quellserver kopierten Daten werden an die vorhandenen Daten auf dem Zielserver angehängt.|  
  
> [!NOTE]  
>  Die Option **ExistingData** ist nur verfügbar, wenn **CopyData** auf **True**festgelegt ist.  
  
 **CopySchema**  
 Bestimmen Sie, ob mit dem Task „ [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Objekte übertragen“ auch das Schema kopiert werden soll.  
  
> [!NOTE]  
>  **CopySchema** ist nur für [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]verfügbar.  
  
 **Usecollations**  
 Bestimmen Sie, ob die Übertragung von Objekten die auf dem Quellserver angegebene Sortierung beinhalten soll.  
  
 **Include dependentobjects**  
 Bestimmen Sie, ob beim Kopieren auch die kaskadierenden Objekte, die von den für das Kopieren ausgewählten Objekten abhängig sind, kopiert werden sollen.  
  
 **CopyAllObjects**  
 Bestimmen Sie, ob der Task alle Objekte der angegebenen Quelldatenbank oder nur die ausgewählten Objekte kopieren soll.  Wenn Sie diese Option auf False festlegen, haben Sie die Möglichkeit, die zu übertragenden Objekte auszuwählen. Dazu werden dann die dynamischen Optionen des Bereichs **CopyAllObjects**angezeigt.  
  
 **ObjectsToCopy**  
 Erweitern Sie **ObjectsToCopy** , um anzugeben, welche Objekte von der Quelldatenbank in die Zieldatenbank kopiert werden sollen.  
  
> [!NOTE]  
>  **ObjectsToCopy** ist nur verfügbar, wenn **copyzuzujects** auf **false**festgelegt ist.  
  
 Die Optionen zum Kopieren der folgenden Objekttypen werden nur in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]unterstützt:  
  
 Assemblys  
  
 Partitionsfunktionen  
  
 Partitionsschemas  
  
 Schemas  
  
 Benutzerdefinierte Aggregate  
  
 Benutzerdefinierte Typen  
  
 XML-Schemaauflistungen  
  
 **Copydatabaseusers**  
 Geben Sie an, ob die Übertragung Datenbankbenutzer beinhalten soll.  
  
 **Copydatabaseroles**  
 Geben Sie an, ob die Übertragung Datenbankrollen beinhalten soll.  
  
 **Copysqlserverlogins**  
 Geben Sie an, ob die Übertragung [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Anmeldungen beinhalten soll.  
  
 **Copyobjectlevel-Berechtigungen**  
 Geben Sie an, ob die Übertragung Berechtigungen auf Objektebene beinhalten soll.  
  
 **Copyindexes**  
 Geben Sie an, ob die Übertragung Indizes beinhalten soll.  
  
 **Copytriggers**  
 Geben Sie an, ob die Übertragung Trigger beinhalten soll.  
  
 **Copyfulltextindexes**  
 Geben Sie an, ob die Übertragung Volltextindizes beinhalten soll.  
  
 **Copyprimarykeys**  
 Geben Sie an, ob die Übertragung Primärschlüssel beinhalten soll.  
  
 **Copyfremdnkeys**  
 Geben Sie an, ob die Übertragung Fremdschlüssel beinhalten soll.  
  
 **Generatescriptsinunicode**  
 Geben Sie an, ob die generierten Übertragungsskripts das Unicode-Format aufweisen sollen.  
  
## <a name="dynamic-options"></a>Dynamische Optionen  
  
### <a name="copyallobjects--false"></a>CopyAllObjects = False  
 **CopyAllTables**  
 Bestimmen Sie, ob der Task alle Tabellen der angegebenen Quelldatenbank oder nur die ausgewählten Tabellen kopieren soll.  
  
 **TablesList**  
 Klicken Sie auf diese Option, um das Dialogfeld **Tabellen auswählen** zu öffnen.  
  
 **CopyAllViews**  
 Bestimmen Sie, ob der Task alle Sichten der angegebenen Quelldatenbank oder nur die ausgewählten Sichten kopieren soll.  
  
 **Viewslist**  
 Klicken Sie auf diese Option, um das Dialogfeld **Sichten auswählen** zu öffnen.  
  
 **CopyAllStoredProcedures**  
 Bestimmen Sie, ob der Task alle benutzerdefinierten gespeicherten Prozeduren der angegebenen Quelldatenbank oder nur die ausgewählten Prozeduren kopieren soll.  
  
 **StoredProceduresList**  
 Klicken Sie auf diese Option, um das Dialogfeld **Gespeicherte Prozeduren auswählen** zu öffnen.  
  
 **Copyalluserdefinedfunctions**  
 Bestimmen Sie, ob der Task alle benutzerdefinierten Funktionen der angegebenen Quelldatenbank oder nur die ausgewählten benutzerdefinierten Prozeduren kopieren soll.  
  
 **Userdefinedfunctionslist**  
 Klicken Sie auf diese Option, um das Dialogfeld **Benutzerdefinierte Funktionen auswählen** zu öffnen.  
  
 **CopyAllDefaults**  
 Bestimmen Sie, ob der Task alle Standardwerte der angegebenen Quelldatenbank oder nur die ausgewählten Standardwerte kopieren soll.  
  
 **Defaullilist**  
 Klicken Sie auf diese Option, um das Dialogfeld **Standardwerte auswählen** zu öffnen.  
  
 **CopyAllUserDefinedDatatypes**  
 Bestimmen Sie, ob der Task alle benutzerdefinierten Datentypen der angegebenen Quelldatenbank oder nur die ausgewählten benutzerdefinierten Datentypen kopieren soll.  
  
 **Userdefineddatatypeslist**  
 Klicken Sie auf diese Option, um das Dialogfeld **Benutzerdefinierte Datentypen auswählen** zu öffnen.  
  
 **Copyallpartitionfunctions**  
 Bestimmen Sie, ob der Task alle benutzerdefinierten Partitionsfunktionen der angegebenen Quelldatenbank oder nur die ausgewählten Partitionsfunktionen kopieren soll. Dies wird nur in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]unterstützt.  
  
 **Partitionfunctionslist**  
 Klicken Sie auf diese Option, um das Dialogfeld **Partitionsfunktionen auswählen** zu öffnen.  
  
 **Copyallpartitionschemas**  
 Bestimmen Sie, ob der Task alle Partitionsschemas der angegebenen Quelldatenbank oder nur die ausgewählten Partitionsschemas kopieren soll. Dies wird nur in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]unterstützt.  
  
 **Partitionschemeslist**  
 Klicken Sie auf diese Option, um das Dialogfeld **Partitionsschemas auswählen** zu öffnen.  
  
 **Copyallschemas**  
 Bestimmen Sie, ob der Task alle Schemas der angegebenen Quelldatenbank oder nur die ausgewählten Schemas kopieren soll. Dies wird nur in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]unterstützt.  
  
 **Schemaslist**  
 Klicken Sie auf diese Option, um das Dialogfeld **Schemas auswählen** zu öffnen.  
  
 **Copyallsqlassemblys**  
 Bestimmen Sie, ob der Task alle SQL-Assemblys der angegebenen Quelldatenbank oder nur die ausgewählten SQL-Assemblys kopieren soll. Dies wird nur in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]unterstützt.  
  
 **Sqlassemblieslist**  
 Klicken Sie auf diese Option, um das Dialogfeld **Assemblys auswählen** zu öffnen.  
  
 **Copyalluserdefinedaggregate**  
 Bestimmen Sie, ob der Task alle benutzerdefinierten Aggregate der angegebenen Quelldatenbank oder nur die ausgewählten benutzerdefinierten Aggregate kopieren soll. Dies wird nur in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]unterstützt.  
  
 **Userdefinedaggregateslist**  
 Klicken Sie auf diese Option, um das Dialogfeld **Benutzerdefinierte Aggregate** auswählen zu öffnen.  
  
 **Copyalluserdefinedtypes**  
 Bestimmen Sie, ob der Task alle benutzerdefinierten Typen der angegebenen Quelldatenbank oder nur die ausgewählten benutzerdefinierten Datentypen kopieren soll. Dies wird nur in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]unterstützt.  
  
 **UserDefinedTypes**  
 Klicken Sie auf diese Option, um das Dialogfeld **Benutzerdefinierte Typen** auswählen zu öffnen.  
  
 **Copyallxmlschemacollections**  
 Bestimmen Sie, ob der Task alle XML-Schemaauflistungen der angegebenen Quelldatenbank oder nur die ausgewählten XML-Schemaauflistungen kopieren soll. Dies wird nur in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]unterstützt.  
  
 **Xmlschemacollectionslist**  
 Klicken Sie auf diese Option, um das Dialogfeld **XML-Schemaauflistungen** auswählen zu öffnen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Fehler- und Meldungsreferenz von Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Integration Services-Tasks](control-flow/integration-services-tasks.md)   
 [Editor für den Task ' SQL Server Objekte übertragen ' &#40;Seite Allgemein&#41;](general-page-of-integration-services-designers-options.md)   
 [Seite Ausdrücke](expressions/expressions-page.md)   
 [Datenformate für Massen Import oder Massen Export &#40;SQL Server&#41;](../relational-databases/import-export/data-formats-for-bulk-import-or-bulk-export-sql-server.md)   
 [Überlegungen zur Sicherheit bei SQL Server-Installationen](../../2014/sql-server/install/security-considerations-for-a-sql-server-installation.md)  
  
  
