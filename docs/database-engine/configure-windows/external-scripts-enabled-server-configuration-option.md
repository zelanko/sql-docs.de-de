---
title: Externe Skripts aktiviert (Serverkonfigurationsoption) | Microsoft-Dokumentation
ms.date: 11/13/2017
ms.prod: sql
ms.technology: configuration
ms.reviewer: ''
ms.topic: language-reference
f1_keywords:
- external scripts enabled
- external_scripts_enabled_TSQL
helpviewer_keywords:
- external scripts enabled option
ms.assetid: 9d0ce165-8719-4007-9ae8-00f85cab3a0d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3f47352cc82ac831ebcd64548baa24423490094f
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "72006047"
---
# <a name="external-scripts-enabled-server-configuration-option"></a>Externe Skripts aktiviert – Serverkonfigurationsoption
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
**Gilt für:** [!INCLUDE[sssql15-md](../../includes/sssql15-md.md)] [!INCLUDE[rsql-productname-md](../../includes/rsql-productname-md.md)] und [!INCLUDE[sssql17-md](../../includes/sssql17-md.md)] [!INCLUDE[rsql-productnamenew-md](../../includes/rsql-productnamenew-md.md)]

Aktivieren Sie mit der Option **external scripts enabled** die Ausführung von Skripts mit bestimmten Remotespracherweiterungen. Diese Eigenschaft ist standardmäßig deaktiviert. Beim Setup kann diese Eigenschaft optional auf TRUE festgelegt werden, wenn **Advanced Analytics Services** installiert wird.

## <a name="remarks"></a>Bemerkungen

Bevor Sie mit der gespeicherten Prozedur [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) ein externes Skript ausführen können, müssen Sie die Option „external script enabled“ aktivieren. Verwenden Sie **sp_execute_external_script** zum Ausführen von Skripts, die in einer unterstützten Sprache wie R oder Python geschrieben sind. 

+ Für [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]

    [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] bietet Unterstützung für die Sprache R in [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] und einen Satz von R-Arbeitsstationstools und -Verbindungsbibliotheken.

    Installieren Sie das Feature **Advanced Analytics-Erweiterungen** während des Setups von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , um die Ausführung von R-Skripts zu ermöglichen. Die Sprache R wird standardmäßig installiert.

+ Für [!INCLUDE[sssql17-md](../../includes/sssql17-md.md)]

    [!INCLUDE[rsql-productnamenew-md](../../includes/rsql-productnamenew-md.md)] verwendet die gleiche Architektur wie in SQL Server 2016, bietet jedoch Unterstützung für die Sprache Python.

    Installieren Sie das Feature **Advanced Analytics-Erweiterungen** während des Setups von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], um die Ausführung externer Skripts zu ermöglichen. Achten Sie darauf, dass Sie während der ersten Installation mindestens eine Sprache auswählen: R oder Python oder beides. 

## <a name="additional-requirements"></a>Zusätzliche Anforderungen

Führen Sie nach der Installation das folgende Skript aus, um externe Skripts zu aktivieren:

```sql
sp_configure 'external scripts enabled', 1;
RECONFIGURE WITH OVERRIDE;  
```

Starten Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] neu, damit diese Änderung wirksam wird.

Weitere Informationen finden Sie unter [Einrichten von SQL Server Machine Learning-Services (Datenbankintern)](../../advanced-analytics/r/set-up-sql-server-r-services-in-database.md).

## <a name="see-also"></a>Weitere Informationen

[sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)

[RECONFIGURE &#40;Transact-SQL&#41;](../../t-sql/language-elements/reconfigure-transact-sql.md)

[sp_execute_external_script &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)

[SQL Server Machine Learning Services](../../advanced-analytics/r/sql-server-r-services.md)
