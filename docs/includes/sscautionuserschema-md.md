---
ms.openlocfilehash: 327fd6bac9bc1036a0dd07f7b955ee92cb7e40c8
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68223544"
---
  Ab SQL Server 2005 hat sich das Verhalten der Schemas geändert. Daher gibt Code, der voraussetzt, dass Schemas mit Datenbankbenutzern identisch sind, nunmehr keine richtigen Ergebnisse mehr zurück. Alte Katalogsichten, einschließlich „sysobjects“, sollten nicht in einer Datenbank verwendet werden, in der bereits eine der folgenden DDL-Anweisungen verwendet wurde: CREATE SCHEMA, ALTER SCHEMA, DROP SCHEMA, CREATE USER, ALTER USER, DROP USER, CREATE ROLE, ALTER ROLE, DROP ROLE, CREATE APPROLE, ALTER APPROLE, DROP APPROLE, ALTER AUTHORIZATION. In derlei Datenbanken müssen Sie stattdessen die neuen Katalogansichten verwenden. In den neuen Katalogsichten wird die Trennung zwischen Prinzipalen und Schemas berücksichtigt, die in SQL Server 2005 eingeführt wurde. Weitere Informationen zu Katalogansichten finden Sie unter [Catalog Views &#40;Transact-SQL&#41; (Katalogansichten (Transact-SQL))](../relational-databases/system-catalog-views/catalog-views-transact-sql.md).
   