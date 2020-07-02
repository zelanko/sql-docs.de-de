---
title: sp_prepexecrpc (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/02/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_cursor_prepexecrpc
- sp_cursor_prepexecrpc_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_prepexecrpc
ms.assetid: 35d686f2-ef31-4eaa-baa9-9cef5d6c87c2
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: f35bd49fa9969d0d5f381d5e1cb7f905b9a0743b
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85760040"
---
# <a name="sp_prepexecrpc-transact-sql"></a>sp_prepexecrpc (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Bereitet einen Aufruf einer parametrisierten, mithilfe eines RPC-Bezeichners angegebenen gespeicherten Prozedur vor und führt sie aus. sp_prepexecrpc wird von ID = 14 in einem Tabular Data Stream-Paket (TDS) aufgerufen.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_prepexecrpc handle OUTPUT, RPCCall  
    [ , bound_param ] [ ,...n]]  
```  
  
## <a name="arguments"></a>Argumente  
 *bewältigen*  
 Der von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]generierte, vorbereitete Handlebezeichner. *handle* ist ein erforderlicher Parameter mit einem **int** -Rückgabewert.  
  
 *RPCCall*  
 Definiert den Aufruf für die gespeicherte Prozedur mit kanonischer ODBC-Syntax. *RPCCall* ist ein erforderlicher Parameter, der einen Eingabewert für eine **ntext** -Zeichenfolge erfordert.  
  
 *bound_param*  
 Gibt die optionale Verwendung zusätzlicher Parameter an. *bound_param* erfordert einen Eingabewert eines beliebigen Datentyps, um die zusätzlichen verwendeten Parameter festzulegen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
