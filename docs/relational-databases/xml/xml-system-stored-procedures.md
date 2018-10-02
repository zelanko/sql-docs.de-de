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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: de9c0bb15963ecfa170c6079a95bfc446cb14f3b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47787768"
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
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [OPENXML &#40;Transact-SQL&#41;](../../t-sql/functions/openxml-transact-sql.md)   
 [OPENXML &#40;SQL Server&#41;](../../relational-databases/xml/openxml-sql-server.md)  
  
  
