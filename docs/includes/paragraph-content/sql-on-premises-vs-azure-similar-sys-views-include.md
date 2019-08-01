---
ms.openlocfilehash: 6fd7bb2b8be38becc87c4dc8cb353594459a8dd6
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68220164"
---

<!--
### Code examples for Azure cloud differ slightly from on-premises
  Or.....
### Code examples can differ for Azure SQL Database
-->

Einige Transact-SQL-Codebeispiele, die für lokale SQL Server-Instanzen geschrieben wurden, müssen leicht abgeändert werden, damit sie in Azure SQL-Datenbank in der Cloud ausgeführt werden können. Eine Kategorie solcher Codebeispiele umfasst Systemsichten, deren Namenspräfixe sich zwischen den beiden Datenbanksystemen leicht unterscheiden:

- **server\_** &nbsp; - &nbsp; _Präfix für lokale Instanz_
- **database\_** &nbsp; - &nbsp; _Präfix für Azure SQL-Datenbank in der Cloud_

Zur Veranschaulichung werden in der folgenden Tabelle zwei Teilmengen der Systemsichten aufgelistet und verglichen. Aus Platzgründen dürfen die Teilmengen nur Namen anzeigen, die ebenfalls die Zeichenfolge `_event` enthalten. Die Namenspräfixe der Teilmengen unterscheiden sich, da sie aus zwei unterschiedlichen Datenbanksystemen stammen.

| Name aus der lokalen 2017-Instanz | Name aus dem Clouddienst |
| :------------------------- | :---------------------- |
| server_event_notifications<br />server_event_session_actions<br />server_event_session_events<br />server_event_session_fields<br />server_event_session_targets<br />server_event_sessions<br />server_events<br />server_trigger_events | database_event_session_actions<br />database_event_session_events<br />database_event_session_fields<br />database_event_session_targets<br />database_event_sessions |
| &nbsp; | &nbsp; |

Die beiden Listen in der vorangehenden Tabelle weisen den exakten Stand von Juni 2019 auf. Der Inhalt der Tabelle wird jedoch möglicherweise veraltet sein, da dieser hier nicht aktualisiert wird. Führen Sie die folgende SELECT-Anweisung von T-SQL aus, um genaue Listen zu erhalten. Führen Sie die SELECT-Anweisung zweimal aus – einmal pro Datenbanksystem.

```sql
SELECT name
    FROM sys.all_objects
    WHERE
        (name LIKE 'database\_%' { ESCAPE '\' } OR
         name LIKE 'server\_%' { ESCAPE '\' })
        AND name LIKE '%\_event%' { ESCAPE '\' }
        AND type = 'V'
    ORDER BY name;
```

<!--
The creation of this docs/includes/ file was prompted by Issue 2211 (https://github.com/MicrosoftDocs/sql-docs/issues/2211).
Initial PR was PR 10427 (https://github.com/MicrosoftDocs/sql-docs-pr/pull/10427).
The complaint was that a specific T-SQL code block failed on Azure SQL Database.

GeneMi  ,  2019/05/28
-->
