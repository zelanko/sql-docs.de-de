---
title: OLE-Automatisierungsobjekte in Transact-SQL | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: conceptual
helpviewer_keywords:
- triggers [SQL Server], OLE Automation
- batches [SQL Server], OLE Automation
- OLE Automation [SQL Server]
- OLE Automation [SQL Server], about OLE Automation
ms.assetid: a887d956-4cd0-400a-aa96-00d7abd7c44b
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 06913c27af89657aef5a0a5397cd77a1ee025299
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48075792"
---
# <a name="ole-automation-objects-in-transact-sql"></a>OLE-Automatisierungsobjekte in Transact-SQL
  [!INCLUDE[tsql](../../includes/tsql-md.md)] enthält mehrere gespeicherte Systemprozeduren, die Verweise auf OLE-Automatisierungsobjekte in [!INCLUDE[tsql](../../includes/tsql-md.md)] -Batches, gespeicherten Prozeduren und Triggern ermöglichen. Diese gespeicherten Systemprozeduren werden als erweiterte gespeicherte Prozeduren ausgeführt, und die OLE-Automatisierungsobjekte, die über die gespeicherten Prozeduren ausgeführt werden, werden wie eine erweiterte gespeicherte Prozedur im Adressraum einer Instanz von [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] ausgeführt.  
  
 Die gespeicherten OLE-Automatisierungsprozeduren ermöglichen es [!INCLUDE[tsql](../../includes/tsql-md.md)] -Batches, auf SQL-DMO-Objekte und benutzerdefinierte OLE-Automatisierungsobjekte zu verweisen, wie etwa Objekte, die die **IDispatch** -Schnittstelle verfügbar machen. Ein benutzerdefinierter In-Process-OLE-Server, der mithilfe von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] erstellt wurde, muss mit einem (mit der **On Error GoTo** -Anweisung angegebenen) Fehlerhundler für die Unterroutinen **Class_Initialize** und **Class_Terminate** ausgestattet sein. Nicht behandelte Fehler in den Unterroutinen **Class_Initialize** und **Class_Terminate** können unvorhersehbare Fehler verursachen, wie z.B. eine Zugriffsverletzungen in einer Instanz von [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Fehlerhandler werden auch für andere Unterroutinen empfohlen.  
  
 Der erste Schritt beim Verwenden eines OLE-Automatisierungsobjekts in [!INCLUDE[tsql](../../includes/tsql-md.md)] ist das Aufrufen der gespeicherten Systemprozedur **sp_OACreate** , um eine Instanz des Objekts im Adressraum der Instanz von [!INCLUDE[ssDE](../../includes/ssde-md.md)]zu erstellen.  
  
 Verwenden Sie nach dem Erstellen einer Instanz des Objekts die folgenden gespeicherten Prozeduren, um mit den Eigenschaften, Methoden und Fehlerinformationen im Zusammenhang mit dem Objekt zu arbeiten:  
  
-   **sp_OAGetProperty** ruft den Wert einer Eigenschaft ab.  
  
-   **sp_OASetProperty** legt den Wert einer Eigenschaft fest.  
  
-   **sp_OAMethod** ruft eine Methode auf.  
  
-   **sp_OAGetErrorInfo** ruft die letzten Fehlerinformationen ab.  
  
 Wenn das Objekt nicht mehr benötigt wird, rufen Sie **sp_OADestroy** auf, um die Zuordnung der mit **sp_OACreate**erstellten Instanz des Objekts aufzuheben.  
  
 OLE-Automatisierungsobjekte geben Daten durch Eigenschaftswerte und Methoden zurück. **sp_OAGetProperty** und **sp_OAMethod** geben diese Datenwerte als Resultset zurück.  
  
 Der Gültigkeitsbereich eines OLE-Automatisierungsobjekts ist ein Batch. Alle Verweise auf das Objekt müssen in einem einzelnen Batch, einer gespeicherten Prozedur oder einem Trigger enthalten sein.  
  
 Beim Verweisen auf Objekte unterstützen die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -OLE-Automatisierungsobjekte das Traversieren des Objekts, auf das verwiesen wird, auf andere Objekte, die es enthält. Wenn beispielsweise das SQL-DMO-Objekt **SQLServer** verwendet wird, können Verweise auf Datenbanken und Tabellen erfolgen, die sich auf dem betreffenden Server befinden.  
  
## <a name="related-content"></a>Verwandte Inhalte  
 [Objekthierarchiesyntax &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/object-hierarchy-syntax-transact-sql)  
  
 [Oberflächenkonfiguration](../security/surface-area-configuration.md)  
  
 [OLE-Automatisierungsprozeduren (Serverkonfigurationsoption)](../../database-engine/configure-windows/ole-automation-procedures-server-configuration-option.md)  
  
 [sp_OACreate &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-oacreate-transact-sql)  
  
 [sp_OAGetProperty &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-oagetproperty-transact-sql)  
  
 [sp_OASetProperty &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-oasetproperty-transact-sql)  
  
 [sp_OAMethod &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-oamethod-transact-sql)  
  
 [sp_OAGetErrorInfo &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-oageterrorinfo-transact-sql)  
  
 [sp_OADestroy &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-oadestroy-transact-sql)  
  
  
