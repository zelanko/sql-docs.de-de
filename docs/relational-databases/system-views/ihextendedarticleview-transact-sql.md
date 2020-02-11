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
ms.openlocfilehash: 0abca8ca826ec986a9cbf71f4fb577291e095e39
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68029543"
---
# <a name="ihextendedarticleview-transact-sql"></a>IHextendedArticleView (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Die **IHextendedArticleView** -Sicht macht Informationen zu Artikeln in einer Nicht-SQL Server-Veröffentlichung verfügbar. Diese Sicht wird in der **Verteilungs** Datenbank gespeichert.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**publisher_id**|**smallint**|Der eindeutige Bezeichner des Verlegers.|  
|**publication_id**|**int**|Der eindeutige Bezeichner der Veröffentlichung.|  
|**Artikel**|**sysname**|Der Name des Artikels.|  
|**destination_object**|**sysname**|Der Name des veröffentlichten Objekts auf dem Abonnenten.|  
|**source_owner**|**sysname**|Der Besitzer des veröffentlichten Objekts auf dem Verleger.|  
|**source_object**|**sysname**|Der Name des veröffentlichten Objekts auf dem Verleger.|  
|**Beschreibung**|**nvarchar(255)**|Die Beschreibung des Artikels.|  
|**creation_script**|**nvarchar(255)**|Das Schemaerstellungsskript für den Artikel|  
|**del_cmd**|**nvarchar(255)**|Der für eine DELETE-Anweisung ausgeführte Befehl.|  
|**Filter**|**int**|Der Bezeichner für die gespeicherte Prozedur, die die horizontale Partition definiert.|  
|**filter_clause**|**ntext**|Die zum horizontalen Filtern des Artikels verwendete WHERE-Klausel.|  
|**ins_cmd**|**nvarchar(255)**|Der für eine INSERT-Anweisung ausgeführte Befehl.|  
|**pre_creation_cmd**|**tinyint**|Der Vorabbefehl für DROP TABLE, DELETE TABLE oder TRUNCATE:<br /><br /> **0** = keine.<br /><br /> **1** = Drop.<br /><br /> **2** = löschen.<br /><br /> **3** = abschneiden.|  
|**Stands**|**tinyint**|Die Bitmaske der Artikeloptionen und der Status, die das Ergebnis des bitweisen logischen OR von mindestens einem der folgenden Werte sein können:<br /><br /> **1** = Artikel ist aktiv.<br /><br /> **8** = schließen Sie den Spaltennamen in INSERT-Anweisungen ein.<br /><br /> **16** = parametrisierte Anweisungen verwenden.<br /><br /> **24** = beide enthalten den Spaltennamen in INSERT-Anweisungen und verwenden parametrisierte Anweisungen.<br /><br /> Ein aktiver Artikel, der parametrisierte Anweisungen verwendet, würde in dieser Spalte beispielsweise den Wert **17** aufweisen. Der Wert **0** bedeutet, dass der Artikel inaktiv ist und keine zusätzlichen Eigenschaften definiert sind.|  
|**type**|**tinyint**|Artikeltyp:<br /><br /> **1** = Protokoll basierter Artikel.<br /><br /> **3** = Protokoll basierter Artikel mit manuellem Filter.<br /><br /> **5** = Protokoll basierter Artikel mit manueller Sicht.<br /><br /> **7** = Protokoll basierter Artikel mit manuellem Filter und manueller Ansicht.|  
|**upd_cmd**|**nvarchar(255)**|Der für eine UPDATE-Anweisung ausgeführte Befehl.|  
|**schema_option**|**BINARY**|Gibt an, wofür ein Skript erstellt werden soll. Eine Liste der unterstützten Schema Optionen finden Sie unter [sp_addarticle &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md) .|  
|**dest_owner**|**sysname**|Der Besitzer des veröffentlichten Objekts in der Zieldatenbank.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Heterogene Datenbankreplikation](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [Replikations Tabellen &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Replikationssichten &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
