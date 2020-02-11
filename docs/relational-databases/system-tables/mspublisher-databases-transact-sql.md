---
title: MSpublisher_databases (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSpublisher_databases
- MSpublisher_databases_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSpublisher_databases system table
ms.assetid: 59b0166e-a64c-46b8-befc-c222fa1ccce2
author: stevestein
ms.author: sstein
ms.openlocfilehash: da208c7fb83053c1817693bb16d16c3488fe90c8
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68032610"
---
# <a name="mspublisher_databases-transact-sql"></a>MSpublisher_databases (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Die **MSpublisher_databases** Tabelle enthält eine Zeile für jedes vom lokalen Verteiler verarbeitete Verleger-/Herausgeber-Daten Bank Paar. Diese Tabelle wird in der Verteilungsdatenbank gespeichert.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**publisher_id**|**smallint**|Die ID des Verlegers|  
|**publisher_db**|**sysname**|Der Name der Verlegerdatenbank.|  
|**Name**|**int**|Die ID der Zeile.|  
|**publisher_engine_edition**|**int**|Die Edition des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Verlegers. Diese kann einen der folgenden Werte annehmen:<br /><br /> **10** = Personal Edition<br /><br /> **11** = Desktop-Engine (MSDE)<br /><br /> **20** = Standard<br /><br /> **21** = Arbeitsgruppe<br /><br /> **30** = Enterprise (Evaluation)<br /><br /> **31** = Entwickler<br /><br /> **40** = Express (Express darf kein Verleger sein. Dieser Wert ist der Vollständigkeit halber angegeben.)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Replikationstabellen &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)  
  
  
