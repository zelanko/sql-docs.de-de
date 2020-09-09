---
description: sp_xml_removedocument (Transact-SQL)
title: sp_xml_removedocument (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_xml_removedocument_TSQL
- sp_xml_removedocument
dev_langs:
- TSQL
helpviewer_keywords:
- sp_xml_removedocument
ms.assetid: f9dca50a-8baf-4170-90bc-e72783ce5b73
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 2ffb8f5fab2949538fcb2f8d976df2ff6b721f44
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89542992"
---
# <a name="sp_xml_removedocument-transact-sql"></a>sp_xml_removedocument (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Entfernt die interne Darstellung des XML-Dokuments, das durch das Dokumenthandle angegeben wird, und erklärt das Dokumenthandle für ungültig.  
  
> [!NOTE]  
>  Ein analysiertes Dokument wird im internen Cache von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gespeichert. Der MSXML-Parser (Msxmlsql.dll) verwendet ein Achtel des gesamten für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verfügbaren Arbeitsspeichers. Führen Sie **sp_xml_removedocument** aus, um den Arbeitsspeicher freizugeben.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_xml_removedocument hdoc  
```  
  
## <a name="arguments"></a>Argumente  
 *hdoc*  
 Das Handle für das gerade erstellte Dokument. Wenn das Handle ungültig ist, wird ein Fehler zurückgegeben. *HDOC* ist eine ganze Zahl.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder >0 (Fehler)  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der **public** -Rolle.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird die interne Darstellung eines XML-Dokuments entfernt. Das Handle für das Dokument wird als Eingabe bereitgestellt.  
  
```  
EXEC sp_xml_removedocument @hdoc;  
```  
  
## <a name="see-also"></a>Weitere Informationen      
 <br>[Gespeicherte System Prozeduren (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)
 <br>[Gespeicherte XML-Prozeduren (Transact-SQL)](../../relational-databases/system-stored-procedures/xml-stored-procedures-transact-sql.md)
 <br>[sys. dm_exec_xml_handles (Transact-SQL)](../system-dynamic-management-views/sys-dm-exec-xml-handles-transact-sql.md)
 <br>[sp_xml_preparedocument (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-xml-preparedocument-transact-sql.md)
 <br>[OPENXML (Transact-SQL)](../../t-sql/functions/openxml-transact-sql.md)
  
  
