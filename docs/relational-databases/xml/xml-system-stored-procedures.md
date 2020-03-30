---
title: Gespeicherte XML-Systemprozeduren | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- system stored procedures [SQL Server], XML
- sp_xml_removedocument
- OPENXML statement, system stored procedures
- sp_xml_preparedocument
- XML [SQL Server], system stored procedures
ms.assetid: e60c7f85-6823-4d28-93d6-b053d08cc830
author: MightyPen
ms.author: genemi
ms.openlocfilehash: b07b7f782c534c7d98e6e20047f58787fe32e8e7
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "67902867"
---
# <a name="xml-system-stored-procedures"></a>Gespeicherte XML-Systemprozeduren
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  SQL Server stellt die folgenden gespeicherten Systemprozeduren zum Verwenden mit OPENXML bereit:  
  
-   [sp_xml_preparedocument &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-xml-preparedocument-transact-sql.md)  
  
-   [sp_xml_removedocument &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-xml-removedocument-transact-sql.md)  
  
 Um Abfragen mithilfe von OPENXML zu schreiben, müssen Sie zunächst eine interne Darstellung des XML-Dokuments erstellen, indem Sie **sp_xml_preparedocument**aufrufen. Die gespeicherte Prozedur gibt ein Handle für die interne Darstellung des XML-Dokuments zurück. Dieses Handle wird dann an OPENXML übergeben. OPENXML stellt auf XPaths basierende Rowsetansichten des Dokuments bereit. Dabei handelt es sich um ein Zeilenmuster und mindestens ein Spaltenmuster.  
  
> [!NOTE]  
>  Das von der **sp_xml_preparedocument** -Prozedur zurückgegebene Dokumenthandle ist für die Dauer der Sitzung gültig.  
  
 Die interne Darstellung eines XML-Dokuments kann durch Aufrufen der gespeicherten Systemprozedur **sp_xml_removedocument** aus dem Arbeitsspeicher gelöscht werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [OPENXML &#40;Transact-SQL&#41;](../../t-sql/functions/openxml-transact-sql.md)   
 [OPENXML &#40;SQL Server&#41;](../../relational-databases/xml/openxml-sql-server.md)  
  
  
