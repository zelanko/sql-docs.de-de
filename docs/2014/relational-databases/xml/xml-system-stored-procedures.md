---
title: Gespeicherte XML-Systemprozeduren | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
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
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 40d195d01cca04753b9ce8798be7de514de9620c
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/01/2020
ms.locfileid: "82702229"
---
# <a name="xml-system-stored-procedures"></a>Gespeicherte XML-Systemprozeduren
  SQL Server stellt die folgenden gespeicherten Systemprozeduren zum Verwenden mit OPENXML bereit:  
  
-   [sp_xml_preparedocument &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-xml-preparedocument-transact-sql)  
  
-   [sp_xml_removedocument &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-xml-removedocument-transact-sql)  
  
 Um Abfragen mithilfe von OPENXML zu schreiben, müssen Sie zunächst eine interne Darstellung des XML-Dokuments erstellen, indem Sie **sp_xml_preparedocument**aufrufen. Die gespeicherte Prozedur gibt ein Handle für die interne Darstellung des XML-Dokuments zurück. Dieses Handle wird dann an OPENXML übergeben. OPENXML stellt auf XPaths basierende Rowsetansichten des Dokuments bereit. Dabei handelt es sich um ein Zeilenmuster und mindestens ein Spaltenmuster.  
  
> [!NOTE]  
>  Das von der **sp_xml_preparedocument** -Prozedur zurückgegebene Dokumenthandle ist für die Dauer der Sitzung gültig.  
  
 Die interne Darstellung eines XML-Dokuments kann durch Aufrufen der gespeicherten Systemprozedur **sp_xml_removedocument** aus dem Arbeitsspeicher gelöscht werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [OPENXML &#40;Transact-SQL&#41;](/sql/t-sql/functions/openxml-transact-sql)   
 [OPENXML &#40;SQL Server&#41;](../xml/openxml-sql-server.md)  
  
  
