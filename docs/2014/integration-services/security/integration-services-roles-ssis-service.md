---
title: Integration Services-Rollen (SSIS-Dienst) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- security [Integration Services], roles
- db_ssisoperator role
- db_ssisadmin role
- fixed database roles [Integration Services]
- packages [Integration Services], security
- roles [Integration Services]
- db_ssisltduser role
ms.assetid: 9702e90c-fada-4978-a473-1b1423017d80
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 43c1c932565ae3df666be10a1b89794ecd720135
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62766672"
---
# <a name="integration-services-roles-ssis-service"></a>Integration Services-Rollen (SSIS-Dienst)
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] umfasst die drei Fixed-Rollen `db_ssisadmin`auf Datenbankebene, **db_ssisltduser**und **db_ssisoperator**zum Steuern des Zugriffs auf Pakete. Rollen können nur für Pakete implementiert werden, die in der `msdb` -Datenbank in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]gespeichert werden. Rollen weisen Sie mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]zu. Die Rollenzuweisungen werden in der `msdb` Datenbank gespeichert.  
  
## <a name="read-and-write-actions"></a>Lese- und Schreibaktionen  
 In der folgenden Tabelle werden die Lese- und Schreibaktionen von Windows und der festen Rollen auf Datenbankebene in [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]beschrieben.  
  
|Role|Leseaktion|Schreibaktion|  
|----------|-----------------|------------------|  
|`db_ssisadmin`<br /><br /> oder<br /><br /> `sysadmin`|Eigene Pakete aufzählen.<br /><br /> Alle Pakete aufzählen.<br /><br /> Eigene Pakete anzeigen.<br /><br /> Alle Pakete anzeigen.<br /><br /> Eigene Pakete ausführen.<br /><br /> Alle Pakete ausführen.<br /><br /> Eigene Pakete exportieren.<br /><br /> Alle Pakete exportieren.<br /><br /> Alle Pakete in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent ausführen.|Pakete importieren.<br /><br /> Eigene Pakete löschen.<br /><br /> Alle Pakete löschen.<br /><br /> Eigene Paketrollen ändern.<br /><br /> Alle Paketrollen ändern.<br /><br /> <br /><br /> ** \* Wichtig \* \* ** Mitglieder der db_ssisadmin Rolle und der dc_admin-Rolle können Ihre Berechtigungen möglicherweise auf sysadmin erhöhen. Diese Ausweitung von Berechtigungen ist möglich, da diese Rollen [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Pakete ändern können und [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Pakete von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mithilfe des sysadmin-Sicherheitskontexts des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agents ausgeführt werden können. Konfigurieren Sie als Schutz vor dieser Ausweitung von Berechtigungen beim Ausführen von Wartungsplänen, Datensammlungssätzen und anderen [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Paketen Aufträge des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agents, die Pakete ausführen, für die Verwendung eines Proxykontos mit einschränkten Berechtigungen, oder fügen Sie der db_ssisadmin-Rolle und der dc_admin-Rolle nur sysadmin-Mitglieder hinzu.|  
|**db_ssisltduser**|Eigene Pakete aufzählen.<br /><br /> Alle Pakete aufzählen.<br /><br /> Eigene Pakete anzeigen.<br /><br /> Eigene Pakete ausführen.<br /><br /> Eigene Pakete exportieren.|Pakete importieren.<br /><br /> Eigene Pakete löschen.<br /><br /> Eigene Paketrollen ändern.|  
|**db_ssisoperator**|Alle Pakete aufzählen.<br /><br /> Alle Pakete anzeigen.<br /><br /> Alle Pakete ausführen.<br /><br /> Alle Pakete exportieren.<br /><br /> Alle Pakete in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent ausführen.|Keine|  
|**Windows-Administratoren**|Ausführungsdetails zu allen ausgeführten Paketen anzeigen.|Alle derzeit ausgeführten Pakete anhalten.|  
  
## <a name="sysssispackages-table"></a>Sysssispackages-Tabelle  
 Die **sysssispackages** -Tabelle `msdb` in enthält die Pakete, die in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]gespeichert werden. Weitere Informationen finden Sie unter [sysssispackages &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/sysssispackages-transact-sql).  
  
 Die **sysssispackages** -Tabelle enthält Spalten, die Informationen über die Rollen enthalten, die Paketen zugewiesen sind.  
  
-   In der Spalte **readerrole** wird die Rolle angegeben, die über Lesezugriff auf das Paket verfügt.  
  
-   In der Spalte **writerrole** wird die Rolle angegeben, die über Schreibzugriff auf das Paket verfügt.  
  
-   Die **ownersid** -Spalte enthält den eindeutigen Sicherheitsbezeichner des Benutzers, der das Paket erstellte. In dieser Spalte wird der Besitzer des Pakets definiert.  
  
## <a name="permissions"></a>Berechtigungen  
 Standardmäßig gelten die Berechtigungen von `db_ssisadmin` und **db_ssisoperator** fixierte Rollen auf Datenbankebene und die eindeutige Sicherheits-ID des Benutzers, der das Paket erstellt hat, für die Rolle "Leser" für Pakete, `db_ssisadmin` und die Berechtigungen der Rolle und die eindeutige Sicherheits-ID des Benutzers, der das Paket erstellt hat, gelten für die Schreib Rolle. Ein Benutzer muss Mitglied der Rolle `db_ssisadmin`, **db_ssisltduser**oder **db_ssisoperator** sein, um Lesezugriff auf das Paket zu erhalten. Ein Benutzer muss Mitglied der `db_ssisadmin` Rolle sein, um über Schreibzugriff zu verfügen.  
  
## <a name="access-to-packages"></a>Zugriff auf Pakete  
 Die festen Rollen auf Datenbankebene arbeiten mit benutzerdefinierten Rollen zusammen. Die benutzerdefinierten Rollen sind die Rollen, die Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] erstellen und dann zum Zuweisen von Berechtigungen zu Paketen verwenden. Um auf ein Paket zuzugreifen, muss ein Benutzer Mitglied der benutzerdefinierten Rolle und der entsprechenden festen [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Datenbankrolle sein. Wenn Benutzer z. b. Mitglieder der benutzerdefinierten **Audit** users-Rolle sind, die einem Paket zugewiesen ist, müssen Sie auch Mitglieder von `db_ssisadmin`, **db_ssisltduser**oder **db_ssisoperator** Rolle sein, um Lesezugriff auf das Paket zu erhalten.  
  
 Wenn Sie Paketen keine benutzerdefinierten Rollen zuweisen, wird der Paketzugriff durch die festen Rollen auf Datenbankebene bestimmt.  
  
 Wenn Sie benutzerdefinierte Rollen verwenden möchten, müssen Sie diese der `msdb` -Datenbank hinzufügen, bevor Sie Sie Paketen zuweisen können. Neue Datenbankrollen können Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]erstellen.  
  
 Die [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Rollen auf Datenbankebene gewähren den [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Systemtabellen in der msdb-Datenbank Rechte.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)](der MSSQLServer-Dienst) muss gestartet werden, bevor Sie eine Verbindung mit dem Datenbank-Engine herstellen `msdb` und auf die Datenbank zugreifen können.  
  
 Um Rollen Paketen zuzuweisen, müssen Sie die folgenden Tasks ausführen.  
  
-   **Öffnen Sie Objekt-Explorer, und verbinden Sie sich mit Integration Services**  
  
     Bevor Sie Paketen Rollen mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]zuweisen können, müssen Sie den Objekt-Explorer in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] öffnen und eine Verbindung mit [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]herstellen.  
  
     Der [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Dienst muss gestartet werden, bevor Sie eine Verbindung mit [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]herstellen können.  
  
-   **Zuweisen von Lese-und Schreib Rollen zu Paketen**  
  
     Sie können jedem Paket eine Lese- und eine Schreibrolle zuweisen.  
  
## <a name="related-tasks"></a>Related Tasks  
  
-   [Zuweisen einer Lese- und Schreibrolle zu einem Paket](../assign-a-reader-and-writer-role-to-a-package.md)  
  
-   [Erstellen einer benutzerdefinierten Rolle](../create-a-user-defined-role.md)  
  
-   [Herstellen einer Verbindung mit Integration Services](../connect-to-integration-services.md)  
  
  
