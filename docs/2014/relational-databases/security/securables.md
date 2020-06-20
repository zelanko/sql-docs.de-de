---
title: Sicherungsfähige Elemente | Microsoft-Dokumentation
ms.custom: ''
ms.date: 10/14/2015
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql12.swb.roleproperties.selectobject.f1
helpviewer_keywords:
- securables [SQL Server]
- schemas [SQL Server], securables
- database securables [SQL Server]
- hierarchies [SQL Server], securables
- server securables [SQL Server]
ms.assetid: bfa748f0-70b0-453c-870a-04b7b205b9ff
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: ff2aaba72e2e5489694d31b35e594622c099acab
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "84997322"
---
# <a name="securables"></a>Sicherungsfähige Elemente
  Als sicherungsfähige Elemente werden Ressourcen bezeichnet, auf die der Zugriff durch das Autorisierungssystem von [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] reguliert wird. Eine Tabelle ist z. B. ein sicherungsfähiges Element. Bestimmte sicherungsfähige Elemente können sich innerhalb anderer Elemente befinden. Dadurch entstehen geschachtelte Hierarchien, so genannte "Bereiche", die selbst sicherungsfähig sind. Sicherungsfähige Bereiche sind **Server**, **Datenbank**und **Schema**.  
  
## <a name="securable-scope-server"></a>Sicherungsfähiger Bereich: Server  
 Der sicherungsfähige Bereich **Server** enthält die folgenden sicherungsfähigen Elemente:  
  
-   Verfügbarkeitsgruppe  
  
-   Endpunkt  
  
-   Anmeldename  
  
-   Serverrolle  
  
-   Datenbank  
  
## <a name="securable-scope-database"></a>Sicherungsfähiger Bereich: Datenbank  
 Der sicherungsfähige Bereich **Datenbank** enthält die folgenden sicherungsfähigen Elemente:  
  
-   Anwendungsrolle  
  
-   Assembly  
  
-   Asymmetrischer Schlüssel  
  
-   Zertifikat  
  
-   Vertrag  
  
-   Volltextkatalog  
  
-   Volltextstoppliste  
  
-   Nachrichtentyp  
  
-   Remotedienstbindung  
  
-   (Datenbank-)Rolle  
  
-   Route  
  
-   Schema  
  
-   Sucheigenschaftenliste  
  
-   Dienst  
  
-   Symmetrischer Schlüssel  
  
-   Benutzer  
  
## <a name="securable-scope-schema"></a>Sicherungsfähiger Bereich: Schema  
 Der sicherungsfähige Bereich **Schema** enthält die folgenden sicherungsfähigen Elemente:  
  
-   type  
  
-   XML-Schemaauflistung  
  
-   Objekt: Die Objektklasse enthält die folgenden Elemente:  
  
    -   Aggregat  
  
    -   Funktion  
  
    -   Verfahren  
  
    -   Warteschlange  
  
    -   Synonym  
  
    -   Tabelle  
  
    -   Sicht  
  
## <a name="controlling-access-to-a-securable"></a>Steuern von Zugriff auf ein sicherungsfähiges Element  
 Die Entität, die die Berechtigung für ein sicherungsfähiges Element empfängt, wird als Prinzipal bezeichnet. Die am häufigsten auftretenden Prinzipale sind Anmeldedaten und Datenbankbenutzer. Der Zugriff auf sicherungsfähige Elemente wird durch das Gewähren oder Verweigern von Berechtigungen gesteuert, oder durch das Hinzufügen von Anmeldedaten und Benutzer zu Rollen, die über Zugriff verfügen. Informationen zum Steuern von Berechtigungen finden Sie unter [GRANT &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql), [REVOKE &#40;Transact-SQL&#41;](/sql/t-sql/statements/revoke-transact-sql), [DENY &#40;Transact-SQL&#41;](/sql/t-sql/statements/deny-transact-sql), [sp_addrolemember &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addrolemember-transact-sql) und [sp_droprolemember &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-droprolemember-transact-sql).  
  
> [!CAUTION]  
>  Die Standardberechtigungen, die Systemobjekten zum Zeitpunkt der Installation erteilt wurden, werden sorgfältig bezüglich möglicher Bedrohungen ausgewertet und müssen nicht im Rahmen der Härtung der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Installation geändert werden. Alle Änderungen an den Berechtigungen für Systemobjekte können die Funktionalität einschränken oder unterbrechen und potenziell dazu führen, dass Ihre [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Installation einen nicht unterstützten Zustand aufweist.  
  
## <a name="related-content"></a>Verwandte Inhalte  
 [Sichern von SQL Server](securing-sql-server.md)  
  
 [sys.database_principals &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-principals-transact-sql)  
  
 [sys.database_role_members &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-role-members-transact-sql)  
  
 [sys.server_principals &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-principals-transact-sql)  
  
 [sys.server_role_members &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-role-members-transact-sql)  
  
 [sys.sql_logins &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-logins-transact-sql)  
  
  
