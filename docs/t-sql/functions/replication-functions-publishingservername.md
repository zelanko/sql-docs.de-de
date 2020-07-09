---
title: PUBLISHINGSERVERNAME (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- PUBLISHINGSERVERNAME_TSQL
- PUBLISHINGSERVERNAME
dev_langs:
- TSQL
helpviewer_keywords:
- PUBLISHINGSERVERNAME function
- Publishers [SQL Server replication], names
ms.assetid: e7c278e5-ab23-419e-ab3e-3bb20b0636df
author: julieMSFT
ms.author: jrasnick
ms.openlocfilehash: 586dd6e2315e5041b8aebda601d8200030717b0a
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85899148"
---
# <a name="replication-functions---publishingservername"></a>Replikationsfunktionen: PUBLISHINGSERVERNAME
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Gibt den Namen des ursprünglichen Verlegers für eine veröffentlichte Datenbank zurück, die an einer Datenbank-Spiegelungssitzung teilnimmt. Diese Funktion wird auf einer Verlegerinstanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] für die Veröffentlichungsdatenbank ausgeführt. Hiermit bestimmen Sie den ursprünglichen Verleger der veröffentlichten Datenbank.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
PUBLISHINGSERVERNAME()  
```  
  
## <a name="return-types"></a>Rückgabetypen  
 **nvarchar**  
  
## <a name="remarks"></a>Bemerkungen  
 PUBLISHINGSERVERNAME wird für alle Replikationstypen verwendet.  
  
 PUBLISHINGSERVERNAME wird verwendet, wenn eine Datenbank-Spiegelungssitzung für die Veröffentlichungsdatenbank zwischen dem Verleger und einer Spiegelungspartnerinstanz vorhanden ist.  
  
 Diese Funktion muss im Kontext einer Veröffentlichungsdatenbank ausgeführt werden. Wenn PUBLISHINGSERVERNAME für eine Veröffentlichungsdatenbank auf der Spiegelserverinstanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgeführt wird, wird der Name der Verlegerinstanz, von der die veröffentlichte Datenbank stammt, zurückgegeben. Wenn diese Funktion für eine Datenbank auf der Spiegelserverinstanz ausgeführt wird, die nicht veröffentlicht ist oder die von der Spiegelserverinstanz nach einem Failover veröffentlicht wird, wird der Name der Spiegelserverinstanz zurückgegeben. Wenn diese Funktion auf der ursprünglichen Verlegerinstanz ausgeführt wird, wird der Name des Verlegers zurückgegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenbankspiegelung und Replikation (SQL Server)](../../database-engine/database-mirroring/database-mirroring-and-replication-sql-server.md)   
 [Replikationsfunktionen &#40;Transact-SQL&#41;](https://msdn.microsoft.com/library/53702dee-de58-47d5-a552-7f32000f77d4)  
  
  
