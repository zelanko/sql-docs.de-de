---
title: CREATE WORKLOAD CLASSIFIER (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/13/2019
ms.prod: sql
ms.prod_service: sql-data-warehouse
ms.reviewer: jrasnick
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- WORKLOAD CLASSIFIER
- WORKLOAD_CLASSIFIER_TSQL
- CREATE WORKLOAD CLASSIFIER
- CREATE_WORKLOAD_CLASSIFIER_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- CREATE WORKLOAD CLASSIFIER statement
ms.assetid: ''
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: =azure-sqldw-latest||=sqlallproducts-allversions
ms.openlocfilehash: dd10a628e5a60487ceaf11a6dd39f781fbc41596
ms.sourcegitcommit: 46a2c0ffd0a6d996a3afd19a58d2a8f4b55f93de
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/15/2019
ms.locfileid: "59581214"
---
# <a name="create-workload-classifier-transact-sql-preview"></a>CREATE WORKLOAD CLASSIFIER (Transact-SQL) (Vorschauversion)

> [!Note]
> Die Klassifizierung von Workloads ist in der Vorschauversion für SQL Data Warehouse Gen2 verfügbar. Die Klassifizierung für die Workloadverwaltung und Workloadpriorität (Vorschauversion) ist für Builds mit einem Veröffentlichungsdatum ab dem 09. April 2019 verfügbar.  Builds mit einem früheren Veröffentlichungsdatum sollten nicht für das Testen der Workloadverwaltung verwendet werden.  Um zu bestimmen, ob Ihr Build die Workloadverwaltung unterstützt, führen Sie, sobald Sie mit Ihrer SQL Data Warehouse-Instanz verbunden sind, select @@version aus.

[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md.md)]

Erstellt einen Arbeitsauslastungsverwaltungsklassifizierer.  Der Klassifizierer weist eingehende Anforderungen einer Arbeitsauslastungsgruppe zu und weist Prioritäten auf Grundlage der Parameter zu, die in der Definition der Klassifiziereranweisung angegeben sind.  Klassifizierer werden bei jeder eingereichten Anforderung ausgewertet.  Wenn eine Anforderung nicht einem Klassifizierer zugeordnet werden kann, wird sie der Standardarbeitsauslastungsgruppe zugeordnet.  Die Standardarbeitsauslastungsgruppe ist die Ressourcenklasse „smallrc“.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md).  
  
## <a name="syntax"></a>Syntax

```
CREATE WORKLOAD CLASSIFIER classifier_name  
WITH  
    ( WORKLOAD_GROUP = 'name'  
     ,MEMBERNAME = 'security_account'
 [ [ , ] IMPORTANCE = { LOW | BELOW_NORMAL | NORMAL (default) | ABOVE_NORMAL | HIGH }])
[;]
```

## <a name="arguments"></a>Argumente

 *classifier_name*  
 Gibt den Namen an, mit dem der Arbeitsauslastungsklassifizierer identifiziert werden kann.  „classifier_name“ ist vom Datentyp „sysname“.  Dieses Argument kann bis zu 128 Zeichen lang sein und muss innerhalb der Instanz einen eindeutigen Namen haben.

WORKLOAD_GROUP = *'name'* Wenn die Klassifiziererregeln die Bedingungen erfüllen, ordnet „name“ die Anforderung einer Arbeitsauslastungsgruppe zu.  „name“ ist vom Datentyp „sysname“.  Es kann bis zu 128 Zeichen lang sein und muss zum Zeitpunkt der Erstellung des Klassifizierers ein gültiger Arbeitsauslastungsgruppenname sein.

WORKLOAD_GROUP sollte einer vorhandenen Ressourcenklasse zugeordnet werden:

|Statische Ressourcenklassen|Dynamische Ressourcenklassen|
|------------------------|-----------------------|
|staticrc10|smallrc|
|staticrc20|mediumrc|
|staticrc30|largerc|
|staticrc40|xlargerc|
|staticrc50||
|staticrc60||
|staticrc70||
|staticrc80||

MEMBERNAME = *'security_account'* Dies ist das Sicherheitskonto, das der Rolle hinzugefügt wird.  „Security_account“ ist vom Datentyp „sysname“und hat keinen Standardwert. „Security_account“ kann ein Datenbankbenutzer, eine Datenbankrolle, eine Azure Active Directory-Anmeldung oder eine Azure Active Directory-Gruppe sein.

IMPORTANCE = { LOW | BELOW_NORMAL | NORMAL | ABOVE_NORMAL | HIGH } Gibt die relative Priorität einer Anforderung an.  Die Wichtigkeit kann einen der folgenden Werte aufweisen:

- LOW
- BELOW_NORMAL
- NORMAL (Standard)
- ABOVE_NORMAL
- HIGH  

Die Priorität beeinflusst die Reihenfolge, in der Anforderungen geplant werden und somit zuerst Zugriff auf Ressourcen und Sperren erhalten.

Wenn ein Benutzer Mitglied mehrerer Rollen mit verschiedenen zugewiesenen Ressourcenklassen oder Übereinstimmungen in mehreren Klassifizierern ist, wird dem Benutzer die höchste Ressourcenklasse zugewiesen. Weitere Informationen finden Sie unter [workload classification (Workloadklassifizierung)](/azure/sql-data-warehouse/sql-data-warehouse-workload-classification#classification-precedence).

## <a name="permissions"></a>Berechtigungen

 Erfordert die CONTROL DATABASE-Berechtigung.  
  
## <a name="examples"></a>Beispiele

 Das folgende Beispiel zeigt, wie ein Arbeitsauslastungsklassifizierer mit dem Namen `wgcELTRole` erstellt wird. Dieser verwendet die Arbeitsauslastungsgruppe „staticrc20“, den Benutzer `ELTRole` und legt die Priorität auf `above_normal` fest.

```sql
CREATE WORKLOAD CLASSIFIER wgcELTRole
  WITH (WORKLOAD_GROUP = 'staticrc20'
       ,MEMBERNAME = 'ELTRole'
      ,IMPORTANCE = above_normal);
```

## <a name="see-also"></a>Weitere Informationen

[DROP WORKLOAD CLASSIFIER &#40;Transact-SQL&#41;](../../t-sql/statements/drop-workload-classifier-transact-sql.md)</br>
Katalogsicht [sys.workload_management_workload_classifier_details](../../relational-databases/system-catalog-views/sys-workload-management-workload-classifier-details-transact-sql.md)</br>
Katalogsicht [sys.workload_management_workload_classifiers](../../relational-databases/system-catalog-views/sys-workload-management-workload-classifiers-transact-sql.md)
[SQL Data Warehouse Classification (SQL Data Warehouse-Klassifizierung)](/azure/sql-data-warehouse/classification)
