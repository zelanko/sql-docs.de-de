---
title: IHextendedArticleView (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- IHextendedArticleView_TSQL
- IHextendedArticleView
dev_langs:
- TSQL
helpviewer_keywords:
- IHextendedArticleView view
ms.assetid: 19ef0a12-3214-4bb0-9c25-a665897e65a2
author: stevestein
ms.author: sstein
ms.openlocfilehash: e15bb478ba04a95fa3c4d358477fe8073f50d007
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85889213"
---
# <a name="ihextendedarticleview-transact-sql"></a>IHextendedArticleView (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Die **IHextendedArticleView** -Sicht macht Informationen zu Artikeln in einer Nicht-SQL Server-Veröffentlichung verfügbar. Diese Sicht wird in der **Verteilungs** Datenbank gespeichert.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**publisher_id**|**smallint**|Der eindeutige Bezeichner des Verlegers.|  
|**publication_id**|**int**|Der eindeutige Bezeichner der Veröffentlichung.|  
|**Artikel**|**sysname**|Der Name des Artikels.|  
|**destination_object**|**sysname**|Der Name des veröffentlichten Objekts auf dem Abonnenten.|  
|**source_owner**|**sysname**|Der Besitzer des veröffentlichten Objekts auf dem Verleger.|  
|**source_object**|**sysname**|Der Name des veröffentlichten Objekts auf dem Verleger.|  
|**description**|**nvarchar(255)**|Die Beschreibung des Artikels.|  
|**creation_script**|**nvarchar(255)**|Das Schemaerstellungsskript für den Artikel|  
|**del_cmd**|**nvarchar(255)**|Der für eine DELETE-Anweisung ausgeführte Befehl.|  
|**filter**|**int**|Der Bezeichner für die gespeicherte Prozedur, die die horizontale Partition definiert.|  
|**filter_clause**|**ntext**|Die zum horizontalen Filtern des Artikels verwendete WHERE-Klausel.|  
|**ins_cmd**|**nvarchar(255)**|Der für eine INSERT-Anweisung ausgeführte Befehl.|  
|**pre_creation_cmd**|**tinyint**|Der Vorabbefehl für DROP TABLE, DELETE TABLE oder TRUNCATE:<br /><br /> **0** = keine.<br /><br /> **1** = DROP.<br /><br /> **2** = DELETE.<br /><br /> **3** = TRUNCATE.|  
|**status**|**tinyint**|Die Bitmaske der Artikeloptionen und der Status, die das Ergebnis des bitweisen logischen OR von mindestens einem der folgenden Werte sein können:<br /><br /> **1** = Artikel ist aktiv.<br /><br /> **8** = Den Spaltennamen in INSERT-Anweisungen einschließen.<br /><br /> **16** = Parametrisierte Anweisungen verwenden.<br /><br /> **24** = Sowohl den Spaltennamen in INSERT-Anweisungen einschließen als auch parametrisierte Anweisungen verwenden.<br /><br /> Ein aktiver Artikel, der parametrisierte Anweisungen verwendet, würde in dieser Spalte beispielsweise den Wert **17** aufweisen. Der Wert **0** bedeutet, dass der Artikel inaktiv ist und keine zusätzlichen Eigenschaften definiert sind.|  
|**type**|**tinyint**|Artikeltyp:<br /><br /> **1** = Protokollbasierter Artikel.<br /><br /> **3** = Protokollbasierter Artikel mit manuell erstelltem Filter.<br /><br /> **5** = Protokollbasierter Artikel mit manuell erstellter Sicht.<br /><br /> **7** = Protokollbasierter Artikel mit manuell erstelltem Filter und manuell erstellter Sicht.|  
|**upd_cmd**|**nvarchar(255)**|Der für eine UPDATE-Anweisung ausgeführte Befehl.|  
|**schema_option**|**binary**|Gibt an, wofür ein Skript erstellt werden soll. Eine Liste der unterstützten Schema Optionen finden Sie unter [sp_addarticle &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md) .|  
|**dest_owner**|**sysname**|Der Besitzer des veröffentlichten Objekts in der Zieldatenbank.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Heterogene Replikation](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [Replikations Tabellen &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Replikationssichten &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
