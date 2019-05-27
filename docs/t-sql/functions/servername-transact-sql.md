---
title: '@@SERVERNAME (Transact-SQL) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 09/07/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- '@@SERVERNAME'
- '@@SERVERNAME_TSQL'
dev_langs:
- TSQL
helpviewer_keywords:
- '@@SERVERNAME function'
- local servers [SQL Server]
ms.assetid: b0ef33fb-954a-4294-b05b-a87c14ce25a3
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 529938ad7f9bd5d38ea9944fc67027588a80407a
ms.sourcegitcommit: 83f061304fedbc2801d8d6a44094ccda97fdb576
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/20/2019
ms.locfileid: "65945284"
---
# <a name="x40x40servername-transact-sql"></a>&#x40;&#x40;SERVERNAME (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Gibt den Namen des lokalen Servers zurück, auf dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgeführt wird.  
 ![Artikellinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
@@SERVERNAME  
```  
  
## <a name="return-types"></a>Rückgabetypen  
 **nvarchar**  
  
## <a name="remarks"></a>Remarks  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup legt den Servernamen während der Installation auf den Computernamen fest. Verwenden Sie zum Ändern des Namens des Servers **sp_addserver**, und starten Sie dann [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] neu.  
  
 Wenn mehrere Instanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installiert sind, gibt @@SERVERNAME die folgenden Informationen zum Namen des lokalen Servers zurück, wenn der Name des lokalen Servers seit der Installation nicht geändert wurde:  
  
|Instanz|Serverinformationen|  
|--------------|------------------------|  
|Standardinstanz|'*servername*'|  
|Benannte Instanz|'*servername*\\*instancename*'|  
|Failoverclusterinstanz – Standardinstanz|'*Netzwerkname_für_fci_in_wsfc*'|  
|Failoverclusterinstanz – benannte Instanz|'*Netzwerkname_für_fci_in_wsfc*\\*Instanzname*'|  
  
 Obwohl die @@SERVERNAME-Funktion und die SERVERNAME-Eigenschaft der SERVERPROPERTY-Funktion möglicherweise Zeichenfolgen mit ähnlichen Formaten zurückgeben, kann die Information abweichen. Die SERVERNAME-Eigenschaft meldet Änderungen des Netzwerknamens des Computers automatisch.  
  
 @@SERVERNAME meldet diese Änderungen hingegen nicht. @@SERVERNAME meldet mithilfe der gespeicherten Prozeduren **sp_addserver** oder **sp_dropserver** Änderungen des Namens des lokalen Servers.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird die Verwendung von `@@SERVERNAME` gezeigt.  
  
```  
SELECT @@SERVERNAME AS 'Server Name'  
```  
  
 Hier ist ein Beispielresultset.  
  
```  
Server Name  
---------------------------------  
ACCTG  
  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Konfigurationsfunktionen (Transact-SQL)](../../t-sql/functions/configuration-functions-transact-sql.md)   
 [SERVERPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/serverproperty-transact-sql.md)   
 [sp_addserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addserver-transact-sql.md)  
  
  
